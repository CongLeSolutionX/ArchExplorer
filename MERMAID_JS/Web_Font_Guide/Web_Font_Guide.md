---
created: 2025-03-29 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# Comprehensive Web Font Guide for Mermaid Diagrams
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


This guide details various web fonts potentially usable in Mermaid diagrams, combining classic "web-safe" fonts with modern OS defaults and popular web fonts. It highlights technical aspects and potential issues to consider for reliable rendering.

### 1. Font Categorization and Origin

This mind map categorizes the fonts and provides a quick reference for their type and typical availability:

*   **[WS]**: Classic Web-Safe (Highest compatibility, expect broad availability)
*   **[MOD]**: Modern OS Default (High availability on specific OS - Win/Mac/iOS/Android)
*   **[PWF]**: Popular Web Font / Open Source (Often installed/cached, may require embedding)
*   **[O]**: Other (Less common, decorative, use with caution)

```mermaid
---
title: "Font Categorization and Origin"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%{
  init: {
    'fontFamily': 'Andale Mono, monospace',
    'mindmap': {
	    'nodeAlign': 'center',
	    'padding': 15
    },
    'themeVariables': {
      'primaryColor': '#FC82',
      'primaryTextColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#EBF3',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD',
      'fontSize': '20px'
    }
  }
}%%
mindmap
  root)"Web Fonts for Mermaid"(
    Sans_Serif))"Sans-Serif"((
      Helvetica("Helvetica<br>[WS]")
      Arial("Arial<br>[WS]")
      Arial_Black("Arial Black<br>[WS]")
      Verdana("Verdana<br>[WS]")
      Tahoma("Tahoma<br>[WS]")
      Trebuchet_MS("Trebuchet MS<br>[WS]")
      Impact("Impact<br>[WS]")
      Gill_Sans("Gill Sans<br>[WS]")
      Segoe_UI("Segoe UI<br>[MOD - Win]")
      apple_system("-apple-system / BlinkMacSystemFont<br>[MOD - Apple]")
      Calibri("Calibri<br>[MOD - Win/Office]")
      Roboto("Roboto<br>[PWF - Android/Google]")
      Source_Sans_Pro("Source Sans Pro<br>[PWF - Adobe]")
      Lato("Lato<br>[PWF - Google]")
    Serif))"Serif"((
      Times_New_Roman("Times New Roman<br>[WS]")
      Georgia("Georgia<br>[WS]")
      Palatino("Palatino<br>[WS]")
      Baskerville("Baskerville<br>[WS]")
      Cambria("Cambria<br>[MOD - Win/Office]")
      Source_Serif_Pro("Source Serif Pro<br>[PWF - Adobe]")
    Monospace))"Monospace"((
      Andale_Mono("Andalé Mono<br>[WS]")
      Courier("Courier<br>[WS]")
      Courier_New("Courier New<br>[WS]")
      Lucida("Lucida<br>(Console/Sans Typewriter)<br>[WS]")
      Monaco("Monaco<br>[MOD - Mac Classic]")
      Consolas("Consolas<br>[MOD - Win/Office]")
      Menlo("Menlo<br>[MOD - Mac]")
      Source_Code_Pro("Source Code Pro<br>[PWF - Adobe]")
      Fira_Mono_Fira_Code("Fira Mono / Fira Code<br>[PWF - Mozilla]")
    Cursive))"Cursive"((
      Comic_Sans_MS("Comic Sans MS [WS]<br>(Often debated category, technically cursive)")
      Bradley_Hand("Bradley Hand<br>[O]")
      Brush_Script_MT("Brush Script MT<br>[O]")
    Fantasy))"Fantasy"((
      Luminari("Luminari<br>[O]")
      
```


**Technical Notes on Mind Map:**

*   **Availability is Key:** The bracketed codes ([WS], [MOD], [PWF]) are crucial. Mermaid rendering relies on the font being available in the environment (browser, OS, rendering tool).
*   **System Fonts (`-apple-system`, etc.):** These aren't single fonts but CSS mechanisms to use the OS's preferred UI font. Support depends on the Mermaid rendering engine understanding these CSS values.
*   **Popular Web Fonts (`Roboto`, `Source Sans Pro`, etc.):** While common, they aren't guaranteed unless the specific Mermaid tool explicitly loads them (e.g., via `@font-face` in a web context) or the user has them installed.

