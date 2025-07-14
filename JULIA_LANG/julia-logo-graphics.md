---
created: 2025-07-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/JuliaLang/julia-logo-graphics
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExMXVjejV3dnVjc2o5MXd3eXBvcDR1cHlzbHQ1Z2R6YjY0ZHpmdjJ6OCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/hL9q5k9dk9l0wGd4e0/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# julia-logo-graphics repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes (<ins>sometimes, entertainment purposes</ins>), personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>



----

```mermaid
---
title: "julia-logo-graphics repo project"
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
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': { 'htmlLabels': false, 'curve': 'linear' },
    'fontFamily': 'Monaco',
    'themeVariables': {
      'primaryColor': '#F5E3',
      'primaryTextColor': '#F8B229',
      'lineColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#EEF5',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD'
    }
  }
}%%
flowchart LR
    %% User
    UserCLI["User CLI"]:::external

    %% External Libraries
    subgraph "External Libraries"
        Luxor["Luxor.jl"]:::lib
        Colors["Colors.jl"]:::lib
    end

    %% System Utilities
    subgraph "System Utilities"
        SIPS["sips"]:::os
        Iconutil["iconutil"]:::os
    end

    %% Asset Stores
    subgraph "Asset Stores"
        FontStore["font/"]:::fs
        ImageStore["images/"]:::fs
    end

    %% Julia Generator Scripts
    subgraph "Julia Generator Scripts" 
        direction TB
        CoreModules["src/"]:::julia
        ColorMap["compare_color_to_named_colors.jl"]:::julia
        FontDemo["fontexample.jl"]:::julia
        DotsOnly["julia-dots.jl"]:::julia
        FullColor["julia-logo-color.jl"]:::julia
        DarkMode["julia-logo-dark.jl"]:::julia
        MonoDark["julia-logo-dark-mono.jl"]:::julia
        ColorPNG["julia-logo-color-png-320-230.jl"]:::julia
    end

    %% Outputs
    subgraph "Generated Outputs"
        PDFColor["images/julia-logo-color.pdf"]:::fs
        PDFx3["images/julia-logo-color-pdfx3.pdf"]:::fs
        ICNS["images/juliadots.icns"]:::fs
    end

    %% Flows
    UserCLI -->|"invoke"| CoreModules
    CoreModules --> ColorMap
    CoreModules --> FontDemo
    CoreModules --> DotsOnly
    CoreModules --> FullColor
    CoreModules --> DarkMode
    CoreModules --> MonoDark
    CoreModules --> ColorPNG

    ColorMap -->|"uses"| Colors
    FontDemo -->|"uses"| Luxor
    DotsOnly -->|"uses"| Luxor
    FullColor -->|"uses"| Luxor
    DarkMode -->|"uses"| Luxor
    MonoDark -->|"uses"| Luxor
    ColorPNG -->|"uses"| Luxor

    %% Asset read
    DotsOnly -->|"reads fonts/images"| FontStore
    FullColor --> FontStore
    FullColor --> ImageStore
    DarkMode --> ImageStore
    MonoDark --> ImageStore
    ColorPNG --> ImageStore
    ColorMap --> ImageStore

    %% Outputs
    DotsOnly -->|"writes SVG/PNG"| ImageStore
    FullColor -->|"writes SVG/PNG"| ImageStore
    DarkMode -->|"writes SVG/PNG"| ImageStore
    MonoDark -->|"writes SVG/PNG"| ImageStore
    ColorPNG -->|"writes PNG (320x230)"| ImageStore
    FullColor -->|"writes PDF"| PDFColor
    FullColor -->|"writes PDF x3"| PDFx3

    %% macOS Iconset flow
    CoreModules -->|"generate-mac-iconset.jl"| SIPS
    SIPS --> Iconutil
    Iconutil --> ICNS

    %% Click Events
    click CoreModules "https://github.com/julialang/julia-logo-graphics/tree/master/src/"
    click ColorMap "https://github.com/julialang/julia-logo-graphics/blob/master/src/compare_color_to_named_colors.jl"
    click FontDemo "https://github.com/julialang/julia-logo-graphics/blob/master/src/fontexample.jl"
    click DotsOnly "https://github.com/julialang/julia-logo-graphics/blob/master/src/julia-dots.jl"
    click FullColor "https://github.com/julialang/julia-logo-graphics/blob/master/src/julia-logo-color.jl"
    click DarkMode "https://github.com/julialang/julia-logo-graphics/blob/master/src/julia-logo-dark.jl"
    click MonoDark "https://github.com/julialang/julia-logo-graphics/blob/master/src/julia-logo-dark-mono.jl"
    click ColorPNG "https://github.com/julialang/julia-logo-graphics/blob/master/src/julia-logo-color-png-320-230.jl"
    click FontStore "https://github.com/julialang/julia-logo-graphics/tree/master/font/"
    click ImageStore "https://github.com/julialang/julia-logo-graphics/tree/master/images/"
    click PDFColor "https://github.com/julialang/julia-logo-graphics/blob/master/images/julia-logo-color.pdf"
    click PDFx3 "https://github.com/julialang/julia-logo-graphics/blob/master/images/julia-logo-color-pdfx3.pdf"
    click ICNS "https://github.com/julialang/julia-logo-graphics/blob/master/images/juliadots.icns"

    %% Styles
    classDef julia fill:#c3dafe,stroke:#1e40af,stroke-width:2px
    classDef lib fill:#d1fae5,stroke:#047857,stroke-width:2px
    classDef os fill:#fee2e2,stroke:#b91c1c,stroke-width:2px
    classDef fs fill:#e5e7eb,stroke:#374151,stroke-width:2px
    classDef external fill:#f0f9ff,stroke:#3b82f6,stroke-width:2px
```

----


<!-- 
```mermaid
%% Current Mermaid version
info
```  -->


```mermaid
---
title: "C<char>o&#770;</char>ngL<char>e&#770;</char>SolutionX"
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
    
  My_Meme ~~~ Closing_quote
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX/CongLeSolutionX' target='_blank'>Click here if you care about the profile of a tech guy seeking for job 🙏🏼</a>"}}

  Closing_quote ~~~ My_Meme
  My_Meme animatingEdge@--> Link_to_my_profile
  
  animatingEdge@{ animate: true }



```

---
>**Licenses:**
>
>- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
>- **Creative Commons Attribution-ShareAlike 4.0 International**: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) [![CC BY-SA 4.0](https://licensebuttons.net/l/by-sa/4.0/88x31.png)](https://creativecommons.org/licenses/by-sa/4.0/) - Legal details in [LICENSE-CC-BY-SA-4.0](THE_PAST/LICENSE-CC-BY-SA-4.0) and at [Creative Commons official site](https://creativecommons.org/licenses/by-sa/4.0/).
>
---