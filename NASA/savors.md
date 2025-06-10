---
created: 2025-03-16 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExdHdpcnJlbjRma3BjYXJ0OW1oamxwNHliZDVrdzRpemM4ZXljdHMxcyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/3o7TKuWWflyTslSoUM/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# savors
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



```mermaid
---
title: "savors"
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
    'flowchart': {'htmlLabels': true, 'curve': 'basis' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#ffff',
      'primaryTextColor': '#2ff9',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
flowchart TD
    CLI["CLI Interface"]:::core
    CoreEngine["Core Engine<br>(Perl/Savors)"]:::core
    ConfigDoc["Configuration & Documentation"]:::config

    subgraph Visualization_Modules["Visualization Modules"]
        axis["Axis"]:::vis
        chart["Chart"]:::vis
        cloud["Cloud"]:::vis
        graph_module["Graph"]:::vis
        grid["Grid"]:::vis
        map["Map"]:::vis
        rain["Rain"]:::vis
        tree["Tree"]:::vis
    end

    subgraph Auxiliary_Libraries["Auxiliary Libraries"]
        libCloud["Cloud Support"]:::aux
        libMaps["Maps Data"]:::aux
    end

    CLI -->|"input"| CoreEngine
    ConfigDoc -->|"configures"| CoreEngine

    CoreEngine -->|"orchestrates"| axis
    CoreEngine -->|"orchestrates"| chart
    CoreEngine -->|"orchestrates"| cloud
    CoreEngine -->|"orchestrates"| graph_module
    CoreEngine -->|"orchestrates"| grid
    CoreEngine -->|"orchestrates"| map
    CoreEngine -->|"orchestrates"| rain
    CoreEngine -->|"orchestrates"| tree

    CoreEngine <-->|"depends"| libCloud
    CoreEngine <-->|"depends"| libMaps

    cloud -->|"renders"| libCloud
    map -->|"renders"| libMaps

    click CLI "https://github.com/pkolano/savors/blob/master/perl/savors.pl"
    click CoreEngine "https://github.com/pkolano/savors/tree/master/perl/Savors"
    click axis "https://github.com/pkolano/savors/blob/master/perl/Savors/View/Axis.pm"
    click chart "https://github.com/pkolano/savors/blob/master/perl/Savors/View/Chart.pm"
    click cloud "https://github.com/pkolano/savors/blob/master/perl/Savors/View/Cloud.pm"
    click graph_module "https://github.com/pkolano/savors/blob/master/perl/Savors/View/Graph.pm"
    click grid "https://github.com/pkolano/savors/blob/master/perl/Savors/View/Grid.pm"
    click map "https://github.com/pkolano/savors/blob/master/perl/Savors/View/Map.pm"
    click rain "https://github.com/pkolano/savors/blob/master/perl/Savors/View/Rain.pm"
    click tree "https://github.com/pkolano/savors/blob/master/perl/Savors/View/Tree.pm"
    click libCloud "https://github.com/pkolano/savors/tree/master/lib/cloud"
    click libMaps "https://github.com/pkolano/savors/tree/master/lib/maps"
    click ConfigDoc "https://github.com/pkolano/savors/tree/master/etc/savorsrc"

    classDef core fill:#c1a9,stroke:#000,stroke-width:2px
    classDef vis fill:#ef29,stroke:#000,stroke-width:2px
    classDef aux fill:#f5c9,stroke:#000,stroke-width:2px
    classDef config fill:#f2a9,stroke:#000,stroke-width:2px

```




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
