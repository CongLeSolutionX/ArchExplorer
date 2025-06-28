---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/VSCodium/icons
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExMmd6MzM5eXFzcG1zY251NGRtbWcyOGh6NHZlbWNwdjMwNGt2c3JuZyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/4OAxDXv4RdUeg38JYi/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# icons repo project
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


---

```mermaid
---
title: "CHANGE_ME_DADDY"
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
flowchart TB
  subgraph Generation_Pipeline["Generation Pipeline"]
  style Generation_Pipeline fill:#F2F2,stroke:#333,stroke-width:1px, color: #FFFF
  direction TB
    TS["Templates (Shapes)"]:::storage
    TBk["Templates (Backgrounds)"]:::storage
    TC["Templates (Colors)"]:::storage
    BS["build.sh"]:::scripts
    US["utils.sh"]:::scripts
    PS["preview.sh"]:::scripts
    IP["Image-Processing Engine"]:::scripts
    OS["Output Store (icons/)"]:::storage
  end

  subgraph Previewer_Application["Previewer Application"]
  style Previewer_Application fill:#22F2,stroke:#333,stroke-width:1px, color: #FFFF
  direction TB
    SS["Next.js Server"]:::web
    SC["previewer/config/*.json"]:::web
    UI["UI Components"]:::web
    LC["Layout & Icons Components"]:::web
    UT["Previewer Utility Functions"]:::web
    HK["Previewer Hooks"]:::web
    ST["Styles & Toolchain Config"]:::web
    SA["Static Assets (public/icons/)"]:::storage
    BR["Browser Client"]:::external
  end

  subgraph External_Hosting_Services["External/Hosting Services"]
  style External_Hosting_Services fill:#22BF,stroke:#333,stroke-width:1px, color: #FFFF
  direction TB
    GH["GitHub (CI/CD)"]:::external
    NT["Netlify (Hosting)"]:::external
  end

  %% Connections
  TS --> BS
  TBk --> BS
  TC --> BS
  BS --> US
  BS --> IP
  US --> IP
  IP --> OS

  OS --> SA
  SA --> SS
  SC --> SS
  SS --> UI
  UI --> LC
  LC --> BR
  SS --> BR

  GH --> BS
  GH --> SS
  SS --> NT

  %% Click Events
  click TS "https://github.com/vscodium/icons/tree/main/templates/shapes/"
  click TBk "https://github.com/vscodium/icons/tree/main/templates/backgrounds/"
  click TC "https://github.com/vscodium/icons/tree/main/templates/colors/"
  click BS "https://github.com/vscodium/icons/blob/main/build.sh"
  click US "https://github.com/vscodium/icons/blob/main/utils.sh"
  click PS "https://github.com/vscodium/icons/blob/main/preview.sh"
  click OS "https://github.com/vscodium/icons/tree/main/icons/"
  click SS "https://github.com/vscodium/icons/blob/main/previewer/pages/_app.tsx"
  click SS "https://github.com/vscodium/icons/blob/main/previewer/pages/index.tsx"
  click SC "https://github.com/vscodium/icons/blob/main/previewer/config/backgrounds.json"
  click SC "https://github.com/vscodium/icons/blob/main/previewer/config/colors.json"
  click SC "https://github.com/vscodium/icons/blob/main/previewer/config/shapes.json"
  click SC "https://github.com/vscodium/icons/blob/main/previewer/config/platforms.json"
  click UI "https://github.com/vscodium/icons/tree/main/previewer/components/ui/"
  click LC "https://github.com/vscodium/icons/blob/main/previewer/components/layout.tsx"
  click LC "https://github.com/vscodium/icons/blob/main/previewer/components/icons.tsx"
  click SA "https://github.com/vscodium/icons/tree/main/previewer/public/icons/"
  click UT "https://github.com/vscodium/icons/blob/main/previewer/lib/utils.ts"
  click HK "https://github.com/vscodium/icons/blob/main/previewer/hooks/use-toast.ts"
  click ST "https://github.com/vscodium/icons/blob/main/previewer/styles/globals.css"
  click ST "https://github.com/vscodium/icons/blob/main/previewer/tailwind.config.js"
  click ST "https://github.com/vscodium/icons/blob/main/previewer/postcss.config.js"
  click ST "https://github.com/vscodium/icons/blob/main/previewer/.eslintrc.json"
  click ST "https://github.com/vscodium/icons/blob/main/previewer/prettier.config.js"

  %% Styles
  classDef scripts fill:#ade6,stroke:#000;
  classDef storage fill:#9e92,stroke:#000;
  classDef web fill:#d0dd,stroke:#000;
  classDef external fill:#fed2,stroke:#000;
```

----


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
    
  My_Meme ~~~ Closing_quote
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

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
