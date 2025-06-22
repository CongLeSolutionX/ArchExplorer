---
created: 2025-06-21 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/usgpo/bulk-data
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExNG1xOHIwNWplcG1xZG9pYnhhMW5tN3gwbmdnd2lpZWp0emZ4bWcwcSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/xTkcExv186Kpei1pkI/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# bulk-data repo project
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
title: "bulk-data repo project"
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
    %% Documentation Zone
    subgraph "Documentation Zone"
        direction TB
        README["README.md"]:::doc
        CODEOWNERS["CODEOWNERS"]:::doc
        subgraph "Markdown User Guides"
            direction TB
            BILLSGuide["Bills-XML-User-Guide.md"]:::doc
            BILLSSummaryGuide["Bills-Summary-XML-User-Guide.md"]:::doc
            CFRGuide["CFR-XML_User-Guide.md"]:::doc
            ECFRGuide["ECFR-XML-User-Guide.md"]:::doc
            FRGuide["FR-XML_User-Guide.md"]:::doc
        end
        subgraph "PDF Guides"
            direction TB
            pdfBILLS["BILLS-XML_User-Guide-v2.pdf"]:::doc
            pdfBILLSUM["BILLSUM-XML_User-Guide-v2.pdf"]:::doc
            pdfCFR["CFR-XML_User-Guide-v1.pdf"]:::doc
            pdfFR["FR-XML_User-Guide-v1.pdf"]:::doc
        end
        subgraph "Sample XML Snapshots"
            direction TB
            subgraph "Current Snapshots"
                direction TB
                curECFR1["ECFR-title1.xml"]:::doc
                curECFR14["ECFR-title14.xml"]:::doc
                curECFR15["ECFR-title15.xml"]:::doc
                curFR["FR-2024-02-12.xml"]:::doc
            end
            subgraph "Updated Snapshots"
                direction TB
                updECFR1["ECFR-title1.xml"]:::doc
                updECFR14["ECFR-title14.xml"]:::doc
                updECFR15["ECFR-title15.xml"]:::doc
                updFR["FR-2024-02-12.xml"]:::doc
            end
        end
    end

    %% Service Zone
    subgraph "Service Zone"
        direction TB
        API["GPO govinfo Bulkdata API"]:::api
        BillsEndpoint["/bulkdata/xml/BILLS/{congress}/{chamber}/{doc}"]:::api
        JSONEndpoint["/bulkdata/json/{collection}/{year}/{id}"]:::api
        FREndpoint["/bulkdata/FR/{year}/{month}/{day}"]:::api
    end

    %% User Zone
    subgraph "User Zone"
        direction TB
        User["Users (CLI, scripts, browser)"]:::user
    end

    %% Connections
    User -->|"Read guides, download PDFs"| README
    README -->|"Guidance on endpoints"| API
    User -->|"GET /bulkdata/... → 200 OK"| API
    API -->|"Returns XML/JSON payload"| User
    BILLSGuide -->|Uses samples| curECFR1
    ECFRGuide -->|Diff examples| updECFR1

    %% Click Events
    click README "https://github.com/usgpo/bulk-data/blob/main/README.md"
    click CODEOWNERS "https://github.com/usgpo/bulk-data/tree/main/CODEOWNERS"
    click BILLSGuide "https://github.com/usgpo/bulk-data/blob/main/Bills-XML-User-Guide.md"
    click BILLSSummaryGuide "https://github.com/usgpo/bulk-data/blob/main/Bills-Summary-XML-User-Guide.md"
    click CFRGuide "https://github.com/usgpo/bulk-data/blob/main/CFR-XML_User-Guide.md"
    click ECFRGuide "https://github.com/usgpo/bulk-data/blob/main/ECFR-XML-User-Guide.md"
    click FRGuide "https://github.com/usgpo/bulk-data/blob/main/FR-XML_User-Guide.md"
    click pdfBILLS "https://github.com/usgpo/bulk-data/blob/main/pdf/BILLS-XML_User-Guide-v2.pdf"
    click pdfBILLSUM "https://github.com/usgpo/bulk-data/blob/main/pdf/BILLSUM-XML_User-Guide-v2.pdf"
    click pdfCFR "https://github.com/usgpo/bulk-data/blob/main/pdf/CFR-XML_User-Guide-v1.pdf"
    click pdfFR "https://github.com/usgpo/bulk-data/blob/main/pdf/FR-XML_User-Guide-v1.pdf"
    click curECFR1 "https://github.com/usgpo/bulk-data/blob/main/ndash-changes-March2024/current/ECFR-title1.xml"
    click curECFR14 "https://github.com/usgpo/bulk-data/blob/main/ndash-changes-March2024/current/ECFR-title14.xml"
    click curECFR15 "https://github.com/usgpo/bulk-data/blob/main/ndash-changes-March2024/current/ECFR-title15.xml"
    click curFR "https://github.com/usgpo/bulk-data/blob/main/ndash-changes-March2024/current/FR-2024-02-12.xml"
    click updECFR1 "https://github.com/usgpo/bulk-data/blob/main/ndash-changes-March2024/updated/ECFR-title1.xml"
    click updECFR14 "https://github.com/usgpo/bulk-data/blob/main/ndash-changes-March2024/updated/ECFR-title14.xml"
    click updECFR15 "https://github.com/usgpo/bulk-data/blob/main/ndash-changes-March2024/updated/ECFR-title15.xml"
    click updFR "https://github.com/usgpo/bulk-data/blob/main/ndash-changes-March2024/updated/FR-2024-02-12.xml"

    %% Styles
    classDef doc fill:#D0E6FF,stroke:#004E9F
    classDef api fill:#D0FFD0,stroke:#009F00
    classDef user fill:#FFE4C4,stroke:#CC6600


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