---

### 2. Font Choice Decision Process

This flowchart outlines the thought process when selecting a font for your Mermaid diagram:

```mermaid
---
title: "Font Choice Decision Process"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  theme: base
  look: handDrawn
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': { 'htmlLabels': true, 'curve': 'basis' },
    'fontFamily': 'American Typewriter, monospace',
    'logLevel': 'fatal',
    'themeVariables': {
      'primaryColor': '#22BB',
      'primaryTextColor': '#F8B229',
      'lineColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#E2F1',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD',
      'fontSize': '20px'
    }
  }
}%%
flowchart TD
    A["Start:<br>Need Font for Mermaid"] --> B{"What's the Priority?"}
    B -- Compatibility Across Devices --> C["Choose Web-Safe Fonts"]
    B -- Modern Look & Readability --> D{"Target Environment?"}
    B -- "Specific Style<br>(Code/Decorative)" --> E{"Select Font Type"}

    C --> C1["Examples:<br>Arial, Verdana, Georgia, Courier New"]
    C1 --> F["Result:<br>High Reliability, Predictable Look"]

    D -- "Controlled Web Env<br>(Can load fonts)" --> G["Consider Popular Web Fonts / OS Defaults"]
    D -- "Diverse/Unknown Env<br>(Markdown Previewer, etc.)" --> C
    D -- Specific OS Target --> H["Use Respective OS Defaults"]

    G --> G1["Examples:<br>Roboto, Source Sans Pro, Segoe UI, Consolas"]
    G1 -- "Web Font Loading Supported?" --> G2["Result:<br>Modern Look, Good Readability<br>(If Loaded)"]
    G1 -- "Web Font Loading NOT Supported?" --> G3["Result:<br>Font May Fallback - Unpredictable!"] ==> C

    H --> H1["Examples:<br>Segoe UI (Win),<br> -apple-system (Mac),<br> Consolas (Win Code)"]
    H1 --> H2["Result:<br>Native Look on Target OS, Falls back elsewhere"]

    E -- Code / Monospaced Text --> I["Choose Monospace Fonts"]
    E -- Decorative / Stylistic --> J["Choose Cursive/Fantasy Fonts"]

    I --> I1["Web-Safe: Courier New"]
    I --> I2["Modern/Readable: Consolas, Menlo, Source Code Pro"]
    I1 --> F
    I2 --> K["Consider Availability<br>(like G1/H1)"]

    J --> J1["Examples:<br>Comic Sans, Brush Script MT"]
    J1 --> L["Result:<br>Stylized Look, Lower Readability, Use Sparingly!"]
    L --> K

    F --> Z["End:<br>Font Chosen"]
    G2 --> Z
    H2 --> Z
    K --> Z
    
```


**Technical Notes on Flowchart:**

*   **Trade-offs:** The core decision is often compatibility vs. aesthetics/modernity.
*   **Environment Matters:** Where the Mermaid diagram will be viewed heavily dictates font choice. Simple Markdown viewers rarely load external fonts. Web applications have more flexibility.
*   **Fallbacks:** If a chosen font (especially [PWF] or [MOD]) isn't available *and* web fonts aren't loaded, the browser/viewer *will* substitute a default font (like Arial, Times New Roman, Courier). This can significantly alter the diagram's intended appearance and spacing.
*   **Readability:** For diagrams, readability is paramount. Highly decorative fonts ([O]) are generally discouraged for primary text.

---

### 3. Font Availability Tiers & Issues

This graph visualizes the different levels of font availability and the associated risks/considerations:

