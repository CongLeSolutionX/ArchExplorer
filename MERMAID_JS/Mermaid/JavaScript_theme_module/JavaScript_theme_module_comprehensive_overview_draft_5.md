---
created: 2025-03-09 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# JavaScript theme module comprehensive overview
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## A Diagrammatic Guide 



Below is a set of Mermaid diagrams that together illustrate the overall structure, dependencies, initialization flow, and internal workings of the theming system for Mermaid. These diagrams capture how the various theme modules (base, dark, default, forest, neutral) rely on shared resources, follow a common class structure with methods like updateColors and calculate, and perform complex color adjustments (using khroma and a helper mkBorder) to compute the final theme variables.

──────────────────────────────
### 1. File Dependency Diagram

This diagram shows the relationships between the core files in the theming subsystem. Notice how each theme module (base, dark, default, forest, neutral) depends on common modules such as the hardcoded values (erDiagram-oldHardcodedValues.ts), theme-helpers.js, and the khroma library used for color manipulation.

```mermaid
---
title: "MERMAID-JS - mermaid - CHANGE_ME_DADDY"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "graph": { "htmlLabels": false, 'curve': 'natural'},
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#BB28',
      'primaryTextColor': '#299',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229'
    }
  }
}%%
graph TD
    A[khroma Library] 
    B[erDiagram-oldHardcodedValues.ts]
    C[theme-helpers.js]
    D[theme-base.js]
    E[theme-dark.js]
    F[theme-default.js]
    G[theme-forest.js]
    H[theme-neutral.js]
    I[index.js]

    A --> D
    A --> E
    A --> F
    A --> G
    A --> H

    B --> D
    B --> F
    B --> G
    B --> H

    C --> D
    C --> E
    C --> H
    C --> F

    D --> I
    E --> I
    F --> I
    G --> I
    H --> I
```

──────────────────────────────

### 2. Common Structure of Theme Classes

Each theme module defines a Theme class that follows a similar pattern. The class contains a constructor initializing base color values (primary, secondary, tertiary, background, etc.), an updateColors() method that performs detailed adjustments (including loops over a set limit for color scales), and a calculate() method that applies user overrides before calling updateColors() again. Finally, each module exports a getThemeVariables function that creates a new Theme instance.

```mermaid
---
title: "MERMAID-JS - mermaid - CHANGE_ME_DADDY"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "classDiagram": { "htmlLabels": false},
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#BB28',
      'primaryTextColor': '#299',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229'
    }
  }
}%%
classDiagram
    class Theme {
      +constructor()
      +updateColors()
      +calculate(overrides)
    }
    class getThemeVariables {
      <<function>>
    }
    Theme <|-- BaseTheme
    Theme <|-- DarkTheme
    Theme <|-- DefaultTheme
    Theme <|-- ForestTheme
    Theme <|-- NeutralTheme
    getThemeVariables ..> Theme : returns instance
```

──────────────────────────────

### 3. Theme Initialization Process Flow

This flowchart shows the process when a user calls getThemeVariables. A new Theme instance is created by one of the theme modules, then its calculate() method is invoked (which in turn calls updateColors after applying any overrides), and finally the computed theme object is returned.

```mermaid
---
title: "MERMAID-JS - mermaid - CHANGE_ME_DADDY"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "flowchart": { "htmlLabels": false},
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#BB28',
      'primaryTextColor': '#299',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229'
    }
  }
}%%
flowchart TD
    A["User calls<br> getThemeVariables(userOverrides)"]
    B["Create new Theme instance"]
    C["Invoke calculate(overrides)"]
    D["Apply base values from constructor"]
    E["Call updateColors()"]
    F["Loop through color scales and set derived variables"]
    G["Reapply user overrides<br>(if any)"]
    H["Final computed theme variables"]
    
    A --> B
    B --> C
    C --> D
    D --> E
    E --> F
    F --> G
    G --> H
```

──────────────────────────────
1. Breakdown of updateColors() Processing

Within updateColors(), the Theme class organizes variables by diagram type and category. The process includes sections for flowchart settings, sequence diagram properties, gantt chart color definitions, adjustments for color scales (using loops over a limit, inversion of colors, and peer adjustments), and finally setting values for specialized diagram types (pie, quadrant-graph, xychart, requirement diagrams, git-related colors, etc.).

```mermaid
---
title: "MERMAID-JS - mermaid - CHANGE_ME_DADDY"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "flowchart": { "htmlLabels": false},
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#BB28',
      'primaryTextColor': '#299',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229'
    }
  }
}%%
flowchart TD
    A["updateColors() invoked"]
    B["Set Flowchart Variables"]
    C["Set Sequence Diagram Variables"]
    D["Set Gantt Chart Variables"]
    E["Set Architecture / Context Diagram Variables"]
    F["Set Color Scale"]
    G["Loop:<br>For each color index<br>(0 to THEME_COLOR_LIMIT)"]
    H["Adjust base color using darken/lighten/invert/adjust"]
    I["Setup inverted and peer colors"]
    J["Set additional specialized variables<br>(pie, quadrant, xychart, git)"]
    
    A --> B
    A --> C
    A --> D
    A --> E
    A --> F
    F --> G
    G --> H
    H --> I
    I --> J
```

──────────────────────────────
These diagrams together reveal the technical complexities of the theme system in Mermaid. They display how multiple theme modules reuse shared helper functions and hardcoded values; how each Theme class organizes a wide range of style variables using iterative adjustments; and how a consistent initialization pipeline (via calculate → updateColors) produces a rich set of theme variables tailored for different diagram types.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---