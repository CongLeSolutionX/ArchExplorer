---
created: 2025-03-09 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---

> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is an ongoing document collecting notes for personal educational purposes and references. 
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExeHJ4YXdtYjJpMDl0MzEwYmU4ZzBobG0waGNiN3MzNzR0d2R2NnMwNSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/26gssNOlBJKjEM3yo/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


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


## 1. Overall Structure: Theme Management

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
    "flowchart": { "htmlLabels": true, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#ffff',
      'primaryTextColor': '#55ff',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph LR
    A["Mermaid Theming System"] --> B{"Theme Registry<br>(index.js)"}
    B --> C[Theme-Base.js]
    B --> D[Theme-Dark.js]
    B --> E[Theme-Default.js]
    B --> F[Theme-Forest.js]
    B --> G["Theme-Neutral.js"]
    C --> H["khroma<br>(Color Library)"]
    
    D --> H
    E --> H
    F --> H
    G --> H

    style B fill:#f9f3,stroke:#333,stroke-width:2px
    style H fill:#afa3,stroke:#333
   
    classDef Style_for_elements fill:#ccf3,stroke:#333
    class C,D,E,F,G Style_for_elements
    
```

**Explanation:**

*   **`A[Mermaid Theming System]`**: Represents the top-level system.
*   **`B{Theme Registry (index.js)}`**:  This acts as the central point, managing and providing access to different themes.
*   **`C[Theme-Base.js]`**, **`D[Theme-Dark.js]`**, etc.: These are individual theme files, each defining a set of color variables and related styles for a specific theme (base, dark, default, forest, neutral).
*   **`H[khroma (Color Library)]`**:  A dependency used for color manipulation (adjusting hue, saturation, lightness, inverting colors, etc.).  All themes utilize `khroma` for color calculations.

## 2. Theme Base Class and Color Calculation (`theme-base.js`)

```mermaid
---
title: "MERMAID-JS - mermaid - CHANGE_ME_DADDY"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "classDiagram": { "htmlLabels": true },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#B528',
      'primaryTextColor': '#2cf',
      'primaryBorderColor': '#7C33',
      'lineColor': '#F8B229'
    }
  }
}%%
classDiagram
    class Theme {
        - background : string
        - primaryColor : string
        - ... // Many more color variables
        + constructor()
        + updateColors()
        + calculate(overrides: object)
    }
    class ThemeHelper {
        + mkBorder(col: string, darkMode: boolean) : string
    }
    Theme "1" -- "1" ThemeHelper : uses
    Theme "1" -- "*" khroma : uses
    Theme : +getThemeVariables(userOverrides_ object)  Theme
    khroma : +adjust(color_ string, options_ object)  string
    khroma : +darken(color_ string, amount_ number)  string
    khroma : +lighten(color_ string, amount_ number)  string
    khroma : +invert(color_ string) string
    ThemeHelper : +mkBorder(col_ string, darkMode_ boolean)  string

    note for Theme "Defines the base structure for a theme and calculates derived color values."
    note for ThemeHelper "Helper functions to generate colors"
    note for khroma "External library for color manipulation"
    
```


**Explanation:**

*   **`Theme` Class:**
    *   Contains numerous color variables (e.g., `background`, `primaryColor`, `textColor`, `nodeBkg`, etc.).
    *   `constructor()`: Initializes default color values.
    *   `updateColors()`:  **Crucial Method:** Calculates derived color values (e.g., `primaryTextColor`, `secondaryColor`, etc.) based on the base colors and the `khroma` library.  It's responsible for setting up the color scheme based on the chosen base colors.
    *   `calculate(overrides: object)`:  Handles theme customization by allowing user-provided overrides for specific colors. It merges the overrides, calls `updateColors()` to recalculate the color scheme, and applies any overrides to derived values.
*   **`ThemeHelper` Class:**
    *   `mkBorder(col: string, darkMode: boolean) : string`: Function to generate border colors based on input color and dark mode flag.
*   **`khroma`:** External library used by `Theme` to perform various color manipulations, including:
    *   `adjust()`: Modifies color properties like hue, saturation, and lightness.
    *   `darken()`: Darkens a color.
    *   `lighten()`: Lightens a color.
    *   `invert()`: Inverts a color.

## 3. Theme Inheritance and Customization:

```mermaid
---
title: "MERMAID-JS - mermaid - CHANGE_ME_DADDY"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "graph": { "htmlLabels": false, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#ffff',
      'primaryTextColor': '#55ff',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph LR
    A["Theme-Base.js<br>(Theme)"] --> B{"Theme-Dark.js"}
    A --> C{"Theme-Default.js"}
    A --> D{"Theme-Forest.js"}
    A --> E{"Theme-Neutral.js"}

    B --> F["Overrides Base Colors and Re-calculates"]

    C --> F
    D --> F
    E --> F

    style A fill:#ccf3,stroke:#333,stroke-width:2px
    style F fill:#afa3,stroke:#333
    
    classDef Style_for_elements fill:#ccf3,stroke:#333
    class B,C,D,E Style_for_elements
    
```

**Explanation:**

*   **`A[Theme-Base.js (Theme)]`**: Defines the base theme class.
*   **`B{Theme-Dark.js}`**, **`C{Theme-Default.js}`**, etc.: Each theme file extends the `Theme` class or creates a new instance. They provide specific color values, often overriding base theme colors.
*   **`F[Overrides Base Colors and Re-calculates]`**: The core logic is that each theme:
    *   Sets its own values for base colors.
    *   Calls `calculate(overrides)` (from the `Theme` class) to ensure derived colors are correctly calculated based on the overridden base colors and any user provided overrides.

## 4. Theme Variable Calculation Flow (Illustrative):

```mermaid
---
title: "MERMAID-JS - mermaid - CHANGE_ME_DADDY"
config:
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "sequenceDiagram": { "htmlLabels": false},
    'fontFamily': 'verdana',
    'themeVariables': {
      'primaryColor': '#B528',
      'primaryTextColor': '#2cf',
      'primaryBorderColor': '#7C33',
      'lineColor': '#F8B229',
      'secondaryColor': '#0610',
      'tertiaryColor': '#fff'
    }
  }
}%%
sequenceDiagram
    autonumber
    participant Theme as Theme
    participant khroma as khroma
    Theme->>Theme: constructor() // Initialize base colors
    Theme->>Theme: calculate(userOverrides)

    rect rgb(20, 15, 255)
        loop For each override
            Theme->>Theme: this[key] = overrides[key] // Apply overrides
        end
    end
    Theme->>Theme: updateColors()
    Theme->>khroma: adjust(primaryColor, {h: -120}) // Example color calculation
    activate khroma
    khroma-->>Theme: Returns secondaryColor
    deactivate khroma
    Theme->>khroma: invert(background) // Example color calculation
    activate khroma
    khroma-->>Theme: Returns lineColor
    deactivate khroma

    rect rgb(20, 150, 25)
        loop For each override<br>(again, in case derived values were overriden)
            Theme->>Theme: this[key] = overrides[key] // Apply overrides
        end
    end
    Theme-->>Theme: return theme
    
