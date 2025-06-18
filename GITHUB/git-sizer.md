---
created: 2025-06-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/github/git-sizer
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


# git-sizer repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>

---


```mermaid
---
title: "git-sizer repo project"
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
    %% CLI Frontend
    CLI["CLI Frontend"]:::core
    click CLI "https://github.com/github/git-sizer/blob/master/git-sizer.go"

    %% Git Invocation Layer
    subgraph "Git Invocation Layer"
        GitCore["git/git.go"]:::core
        click GitCore "https://github.com/github/git-sizer/blob/master/git/git.go"
        GitBin["git/git_bin.go"]:::core
        click GitBin "https://github.com/github/git-sizer/blob/master/git/git_bin.go"
        GitConfig["git/gitconfig.go"]:::core
        click GitConfig "https://github.com/github/git-sizer/blob/master/git/gitconfig.go"
    end

    %% Iterators & Filters
    subgraph "Iterators & Filters"
        subgraph "Object Iterators"
            ObjIter["obj_iter.go"]:::iter
            click ObjIter "https://github.com/github/git-sizer/blob/master/git/obj_iter.go"
            BatchIter["batch_obj_iter.go"]:::iter
            click BatchIter "https://github.com/github/git-sizer/blob/master/git/batch_obj_iter.go"
            HeadIter["obj_head_iter.go"]:::iter
            click HeadIter "https://github.com/github/git-sizer/blob/master/git/obj_head_iter.go"
            Resolver["obj_resolver.go"]:::iter
            click Resolver "https://github.com/github/git-sizer/blob/master/git/obj_resolver.go"
            Commit["commit.go"]:::iter
            click Commit "https://github.com/github/git-sizer/blob/master/git/commit.go"
            Tree["tree.go"]:::iter
            click Tree "https://github.com/github/git-sizer/blob/master/git/tree.go"
            Tag["tag.go"]:::iter
            click Tag "https://github.com/github/git-sizer/blob/master/git/tag.go"
            RefIter["ref_iter.go"]:::iter
            click RefIter "https://github.com/github/git-sizer/blob/master/git/ref_iter.go"
        end
        subgraph "Reference Filtering"
            RefFilter["ref_filter.go"]:::iter
            click RefFilter "https://github.com/github/git-sizer/blob/master/git/ref_filter.go"
            FilterVal["filter_value.go"]:::iter
            click FilterVal "https://github.com/github/git-sizer/blob/master/internal/refopts/filter_value.go"
            FilterGroupVal["filter_group_value.go"]:::iter
            click FilterGroupVal "https://github.com/github/git-sizer/blob/master/internal/refopts/filter_group_value.go"
            RefGroup["ref_group.go"]:::iter
            click RefGroup "https://github.com/github/git-sizer/blob/master/internal/refopts/ref_group.go"
            RefGroupBuilder["ref_group_builder.go"]:::iter
            click RefGroupBuilder "https://github.com/github/git-sizer/blob/master/internal/refopts/ref_group_builder.go"
            ShowGrouper["show_ref_grouper.go"]:::iter
            click ShowGrouper "https://github.com/github/git-sizer/blob/master/internal/refopts/show_ref_grouper.go"
        end
    end

    %% Metric Calculators
    subgraph "Metric Calculators"
        subgraph "Counts Module"
            Counts["counts.go"]:::calc
            click Counts "https://github.com/github/git-sizer/blob/master/counts/counts.go"
            HumanC["human.go"]:::calc
            click HumanC "https://github.com/github/git-sizer/blob/master/counts/human.go"
        end
        subgraph "Sizes Module"
            Sizes["sizes.go"]:::calc
            click Sizes "https://github.com/github/git-sizer/blob/master/sizes/sizes.go"
            Graph["graph.go"]:::calc
            click Graph "https://github.com/github/git-sizer/blob/master/sizes/graph.go"
            Footnotes["footnotes.go"]:::calc
            click Footnotes "https://github.com/github/git-sizer/blob/master/sizes/footnotes.go"
            Grouper["grouper.go"]:::calc
            click Grouper "https://github.com/github/git-sizer/blob/master/sizes/grouper.go"
            ExplicitRoot["explicit_root.go"]:::calc
            click ExplicitRoot "https://github.com/github/git-sizer/blob/master/sizes/explicit_root.go"
            PathResolver["path_resolver.go"]:::calc
            click PathResolver "https://github.com/github/git-sizer/blob/master/sizes/path_resolver.go"
        end
        Meter["meter.go"]:::calc
        click Meter "https://github.com/github/git-sizer/blob/master/meter/meter.go"
    end

    %% Output Formatter
    Output["Output Formatter (table/JSON)"]:::fmt
    click Output "https://github.com/github/git-sizer/blob/master/sizes/output.go"

    %% Utilities
    subgraph "Utilities"
        IsattyEn["isatty_enabled.go"]:::util
        click IsattyEn "https://github.com/github/git-sizer/blob/master/isatty/isatty_enabled.go"
        IsattyDis["isatty_disabled.go"]:::util
        click IsattyDis "https://github.com/github/git-sizer/blob/master/isatty/isatty_disabled.go"
        NegBool["negated_bool_value.go"]:::util
        click NegBool "https://github.com/github/git-sizer/blob/master/negated_bool_value.go"
    end

    %% Build & CI
    subgraph "Build & CI"
        subgraph "Scripts"
            BS["bootstrap"]:::ci
            click BS "https://github.com/github/git-sizer/tree/master/script/bootstrap"
            BD["build"]:::ci
            click BD "https://github.com/github/git-sizer/tree/master/script/build"
            CIBuild["cibuild"]:::ci
            click CIBuild "https://github.com/github/git-sizer/tree/master/script/cibuild"
            EnsureGo["ensure-go-installed.sh"]:::ci
            click EnsureGo "https://github.com/github/git-sizer/blob/master/script/ensure-go-installed.sh"
            GoScript["go"]:::ci
            click GoScript "https://github.com/github/git-sizer/tree/master/script/go"
            GoFmt["gofmt"]:::ci
            click GoFmt "https://github.com/github/git-sizer/tree/master/script/gofmt"
            InstallVendored["install-vendored-go"]:::ci
            click InstallVendored "https://github.com/github/git-sizer/tree/master/script/install-vendored-go"
        end
        subgraph "CI Workflows"
            LintCI["lint.yml"]:::ci
            click LintCI "https://github.com/github/git-sizer/blob/master/.github/workflows/lint.yml"
            TestCI["test.yml"]:::ci
            click TestCI "https://github.com/github/git-sizer/blob/master/.github/workflows/test.yml"
            ReleaseCI["release.yml"]:::ci
            click ReleaseCI "https://github.com/github/git-sizer/blob/master/.github/workflows/release.yml"
        end
    end

    %% Execution Terminal
    Terminal["Terminal (stdout)"]:::external

    %% Data Flow
    CLI -->|"invoke"| GitCore
    GitCore -->|"stream objects"| ObjIter
    ObjIter -->|"objects"| RefFilter
    RefFilter -->|"filtered refs"| Counts
    RefFilter -->|"filtered refs"| Sizes
    RefFilter -->|"filtered refs"| Meter
    Counts -->|"metrics"| Output
    Sizes -->|"metrics"| Output
    Meter -->|"metrics"| Output
    Output -->|"render"| Terminal
    IsattyEn -->|"detect tty"| Output
    IsattyDis -->|"detect tty"| Output

    %% Styles
    classDef core fill:#ADE8F4,stroke:#000,stroke-width:1px
    classDef iter fill:#B7E4C7,stroke:#000,stroke-width:1px
    classDef calc fill:#FFB703,stroke:#000,stroke-width:1px
    classDef fmt fill:#9D4EDD,stroke:#000,stroke-width:1px
    classDef util fill:#E0E0E0,stroke:#000,stroke-width:1px
    classDef ci fill:#CCCCCC,stroke:#000,stroke-width:1px
    classDef external fill:#F0EFEB,stroke:#000,stroke-width:1px
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
 
  Closing_quote ~~~ My_Meme

  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

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