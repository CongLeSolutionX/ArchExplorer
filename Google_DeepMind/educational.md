---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/google-deepmind/educational
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




# educational repo project
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
title: "educational repo project"
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
    %% User
    User("Learner/Contributor"):::user

    %% GitHub Repository
    Repo["Educational-Resources Repo"]:::storage

    %% Tutorial Content inside Repo
    subgraph "Tutorial Content"
    direction LR
        subgraph "Introductory Notebooks"
        direction TB
            N1["fluttering_avians.ipynb"]:::content
            N2["fun_with_language.ipynb"]:::content
            N3["generative_models.ipynb"]:::content
            N4["protein_folding.ipynb"]:::content
            N5["reinforcement_learning.ipynb"]:::content
            N6["scientific_thinking.ipynb"]:::content
        end
        subgraph "Summer Schools Notebooks"
        direction TB
            S1["intro_to_graph_nets_tutorial_with_jraph.ipynb"]:::content
            S2["intro_to_python_numpy_for_deep_learning.ipynb"]:::content
            S3["intro_to_regression.ipynb"]:::content
            S4["intro_to_reinforcement_learning.ipynb"]:::content
            S5["intro_to_unsupervised_learning.ipynb"]:::content
        end
    end

    %% Google Colab Service
    Colab["Google Colab Service"]:::service

    %% Compute Environment
    subgraph "Colab Compute Environment"
    direction TB
        Runtime["Python Runtime + JAX + Jraph + NumPy + Matplotlib"]:::runtime
        Execution["Notebook Execution"]:::runtime
    end

    %% Connections
    User -->|"View README & links"| Repo
    User -->|"Click 'Open in Colab'"| Colab
    Colab -->|"HTTP GET raw .ipynb"| Repo
    Colab -->|"Provision dependencies"| Runtime
    Runtime -->|"Execute cells"| Execution
    Execution -->|"Stream results (plots, logs)"| User

    %% Click Events
    %% click Repo "https://github.com/google-deepmind/educational/tree/master/" 
    click N1 "https://github.com/google-deepmind/educational/tree/master//colabs/introductory"
    click N2 "https://github.com/google-deepmind/educational/tree/master//colabs/introductory"
    click N3 "https://github.com/google-deepmind/educational/tree/master//colabs/introductory"
    click N4 "https://github.com/google-deepmind/educational/tree/master//colabs/introductory"
    click N5 "https://github.com/google-deepmind/educational/tree/master//colabs/introductory"
    click N6 "https://github.com/google-deepmind/educational/tree/master//colabs/introductory"
    click S1 "https://github.com/google-deepmind/educational/tree/master//colabs/summer_schools"
    click S2 "https://github.com/google-deepmind/educational/tree/master//colabs/summer_schools"
    click S3 "https://github.com/google-deepmind/educational/tree/master//colabs/summer_schools"
    click S4 "https://github.com/google-deepmind/educational/tree/master//colabs/summer_schools"
    click S5 "https://github.com/google-deepmind/educational/tree/master//colabs/summer_schools"

    %% Styles
    classDef storage fill:#add8e6,stroke:#000,stroke-width:1px
    classDef service fill:#d3d3d3,stroke:#000,stroke-width:1px
    classDef runtime fill:#90ee90,stroke:#000,stroke-width:1px
    classDef user fill:#ffffe0,stroke:#000,stroke-width:1px
    classDef content fill:#dda0dd,stroke:#000,stroke-width:1px

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