```


**Explanation:**

*   This sequence diagram illustrates the process of theme calculation and customization:
    *   The `Theme` class is instantiated.
    *   User-provided overrides (if any) are applied.
    *   `updateColors()` is called to calculate the derived color values using the `khroma` library.  Example calculations are shown (adjusting the `primaryColor`, inverting the `background`).
    *   The function returns the `theme` object.

## 5. `erDiagram-oldHardcodedValues.ts` and Its Role

```mermaid
---
title: "MERMAID-JS - mermaid - CHANGE_ME_DADDY"
config:
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
graph LR
    A[Mermaid Core] --> B{erDiagram-oldHardcodedValues.ts}
    B --> C[Theme System]
    C --> D[Theme-Base.js]
    D --> E[Theme-*.js files]

    style B fill:#f9f2,stroke:#333,stroke-width:2px

    classDef Style_for_elements fill:#ccf2,stroke:#333
    class C,D,E Style_for_elements

```


**Explanation:**

*   **`A[Mermaid Core]`**:  The main Mermaid library code.
*   **`B{erDiagram-oldHardcodedValues.ts}`**: This file contains hardcoded color values for the ER (Entity Relationship) diagram.
*   **`C[Theme System]`**:  The theming system.
*   **`D[Theme-Base.js]`**: This file is the base of the theme system.
*   **`E[Theme-*.js files]`**: The individual theme files, inherit colors from `Theme-Base.js`.

*   **Role:** It holds old, hardcoded values that were previously directly in the ER diagram's styling code (`src/diagrams/er/styles.js`). The file acts as a bridge to maintain visual consistency while the theming system is refactored.  The ER diagram's styling now *references* these values.

## 6.  Key Takeaways and Potential Improvements

*   **Modular Design:** The separation of concerns (theme registry, base theme, individual themes, color manipulation library) promotes maintainability and extensibility.
*   **Color Calculation:**  The use of `khroma` and the `updateColors()` method centralize the color logic, making it easy to change how colors are derived.
*   **Customization:** The `calculate()` method allows users to override theme colors, providing flexibility.
*   **`erDiagram-oldHardcodedValues.ts`**:  A temporary solution.  Ideally, these hardcoded values should be integrated fully into the theme system for better consistency and maintainability.

**Potential Improvements:**

*   **More Fine-Grained Control:** Allow for overriding individual color properties within a diagram type (e.g., control the color of a specific element within a flowchart).
*   **Theme Inheritance:** Explore more sophisticated inheritance models to reduce code duplication.
*   **Dynamic Color Adjustments:** Allow for dynamic color adjustments based on the user's system theme (light/dark mode).
*   **Testing:**  Implement comprehensive unit tests to ensure the theme system's correctness and stability.
*   **Documentation:**  Improve documentation to clearly explain how to create and customize themes.


---

<!-- 
```mermaid
%% Current Mermaid version
info
```  -->


```mermaid
---
title: "CongLeSolutionX"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%{
  init: {
    'flowchart': { 'htmlLabels': false },
    'fontFamily': 'Bradley Hand',
    'themeVariables': {
      'primaryColor': '#fc82',
      'primaryTextColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#81c784',
      'secondaryTextColor': '#6C3483',
      'lineColor': '#F8B229',
      'fontSize': '20px'
    }
  }
}%%
flowchart LR
  My_Meme@{ img: "https://raw.githubusercontent.com/CongLeSolutionX/CongLeSolutionX/refs/heads/main/assets/images/My-meme-light-bulb-question-marks.png", label: "Ăn uống gì chưa ngừi đẹp?", pos: "b", w: 200, h: 150, constraint: "off" }

  Closing_quote@{ shape: braces, label: "...searching insights in the process of formulating better questions..." }

  Closing_quote ~~~ My_Meme
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

  Closing_quote ~~~ My_Meme
  My_Meme animatingEdge@--> Link_to_my_profile
  
  animatingEdge@{ animate: true }

```

---
> **Licenses:**
>
> - **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
> - **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).
> 
---
