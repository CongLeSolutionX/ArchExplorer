---
created: 2025-06-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/github/markup
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


# markup repo project
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
title: "markup repo project"
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
flowchart TD
    subgraph CLI_Layer[""CLI Layer""]
        CLI["CLI Entry Point<br/>bin/github-markup"]:::ancillary
    end

    subgraph Core_Library["Core Library"]
        CoreEntry["GitHub::Markup.render(file, content)<br/>.render_s"]:::core
        CoreModule["Core Module Definition<br/>lib/github/markup.rb"]:::core
        FormatRegistry["Format Registry<br/>lib/github/markups.rb"]:::core
    end

    subgraph Implementation_Layer["Implementation Layer"]
        Interface["Implementation#convert(content)<br/>lib/github/markup/implementation.rb"]:::core
        subgraph "Adapter Types"
            CommandImp["CommandImplementation<br/>lib/github/markup/command_implementation.rb"]:::adapter
            GemImp["GemImplementation<br/>lib/github/markup/gem_implementation.rb"]:::adapter
        end
        subgraph Format_Adapters["Format Adapters"]
            MD["Markdown Adapter<br/>lib/github/markup/markdown.rb"]:::adapter
            RDoc["RDoc Adapter<br/>lib/github/markup/rdoc.rb"]:::adapter
            Org["Org Adapter"]:::adapter
            Creole["Creole Adapter"]:::adapter
            MediaWiki["MediaWiki Adapter"]:::adapter
            RST["RST Adapter"]:::adapter
            Asciidoc["Asciidoc Adapter"]:::adapter
            Pod["Pod Adapter"]:::adapter
        end
        subgraph Command_Adapters["Command Adapters"]
            Pod2["pod2html<br/>lib/github/commands/pod2html"]:::adapter
            Pod62["pod62html<br/>lib/github/commands/pod62html"]:::adapter
            Rest2["rest2html<br/>lib/github/commands/rest2html"]:::adapter
        end
    end

    subgraph External_Converters["External Converters"]
        CM["CommonMarker Gem"]:::external
        RedCloth["RedCloth Gem"]:::external
        RDocLib["RDoc Library"]:::external
        OrgRuby["org-ruby Gem"]:::external
        CreoleLib["creole Gem"]:::external
        WikiCloth["wikicloth Gem"]:::external
        Docutils["docutils Tool"]:::external
        Asciidoctor["asciidoctor Tool"]:::external
        PodSimple["Pod::Simple"]:::external
    end

    Downstream["Downstream GitHub.com Pipeline"]:::external

    subgraph Ancillary_Components["Ancillary Components"]
        Bootstrap["script/bootstrap"]:::ancillary
        Gemspec["github-markup.gemspec"]:::ancillary
    end

    subgraph Test_Suite["Test Suite"]
        Tests["test/markup_test.rb & fixtures"]:::test
    end

    CLI -->|invokes| CoreEntry
    CoreEntry -->|calls| CoreModule
    CoreModule -->|uses registry| FormatRegistry
    CoreEntry -->|delegates| Interface
    FormatRegistry -->|lookup| Interface

    Interface -->|strategy| CommandImp
    Interface -->|strategy| GemImp

    CommandImp -->|shell-out| Pod2
    CommandImp -->|shell-out| Pod62
    CommandImp -->|shell-out| Rest2

    GemImp --> MD
    GemImp --> RDoc
    GemImp --> Org
    GemImp --> Creole
    GemImp --> MediaWiki
    GemImp --> RST
    GemImp --> Asciidoc
    GemImp --> Pod

    MD -->|gem api| CM
    RDoc -->|gem api| RedCloth
    RDoc -->|gem api| RDocLib
    Org -->|gem api| OrgRuby
    Creole -->|gem api| CreoleLib
    MediaWiki -->|gem api| WikiCloth
    RST -->|tool| Docutils
    Asciidoc -->|tool| Asciidoctor
    Pod -->|gem api| PodSimple

    Pod2 -->|tool| PodSimple
    Pod62 -->|tool| PodSimple
    Rest2 -->|tool| Docutils

    CoreEntry -->|outputs HTML| Downstream

    Bootstrap -->|prepares deps| External_Converters
    Gemspec -->|defines deps| External_Converters
    Tests -->|verifies| Interface
    Tests -->|fixtures for| FormatRegistry

    classDef core fill:#f9f,stroke:#333,stroke-width:1px
    classDef adapter fill:#cdf,stroke:#333,stroke-width:1px
    classDef external fill:#fcf,stroke:#333,stroke-width:1px
    classDef ancillary fill:#efe,stroke:#333,stroke-width:1px
    classDef test fill:#fee,stroke:#333,stroke-width:1px

    click CLI "https://github.com/github/markup/tree/master/bin/github-markup"
    click CoreEntry "https://github.com/github/markup/blob/master/lib/github-markup.rb"
    click CoreModule "https://github.com/github/markup/blob/master/lib/github/markup.rb"
    click FormatRegistry "https://github.com/github/markup/blob/master/lib/github/markups.rb"
    click Interface "https://github.com/github/markup/blob/master/lib/github/markup/implementation.rb"
    click CommandImp "https://github.com/github/markup/blob/master/lib/github/markup/command_implementation.rb"
    click GemImp "https://github.com/github/markup/blob/master/lib/github/markup/gem_implementation.rb"
    click MD "https://github.com/github/markup/blob/master/lib/github/markup/markdown.rb"
    click RDoc "https://github.com/github/markup/blob/master/lib/github/markup/rdoc.rb"
    click Pod2 "https://github.com/github/markup/tree/master/lib/github/commands/pod2html"
    click Pod62 "https://github.com/github/markup/tree/master/lib/github/commands/pod62html"
    click Rest2 "https://github.com/github/markup/tree/master/lib/github/commands/rest2html"
    click Bootstrap "https://github.com/github/markup/tree/master/script/bootstrap"
    click Gemspec "https://github.com/github/markup/blob/master/github-markup.gemspec"
    click Tests "https://github.com/github/markup/blob/master/test/markup_test.rb"
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