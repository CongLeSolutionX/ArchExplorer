---
created: 2025-06-21 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/usgpo/uslm
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExeG9wYW50NW10MG9pY3JnN3gwcnU4Mm1tb2txZnpyMnlmNzVvZHNzOSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/1ldBRbKQpYXg4/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# uslm repo project
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
title: "uslm repo project"
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
    %% GitHub Repository and Branches
    subgraph "GitHub Repository" 
        direction LR
        Proposed["Proposed Branch"]:::blue
        Main["Main Branch"]:::blue
        subgraph "Governance Files"
            direction TB
            CODEOWNERS["CODEOWNERS"]:::blue
            CONTRIBUTING["CONTRIBUTING.md"]:::blue
            CHANGELOG["CHANGELOG.md"]:::blue
            README["README.md"]:::blue
            LICENSE["LICENSE.md"]:::blue
            GITIGNORE[".gitignore"]:::blue
            GITATTR[".gitattributes"]:::blue
        end
    end

    %% Branch Workflow
    Proposed -->|"Pull Request & Review"| Main

    %% Artifacts under Main Branch
    subgraph "Artifacts (Main)" 
        direction LR
        subgraph "Schema Modules"
            direction TB
            USLMCore["uslm-2.1.0.xsd"]:::green
            USLMComp["uslm-components-2.1.0.xsd"]:::green
            USLMTable["uslm-table-module-2.1.0.xsd"]:::green
            USLMMeta["uslm-meta-senate.xsd"]:::green
            USLMHistory["uslm-2.0.0.xsd … uslm-2.0.17.xsd"]:::green
            TableGeneric["uslm-table-module.xsd"]:::green
            subgraph "MathML Schemas"
                direction TB
                MCommon["mathml3-common.xsd"]:::green
                MContent["mathml3-content.xsd"]:::green
                MPres["mathml3-presentation.xsd"]:::green
                MStrict["mathml3-strict-content.xsd"]:::green
                MAgg["mathml3.xsd"]:::green
            end
            subgraph "XHTML Schemas"
                direction TB
                XHTMLBase["xhtml-1.0.xsd"]:::green
                XHTMLData["xhtml-datatypes-1.xsd"]:::green
            end
            subgraph "Dublin Core Schemas"
                direction TB
                DCTerms["dcterms.xsd"]:::green
                DCType["dcmitype.xsd"]:::green
                DCCore["dc.xsd"]:::green
            end
            XMLSchema["xml.xsd"]:::green
        end
        subgraph "Stylesheets"
            direction TB
            CSSProd["uslm.css"]:::green
            CSSDebug["uslm-debug.css"]:::green
        end
        subgraph "Documentation"
            direction LR
            UGMD["USLM-User-Guide.md"]:::green
            UGPDF["USLM-User-Guide.pdf"]:::green
            Rev20_17["USLM-2_0-Review-Guide-2_0_17.md/pdf"]:::green
            Rev20_12["USLM-2_0-Review-Guide-v2_0_12.md/pdf"]:::green
            Rev21["USLM-2_1-ReviewGuide.md/pdf"]:::green
        end
        subgraph "Samples"
            direction LR
            CurrentSamples["bill-version-samples-september-2024/"]:::green
            Archive["previous/"]:::green
        end
    end

    %% Publishing Pipeline
    Main -->|"On Merge"| Pipeline["Publishing Pipeline"]:::blue
    Pipeline -->|"Publishes to"| GovInfo["GovInfo Publication"]:::orange

    %% Consumers
    subgraph "Consumers & External" 
        direction LR
        GPO["GPO"]:::orange
        XMLWG["XML Working Group"]:::orange
        Devs["Developers/Publishers"]:::orange
    end

    %% Relationships from Artifacts to Consumers
    Artifacts -->|Validates & Styles| Devs
    Artifacts -->|Reviews Drafts| XMLWG
    GovInfo -->|Provides Final Artifacts| GPO

    %% Click Events for Governance
    click CODEOWNERS "https://github.com/usgpo/uslm/tree/main/CODEOWNERS"
    click CONTRIBUTING "https://github.com/usgpo/uslm/blob/main/CONTRIBUTING.md"
    click CHANGELOG "https://github.com/usgpo/uslm/blob/main/CHANGELOG.md"
    click README "https://github.com/usgpo/uslm/blob/main/README.md"
    click LICENSE "https://github.com/usgpo/uslm/blob/main/LICENSE.md"
    click GITIGNORE "https://github.com/usgpo/uslm/blob/main/.gitignore"
    click GITATTR "https://github.com/usgpo/uslm/blob/main/.gitattributes"

    %% Click Events for Core Schema Modules
    click USLMCore "https://github.com/usgpo/uslm/blob/main/uslm-2.1.0.xsd"
    click USLMComp "https://github.com/usgpo/uslm/blob/main/uslm-components-2.1.0.xsd"
    click USLMTable "https://github.com/usgpo/uslm/blob/main/uslm-table-module-2.1.0.xsd"
    click USLMMeta "https://github.com/usgpo/uslm/blob/main/uslm-meta-senate.xsd"
    click USLMHistory "https://github.com/usgpo/uslm/blob/main/uslm-2.0.0.xsd"
    click TableGeneric "https://github.com/usgpo/uslm/blob/main/uslm-table-module.xsd"
    click MCommon "https://github.com/usgpo/uslm/blob/main/mathml3-common.xsd"
    click MContent "https://github.com/usgpo/uslm/blob/main/mathml3-content.xsd"
    click MPres "https://github.com/usgpo/uslm/blob/main/mathml3-presentation.xsd"
    click MStrict "https://github.com/usgpo/uslm/blob/main/mathml3-strict-content.xsd"
    click MAgg "https://github.com/usgpo/uslm/blob/main/mathml3.xsd"
    click XHTMLBase "https://github.com/usgpo/uslm/blob/main/xhtml-1.0.xsd"
    click XHTMLData "https://github.com/usgpo/uslm/blob/main/xhtml-datatypes-1.xsd"
    click DCTerms "https://github.com/usgpo/uslm/blob/main/dcterms.xsd"
    click DCType "https://github.com/usgpo/uslm/blob/main/dcmitype.xsd"
    click DCCore "https://github.com/usgpo/uslm/blob/main/dc.xsd"
    click XMLSchema "https://github.com/usgpo/uslm/blob/main/xml.xsd"

    %% Click Events for Stylesheets
    click CSSProd "https://github.com/usgpo/uslm/blob/main/uslm.css"
    click CSSDebug "https://github.com/usgpo/uslm/blob/main/uslm-debug.css"

    %% Click Events for Documentation
    click UGMD "https://github.com/usgpo/uslm/blob/main/USLM-User-Guide.md"
    click UGPDF "https://github.com/usgpo/uslm/blob/main/USLM-User-Guide.pdf"
    click Rev20_17 "https://github.com/usgpo/uslm/blob/main/USLM-2_0-Review-Guide-2_0_17.md"
    click Rev20_12 "https://github.com/usgpo/uslm/blob/main/USLM-2_0-Review-Guide-v2_0_12.md"
    click Rev21 "https://github.com/usgpo/uslm/blob/main/USLM-2_1-ReviewGuide.md"

    %% Click Events for Samples
    click CurrentSamples "https://github.com/usgpo/uslm/tree/main/bill-version-samples-september-2024/"
    click Archive "https://github.com/usgpo/uslm/tree/main/previous/"

    classDef blue fill:#cce5ff,stroke:#004085,color:#004085,stroke-width:1px;
    classDef green fill:#d4edda,stroke:#155724,color:#155724,stroke-width:1px;
    classDef orange fill:#fff3cd,stroke:#856404,color:#856404,stroke-width:1px;

```

-----

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