```mermaid
---
title: "Font Availability Tiers & Issues"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': {'htmlLabels': true, 'curve': 'basis' },
    'fontFamily': 'monospace',
    'themeVariables': {
      'primaryColor': '#FC82',
      'primaryTextColor': '#F8B229',
      'lineColor': '#F8B229',
      'fontSize': '20px'
    }
  }
}%%
graph TD
    subgraph Tier1["Tier 1:<br>Highest Compatibility"]
        style Tier1 fill:#dff2,stroke:#333,stroke-width:1px
        T1_Node("Classic Web-Safe Fonts<br>(Arial, Times New Roman, Courier New, etc.)")
        T1_Desc("Issues: <br/>- Limited aesthetic choice<br/>- Considered 'dated' by some<br/><b>+ Universally available</b><br/><b>+ Predictable rendering</b>")
        T1_Node --> T1_Desc
    end

    subgraph Tier2["Tier 2:<br>High Compatibility<br>(OS Dependent)"]
        style Tier2 fill:#eff2,stroke:#333,stroke-width:0.1px
        T2_Node("Modern OS Default Fonts<br>(Segoe UI, -apple-system, Consolas, Cambria, etc.)")
        T2_Desc("Issues: <br/>- Inconsistent look across OS<br/>- Falls back on other OS<br/><b>+ Excellent readability on target OS</b><br/><b>+ Native look & feel</b>")
        T2_Node --> T2_Desc
    end

    subgraph Tier3["Tier 3:<br>Medium Compatibility<br>(Context Dependent)"]
        style Tier3 fill:#f3e2,stroke:#333,stroke-width:0.1px
       T3_Node("Popular Web/Open Source Fonts<br>(Roboto, Source Sans Pro, Fira Mono, etc.)")
       T3_Desc("Issues:<br/><b>- Requires installation OR web font loading (@font-face)</b><br/>- Potential licensing checks for embedding<br/>- Falls back if not loaded/installed<br/>+ Modern look & often high quality")
       T3_Node --> T3_Desc
    end

     subgraph Tier4["Tier 4:<br>Lower Compatibility/Use with Caution"]
        style Tier4 fill:#fdd2,stroke:#333,stroke-width:0.1px
        T4_Node("Decorative / Less Common Fonts<br>(Brush Script, Luminari, Bradley Hand)")
        T4_Desc("Issues:<br/><b>- Very unlikely to be installed</b><br/>- Often poor readability for diagrams<br/>- Requires reliable web font loading<br/>- Falls back significantly if unavailable")
        T4_Node --> T4_Desc
    end

    T1_Node -- Safest Choice --> Recommendation("Recommendation")
    T2_Node -- Good for Target OS --> Recommendation
    T3_Node -- Good for Controlled Web Env --> Recommendation
    T4_Node -- Use Sparingly/Stylistic Only --> Recommendation

```

**Technical Notes on Availability Tiers:**

*   **Tier 1 (Web-Safe):** The most robust option for ensuring your diagrams render similarly for almost everyone, regardless of their OS or setup. The primary drawback is the limited selection and potentially dated look.
*   **Tier 2 (OS Default):** Excellent choice if you know your primary audience uses a specific OS (e.g., internal Windows tools using Segoe UI). Be prepared for fallbacks on other systems.
*   **Tier 3 (Popular Web/Open Source):** Offers the best balance of modern aesthetics and high-quality typography *if* the rendering environment supports web font loading (`@font-face`) or if you can reasonably expect users to have them installed (less reliable). This is common in web applications but rare in basic Markdown previews.
*   **Tier 4 (Decorative):** Generally unsuitable for primary diagram text due to readability and availability issues. Use only for specific, non-critical stylistic elements and ensure they can be loaded reliably.

---

### Summary and Potential Issues

*   **Core Issue - Availability:** The biggest challenge is ensuring the chosen font is available where the Mermaid diagram is rendered. Lack of availability leads to font substitution (fallback).
*   **Fallback Impact:** Font substitution can break the layout, spacing, and overall look of a diagram, as different fonts have different character widths and heights.
*   **Rendering Context:** A Mermaid diagram in a web app (using Mermaid.js) might support `@font-face` loading, making Tier 3 fonts viable. A static site generator or Markdown previewer might only have access to Tier 1 and Tier 2 fonts.
*   **SVG Output:** Mermaid typically renders to SVG. The SVG viewer must have access to the font. Embedding fonts directly into SVG increases file size significantly and is often not done by default.
*   **Licensing:** If using Tier 3 or Tier 4 fonts via `@font-face`, ensure the font license permits web embedding. Most popular Google Fonts and Open Source fonts (like Adobe's or Fira) allow this.
*   **Testing:** **Always test** your diagrams with your chosen font in the target viewing environment(s) to confirm rendering accuracy and handle potential fallbacks gracefully.

----

By understanding these categories, decision factors, and potential issues, you can make informed choices about which fonts to use in your Mermaid diagrams to balance visual appeal with reliable rendering. For maximum safety, stick to Tier 1; for modern looks in controlled environments, explore Tier 2 and Tier 3 carefully.


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
