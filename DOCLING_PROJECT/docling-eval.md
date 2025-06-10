---
created: 2025-03-21 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExNTIzMjFxZmYwcXBqeGZ0eWR4cXduOGtndzlrZXNjOWd4eDl1YTRjMyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/Kn5YFlengdRmw/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# Docling Eval
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
title: "Docling Eval"
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
      'lineColor': '#F8B229'
    }
  }
}%%
flowchart TD
    subgraph User_Interaction_and_CLI["User Interaction and CLI"]
        CLI["CLI<br>(docling_eval/cli/main.py)"]:::interface
    end

    subgraph Processing_Pipeline["Processing Pipeline"]
        CONV["Converters<br>(docling_eval/converters)"]:::proc
        EVAL["Evaluators<br>(docling_eval/evaluators/)"]:::proc
        VIS["Visualization<br>(docling_eval/visualisation)"]:::output
    end

    subgraph Benchmark_Modules["Benchmark Modules"]
        BM1["CVAT Annotation"]:::benchmark
        BM2["DocLayNet V1"]:::benchmark
        BM3["DocLayNet V2"]:::benchmark
        BM4["DP-Bench"]:::benchmark
        BM5["FUNSD"]:::benchmark
        BM6["OmniDocBench"]:::benchmark
        BM7["Tableformer<br>(Huggingface OTSL)"]:::benchmark
        BM8["XFund"]:::benchmark
    end

    subgraph Supporting_Modules["Supporting Modules"]
       CI["GitHub CI/CD"]:::support
       EX["Examples<br>(docs/examples)"]:::support
       TEST["Tests<br>(tests/)"]:::support
    end

    CLI -->|"passes input"| CONV
    CONV -->|"sends data"| BM1
    CONV -->|"sends data"| BM2
    CONV -->|"sends data"| BM3
    CONV -->|"sends data"| BM4
    CONV -->|"sends data"| BM5
    CONV -->|"sends data"| BM6
    CONV -->|"sends data"| BM7
    CONV -->|"sends data"| BM8
    BM1 -->|"invokes evaluation"| EVAL
    BM2 -->|"invokes evaluation"| EVAL
    BM3 -->|"invokes evaluation"| EVAL
    BM4 -->|"invokes evaluation"| EVAL
    BM5 -->|"invokes evaluation"| EVAL
    BM6 -->|"invokes evaluation"| EVAL
    BM7 -->|"invokes evaluation"| EVAL
    BM8 -->|"invokes evaluation"| EVAL
    CONV -->|"or directly"| EVAL
    EVAL -->|"produces metrics"| VIS

    CLI --- CI
    CLI --- EX
    CLI --- TEST

    click CLI "https://github.com/docling-project/docling-eval/blob/main/docling_eval/cli/main.py"
    click BM1 "https://github.com/docling-project/docling-eval/tree/main/docling_eval/benchmarks/cvat_annotation/"
    click BM2 "https://github.com/docling-project/docling-eval/blob/main/docling_eval/benchmarks/doclaynet_v1/create.py"
    click BM3 "https://github.com/docling-project/docling-eval/blob/main/docling_eval/benchmarks/doclaynet_v2/create.py"
    click BM4 "https://github.com/docling-project/docling-eval/blob/main/docling_eval/benchmarks/dpbench/create.py"
    click BM5 "https://github.com/docling-project/docling-eval/blob/main/docling_eval/benchmarks/funsd/create.py"
    click BM6 "https://github.com/docling-project/docling-eval/blob/main/docling_eval/benchmarks/omnidocbench/create.py"
    click BM7 "https://github.com/docling-project/docling-eval/blob/main/docling_eval/benchmarks/tableformer_huggingface_otsl/create.py"
    click BM8 "https://github.com/docling-project/docling-eval/blob/main/docling_eval/benchmarks/xfund/create.py"
    click CONV "https://github.com/docling-project/docling-eval/blob/main/docling_eval/converters/conversion.py"
    click EVAL "https://github.com/docling-project/docling-eval/tree/main/docling_eval/evaluators/"
    click VIS "https://github.com/docling-project/docling-eval/blob/main/docling_eval/visualisation/visualisations.py"
    click CI "https://github.com/docling-project/docling-eval/tree/main/.github/actions/setup-poetry/"
    click EX "https://github.com/docling-project/docling-eval/tree/main/docs/examples/"
    click TEST "https://github.com/docling-project/docling-eval/tree/main/tests/"

    classDef interface fill:#f9c3,stroke:#333,stroke-width:2px
    classDef proc fill:#bbf3,stroke:#333,stroke-width:2px
    classDef benchmark fill:#cfc3,stroke:#333,stroke-width:2px
    classDef output fill:#ffe3,stroke:#333,stroke-width:2px
    classDef support fill:#ddd3,stroke:#333,stroke-width:2px
    
```





---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
