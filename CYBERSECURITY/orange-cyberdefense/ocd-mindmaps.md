---
created: 2025-06-25 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/orange-cyberdefense/ocd-mindmaps
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExZjV4d3ZqcGx3OTJ0NTh1bnNmZWV1NjB5bnE2MGgxbHBsd3pxN3N5OSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/3o85xAOn2rfInNueoU/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# ocd-mindmaps repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This project is born from my fascination with blending digital art and artificial intelligence.</br>
> It's where I document my academic explorations,</br>
> share my findings with anyone interested,</br>
> and maintain a personal vault of my creative and technical journey.</br>
> I'm not sure the link for this repo being shared in the back by others,</br>
> since I havent plan for any analytics for this project yet.</br>
> ...and I'm actively looking for a job...</br>

> This document contains my personal notes on the topic,</br>
> compiled from publicly available documentation and various cited sources.
> 
> The materials are intended for educational purposes (<ins>sometimes, entertainment purposes</ins>), personal study, and technical reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>


---

```mermaid
---
title: "ocd-mindmaps repo project"
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
flowchart LR
    subgraph Input_Layer["Input Layer"]
    style Input_Layer fill:#F2F2,stroke:#333,stroke-width:1px, color: #FFFF
    direction TB
        MD["Markdown Sources"]:::io
        XMind["XMind File"]:::io
        JSONSrc["JSON Sources"]:::io
    end

    subgraph Parser_Layer["Parser Layer"]
    style Parser_Layer fill:#F222,stroke:#333,stroke-width:1px, color: #FFFF
    direction TB
        MDParser["parsermd.py"]:::module
        JSONParser["parserjson.py"]:::module
    end

    subgraph Core_Model_Layer["Core Model Layer"]
    style Core_Model_Layer fill:#2BB2,stroke:#333,stroke-width:1px, color: #FFFF
    direction TB
        Models["models Package"]:::module
        ConfigUtils["config.py & utils.py"]:::module
    end

    subgraph Renderer_and_Output_Layer["Renderer & Output Layer"]
    style Renderer_and_Output_Layer fill:#B2B2,stroke:#333,stroke-width:1px, color: #FFFF
    direction TB
        Renderer["Renderer"]:::module
        OutDir["output Directory"]:::io
    end

    subgraph CLI_and_Orchestration["CLI & Orchestration"]
    style CLI_and_Orchestration fill:#22B2,stroke:#333,stroke-width:1px, color: #FFFF
    direction TB
        CLI["main.py"]:::module
        GenAll["gen_all.sh"]:::script
        GenSVG["gen_all_svg.sh"]:::script
    end

    subgraph Configuration["Configuration"]
    style Configuration fill:#2B22,stroke:#333,stroke-width:1px, color: #FFFF
    direction TB
        PackageConf["excalimap/config.py"]:::config
        ADConf["mindmap/ad/conf.yml"]:::config
        ExampleConf["mindmap/example/conf.yml"]:::config
        SiteConf["_config.yml"]:::config
    end

    subgraph Documentation_and_Assets["Documentation & Assets"]
    style Documentation_and_Assets fill:#BF22,stroke:#333,stroke-width:1px, color: #FFFF
    direction TB
        Docs["doc Directory"]:::module
        Icons["icon Directory"]:::module
        RootDocs["README.md & index.md"]:::module
        PackageDocs["excalimap/README.md"]:::module
    end

    %% Connections
    MD -->|reads| MDParser
    JSONSrc -->|reads| JSONParser
    XMind -->|reads| MDParser
    MDParser -->|produces| Models
    JSONParser -->|produces| Models
    Models -->|uses| ConfigUtils
    Models -->|passes data| Renderer
    Renderer -->|writes| OutDir
    CLI -->|orchestrates| MDParser
    CLI -->|orchestrates| JSONParser
    CLI -->|orchestrates| Renderer
    GenAll -->|calls CLI| CLI
    GenSVG -->|calls CLI| CLI
    PackageConf -->|configures| MDParser
    PackageConf -->|configures| JSONParser
    ADConf -->|drives| MDParser
    ExampleConf -->|drives| MDParser
    SiteConf -->|site config| RootDocs
    Docs -->|reference| CLI
    Icons -->|assets for| Renderer
    RootDocs -->|intro| CLI
    PackageDocs -->|details| Models

    %% Click Events
    click MD "https://github.com/orange-cyberdefense/ocd-mindmaps/tree/main/excalimap/mindmap/"
    click XMind "https://github.com/orange-cyberdefense/ocd-mindmaps/blob/main/src/Pentesting_Active_directory_dark.xmind"
    click MDParser "https://github.com/orange-cyberdefense/ocd-mindmaps/blob/main/excalimap/parsermd.py"
    click JSONParser "https://github.com/orange-cyberdefense/ocd-mindmaps/blob/main/excalimap/parserjson.py"
    click Models "https://github.com/orange-cyberdefense/ocd-mindmaps/tree/main/excalimap/models/"
    click ConfigUtils "https://github.com/orange-cyberdefense/ocd-mindmaps/blob/main/excalimap/config.py"
    click OutDir "https://github.com/orange-cyberdefense/ocd-mindmaps/tree/main/excalimap/output/"
    click CLI "https://github.com/orange-cyberdefense/ocd-mindmaps/blob/main/excalimap/main.py"
    click GenAll "https://github.com/orange-cyberdefense/ocd-mindmaps/blob/main/excalimap/gen_all.sh"
    click GenSVG "https://github.com/orange-cyberdefense/ocd-mindmaps/blob/main/excalimap/gen_all_svg.sh"
    click PackageConf "https://github.com/orange-cyberdefense/ocd-mindmaps/blob/main/excalimap/config.py"
    click ADConf "https://github.com/orange-cyberdefense/ocd-mindmaps/blob/main/excalimap/mindmap/ad/conf.yml"
    click ExampleConf "https://github.com/orange-cyberdefense/ocd-mindmaps/blob/main/excalimap/mindmap/example/conf.yml"
    click SiteConf "https://github.com/orange-cyberdefense/ocd-mindmaps/blob/main/_config.yml"
    click Docs "https://github.com/orange-cyberdefense/ocd-mindmaps/tree/main/excalimap/doc/"
    click Icons "https://github.com/orange-cyberdefense/ocd-mindmaps/tree/main/excalimap/icon/"
    click RootDocs "https://github.com/orange-cyberdefense/ocd-mindmaps/blob/main/README.md"
    click PackageDocs "https://github.com/orange-cyberdefense/ocd-mindmaps/blob/main/excalimap/README.md"

    %% Styles
    classDef io fill:#cfc2,stroke:#006600,stroke-width:1px
    classDef module fill:#c5f2,stroke:#003399,stroke-width:1px
    %% classDef script fill:#ccf2,stroke:#333,fill:#fff
    classDef config fill:#fcb2,stroke:#cc6600,stroke-width:1px

```

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
