---
created: 2025-07-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/DPGAlliance/dpg-community
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




# dpg-community repo project
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
title: "dpg-community repo project"
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
flowchart TD
    %% Actors
    Contributor(["Contributor"]):::enduser

    %% Internal Workflow
    subgraph "Content Repository (GitHub Repo)"
        RepoMain["GitHub Repo"]:::internal
        README["README.md"]:::internal
        CodeConduct["CODE_OF_CONDUCT.md"]:::internal
        Assets["assets/"]:::internal
        MeetingsDir["meetings/"]:::internal
        MeetingNote["Nov 22 - Tracking local implementations 2ee0e05baddb4a739bcb5dd5e8fb9ccb.md"]:::internal
    end

    BuildDeploy["Static Build & Deploy\n(GitHub Actions/GitHub Pages)"]:::internal
    Hosting["GitHub Pages CDN\n(Hosting)"]:::internal
    Browser(["End Users\n(Browser Client)"]):::enduser

    %% External Services
    subgraph "External Services"
        Discussions(["GitHub Discussions"]):::external
        Calendar(["Google Calendar"]):::external
        Airtable(["Airtable Form"]):::external
        GDocs(["Google Docs"]):::external
        DPGRegistry(["DPG Registry/Standard Repos"]):::external
    end

    %% Connections
    Contributor -->|"Git push / PR"| RepoMain
    RepoMain -->|"Git push triggers build"| BuildDeploy
    BuildDeploy -->|"deploy via HTTPS"| Hosting
    Hosting -->|"serve content (HTTPS)"| Browser

    Browser -->|click link| Discussions
    Browser -->|click link| Calendar
    Browser -->|click link| Airtable
    Browser -->|click link| GDocs
    Browser -->|click link| DPGRegistry

    %% Click Events
    click README "https://github.com/dpgalliance/dpg-community/blob/main/README.md"
    click CodeConduct "https://github.com/dpgalliance/dpg-community/blob/main/CODE_OF_CONDUCT.md"
    click Assets "https://github.com/dpgalliance/dpg-community/tree/main/assets/"
    click MeetingsDir "https://github.com/dpgalliance/dpg-community/tree/main/meetings/"
    click MeetingNote "https://github.com/dpgalliance/dpg-community/blob/main/meetings/Nov 22 - Tracking local implementations 2ee0e05baddb4a739bcb5dd5e8fb9ccb.md"

    %% Styles
    classDef internal fill:#D6EAF8,stroke:#2E86C1,color:#1B4F72
    classDef enduser fill:#D4EFDF,stroke:#27AE60,color:#145A32
    classDef external fill:#FCF3CF,stroke:#F1C40F,color:#B9770E
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