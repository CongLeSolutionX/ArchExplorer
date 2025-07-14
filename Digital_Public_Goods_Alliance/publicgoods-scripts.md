---
created: 2025-07-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/DPGAlliance/publicgoods-scripts
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




# publicgoods-scripts repo project
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
title: "publicgoods-scripts repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright © 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': { 'htmlLabels': true, 'curve': 'linear'},
    'fontFamily': 'Monaco',
    'themeVariables': {
      'primaryColor': '#22BB',
      'primaryTextColor': '#F8B229',
      'lineColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#EEF2',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD',
      'fontSize': '15px'
    }
  }
}%%
flowchart TB
    %% GitHub and CI
    subgraph "GitHub"
        GHRepo["Monorepo (package.json, package-lock.json)"]:::repo
        subgraph "Workflows"
            Auto["auto.yml"]:::repo
            Feature["feature.yml"]:::repo
            TestWF["test.yml"]:::repo
        end
    end
    GHRepo --> CI["GitHub Actions CI"]:::repo
    Auto --> CI
    Feature --> CI
    TestWF --> CI

    %% CI processes
    CI --> Static["scripts/static.bash"]:::process
    CI --> NodeAuto["Node Automation (packages/automation)"]:::process
    CI --> FEBuilds["Front-End Builds"]:::process
    CI --> Move["scripts/moveFiles.bash"]:::process
    CI --> TestSuite["TestAutomation Suite"]:::test
    CI --> Deploy["Deploy to GitHub Pages"]:::process

    %% Static Bash
    click Static "https://github.com/dpgalliance/publicgoods-scripts/blob/main/scripts/static.bash"

    %% Node Automation Package
    subgraph "packages/automation"
        Index["index.js"]:::process
        Consolidate["consolidate_data.js"]:::process
        GenDPGS["generate_dpgs.js"]:::process
        GenNom["generate_nominees.js"]:::process
        Template["registry_template.html"]:::process
    end
    NodeAuto --> Index
    NodeAuto --> Consolidate
    NodeAuto --> GenDPGS
    NodeAuto --> GenNom
    NodeAuto --> Template

    click Index "https://github.com/dpgalliance/publicgoods-scripts/blob/main/packages/automation/index.js"
    click Consolidate "https://github.com/dpgalliance/publicgoods-scripts/blob/main/packages/automation/consolidate_data.js"
    click GenDPGS "https://github.com/dpgalliance/publicgoods-scripts/blob/main/packages/automation/generate_dpgs.js"
    click GenNom "https://github.com/dpgalliance/publicgoods-scripts/blob/main/packages/automation/generate_nominees.js"
    click Template "https://github.com/dpgalliance/publicgoods-scripts/blob/main/packages/automation/registry_template.html"

    %% Front-End Builds
    subgraph "Front-End Packages"
        subgraph Registry
            R_pkg["package.json"]:::repo
            R_index["src/index.js"]:::process
            R_css["src/index.css"]:::process
            R_resize["public/ResizeSensor.js"]:::process
            R_sw["src/serviceWorker.js"]:::process
        end
        subgraph Eligibility
            E_pkg["package.json"]:::repo
            E_index["src/index.js"]:::process
            E_css["src/index.css"]:::process
            E_comp["src/components/*.js"]:::process
            E_api["src/api/quizQuestions.js"]:::process
        end
        subgraph Map
            M_pkg["package.json"]:::repo
            M_config["next.config.js"]:::process
            M_pages["pages/*.js"]:::process
            M_comp["components/*.js"]:::process
            M_public["public/*.geojson, *.csv"]:::process
            M_script["scripts/pointToPolygon.js"]:::process
            M_style["styles/global.css"]:::process
        end
        subgraph Community
            C_index["index.js"]:::process
            C_html["index.html"]:::process
        end
        subgraph HelpCenter
            H_index["index.js"]:::process
            H_html["index.html"]:::process
        end
        subgraph Roadmap
            Rm_pkg["package.json"]:::repo
            Rm_index["src/index.js"]:::process
            Rm_css["src/index.css"]:::process
            Rm_comp["src/components/Roadmap.js"]:::process
            Rm_style["src/components/style.css"]:::process
        end
    end
    FEBuilds --> Registry
    FEBuilds --> Eligibility
    FEBuilds --> Map
    FEBuilds --> Community
    FEBuilds --> HelpCenter
    FEBuilds --> Roadmap

    click R_pkg "https://github.com/dpgalliance/publicgoods-scripts/blob/main/packages/registry/package.json"
    click R_index "https://github.com/dpgalliance/publicgoods-scripts/blob/main/packages/registry/src/index.js"
    click R_css "https://github.com/dpgalliance/publicgoods-scripts/blob/main/packages/registry/src/index.css"
    click R_resize "https://github.com/dpgalliance/publicgoods-scripts/blob/main/packages/registry/public/ResizeSensor.js"
    click R_sw "https://github.com/dpgalliance/publicgoods-scripts/blob/main/packages/registry/src/serviceWorker.js"

    click E_pkg "https://github.com/dpgalliance/publicgoods-scripts/blob/main/packages/eligibility/package.json"
    click E_index "https://github.com/dpgalliance/publicgoods-scripts/blob/main/packages/eligibility/src/index.js"
    click E_css "https://github.com/dpgalliance/publicgoods-scripts/blob/main/packages/eligibility/src/index.css"
    click E_comp "https://github.com/dpgalliance/publicgoods-scripts/blob/main/packages/eligibility/src/components/*.js"
    click E_api "https://github.com/dpgalliance/publicgoods-scripts/blob/main/packages/eligibility/src/api/quizQuestions.js"

    click M_pkg "https://github.com/dpgalliance/publicgoods-scripts/blob/main/packages/map/package.json"
    click M_config "https://github.com/dpgalliance/publicgoods-scripts/blob/main/packages/map/next.config.js"
    click M_pages "https://github.com/dpgalliance/publicgoods-scripts/blob/main/packages/map/pages/_app.js"
    click M_pages "https://github.com/dpgalliance/publicgoods-scripts/blob/main/packages/map/pages/_document.js"
    click M_pages "https://github.com/dpgalliance/publicgoods-scripts/blob/main/packages/map/pages/index.js"
    click M_pages "https://github.com/dpgalliance/publicgoods-scripts/blob/main/packages/map/pages/helper.js"
    click M_comp "https://github.com/dpgalliance/publicgoods-scripts/blob/main/packages/map/components/*.js"
    click M_public "https://github.com/dpgalliance/publicgoods-scripts/blob/main/packages/map/public/*.geojson, *.csv"
    click M_script "https://github.com/dpgalliance/publicgoods-scripts/blob/main/packages/map/scripts/pointToPolygon.js"
    click M_style "https://github.com/dpgalliance/publicgoods-scripts/blob/main/packages/map/styles/global.css"

    click C_index "https://github.com/dpgalliance/publicgoods-scripts/blob/main/packages/community/index.js"
    click C_html "https://github.com/dpgalliance/publicgoods-scripts/blob/main/packages/community/index.html"

    click H_index "https://github.com/dpgalliance/publicgoods-scripts/blob/main/packages/helpcenter/index.js"
    click H_html "https://github.com/dpgalliance/publicgoods-scripts/blob/main/packages/helpcenter/index.html"

    click Rm_pkg "https://github.com/dpgalliance/publicgoods-scripts/blob/main/packages/roadmap/package.json"
    click Rm_index "https://github.com/dpgalliance/publicgoods-scripts/blob/main/packages/roadmap/src/index.js"
    click Rm_css "https://github.com/dpgalliance/publicgoods-scripts/blob/main/packages/roadmap/src/index.css"
    click Rm_comp "https://github.com/dpgalliance/publicgoods-scripts/blob/main/packages/roadmap/src/components/Roadmap.js"
    click Rm_style "https://github.com/dpgalliance/publicgoods-scripts/blob/main/packages/roadmap/src/components/style.css"

    %% Move Files
    click Move "https://github.com/dpgalliance/publicgoods-scripts/blob/main/scripts/moveFiles.bash"

    %% Test Automation Suite
    subgraph "TestAutomation/DPGAUIAutomation"
        Pom["pom.xml"]:::test
        AppJava["src/main/java/org/example/App.java"]:::test
        API_tests["src/test/java/APIScripts/*.java"]:::test
        UI_tests["src/test/java/uiscripts/*.java"]:::test
        Utils["src/test/java/utilities/BrowserConfig.java"]:::test
        TestNG["testNG.xml"]:::test
        Allure["allure-results/"]:::test
    end
    TestSuite --> Pom
    TestSuite --> AppJava
    TestSuite --> API_tests
    TestSuite --> UI_tests
    TestSuite --> Utils
    TestSuite --> TestNG
    TestSuite --> Allure

    click Pom "https://github.com/dpgalliance/publicgoods-scripts/blob/main/TestAutomation/DPGAUIAutomation/pom.xml"
    click AppJava "https://github.com/dpgalliance/publicgoods-scripts/blob/main/TestAutomation/DPGAUIAutomation/src/main/java/org/example/App.java"
    click API_tests "https://github.com/dpgalliance/publicgoods-scripts/blob/main/TestAutomation/DPGAUIAutomation/src/test/java/APIScripts/*.java"
    click UI_tests "https://github.com/dpgalliance/publicgoods-scripts/blob/main/TestAutomation/DPGAUIAutomation/src/test/java/uiscripts/*.java"
    click Utils "https://github.com/dpgalliance/publicgoods-scripts/blob/main/TestAutomation/DPGAUIAutomation/src/test/java/utilities/BrowserConfig.java"
    click TestNG "https://github.com/dpgalliance/publicgoods-scripts/blob/main/TestAutomation/DPGAUIAutomation/testNG.xml"
    click Allure "https://github.com/dpgalliance/publicgoods-scripts/tree/main/TestAutomation/DPGAUIAutomation/allure-results/"

    %% Deploy & Hosting
    Deploy --> Public["publicgoods-website repo"]:::repo
    Public --> User["End User Browser (digitalpublicgoods.net)"]:::external

    classDef repo fill:#D6E4F0,stroke:#3182CE;
    classDef process fill:#E6F4EA,stroke:#2F855A;
    classDef external fill:#FFFAE6,stroke:#D69E2E;
    classDef test fill:#FEEBC8,stroke:#DD6B20,stroke-dasharray: 5 5;

```

-----


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