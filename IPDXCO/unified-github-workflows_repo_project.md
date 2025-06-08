---
created: 2025-06-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ipdxco/unified-github-workflows
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExM2VlNWRwbjN3OHBvazdxenh1aDhlY2IyMWVqeWhmbHNqOTllYWJwNyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zssaDhS7lyIF2/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# unified-github-workflows repo project
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---

```mermaid
---
title: "unified-github-workflows repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': { 'htmlLabels': true, 'curve': 'linear' },
    'fontFamily': 'Monaco',
    'themeVariables': {
      'primaryColor': '#222B2B',
      'primaryTextColor': '#F8B229',
      'lineColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#2221',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD',
      'fontSize': '20px'
    }
  }
}%%
flowchart TB
  subgraph "Unified CI Repo"
    templates[/templates/]:::static
    defaults["defaults.yml"]:::static
    versionData["templates/version.json"]:::static
    changelog["CHANGELOG.md"]:::static
    licenseAP["LICENSE-APACHE"]:::static
    licenseMIT["LICENSE-MIT"]:::static

    subgraph "Composite Actions"
      inspectReleaser["Inspect Releaser Action"]:::action
      readConfig["Read Config Action"]:::action
      readGoMod["Read Go Mod Action"]:::action
      renderTemplates["Render Templates Action"]:::action
    end

    subgraph "Shell Scripts"
      copyScript["copy-templates.sh"]:::action
      renderScript["render-template.sh"]:::action
      deleteScript["delete-templates.sh"]:::action
      updateGo["update-go.sh"]:::action
      closePRs["close-prs.sh"]:::action
    end

    subgraph "Workflows"
      copyTemplatesWF["Copy Templates Workflow"]:::workflow
      createPRsWF["Create PRs Workflow"]:::workflow
      mergePRsWF["Merge PRs Workflow"]:::workflow
      syncForksWF["Sync Forks Workflow"]:::workflow
      releaseCheckWF["Release Check Workflow"]:::workflow
      releaserWF["Releaser Workflow"]:::workflow
      tagpushWF["Tagpush Workflow"]:::workflow
    end
  end

  subgraph "GitHub Actions Runner"
    GHRunner["GitHub Actions Runner"]:::runner
  end

  subgraph "Target Repos"
    TargetRepos["Participating Repositories"]:::repo
  end

  GitHubAPI["GitHub API"]:::api

  %% Workflow executions
  copyTemplatesWF -->|runs on| GHRunner
  createPRsWF -->|runs on| GHRunner
  mergePRsWF -->|runs on| GHRunner
  syncForksWF -->|runs on| GHRunner
  releaseCheckWF -->|runs on| GHRunner
  releaserWF -->|runs on| GHRunner
  tagpushWF -->|runs on| GHRunner

  %% Runner invokes actions & scripts
  GHRunner --> renderTemplates
  GHRunner --> readConfig
  GHRunner --> readGoMod
  GHRunner --> inspectReleaser

  GHRunner --> copyScript
  GHRunner --> renderScript
  GHRunner --> deleteScript
  GHRunner --> updateGo
  GHRunner --> closePRs

  %% Static assets consumed
  renderTemplates --> defaults
  renderTemplates --> templates
  renderTemplates --> versionData

  copyTemplatesWF -->|uses| renderTemplates
  copyTemplatesWF -->|executes| copyScript
  createPRsWF -->|executes| closePRs
  mergePRsWF -->|executes| closePRs

  %% API interactions
  GHRunner -->|calls| GitHubAPI
  GitHubAPI -->|opens PRs| TargetRepos
  GitHubAPI -->|merges PRs| TargetRepos
  GitHubAPI -->|updates tags/releases| TargetRepos

  %% Click Events
  click inspectReleaser "https://github.com/ipdxco/unified-github-workflows/blob/main/.github/actions/inspect-releaser/action.yml"
  click readConfig "https://github.com/ipdxco/unified-github-workflows/blob/main/.github/actions/read-config/action.yml"
  click readGoMod "https://github.com/ipdxco/unified-github-workflows/blob/main/.github/actions/read-go-mod/action.yml"
  click renderTemplates "https://github.com/ipdxco/unified-github-workflows/blob/main/.github/actions/render-templates/action.yml"

  click copyTemplatesWF "https://github.com/ipdxco/unified-github-workflows/blob/main/.github/workflows/copy-templates.yml"
  click createPRsWF "https://github.com/ipdxco/unified-github-workflows/blob/main/.github/workflows/create-prs.yml"
  click mergePRsWF "https://github.com/ipdxco/unified-github-workflows/blob/main/.github/workflows/merge-prs.yml"
  click syncForksWF "https://github.com/ipdxco/unified-github-workflows/blob/main/.github/workflows/sync-forks.yml"
  click releaseCheckWF "https://github.com/ipdxco/unified-github-workflows/blob/main/.github/workflows/release-check.yml"
  click releaserWF "https://github.com/ipdxco/unified-github-workflows/blob/main/.github/workflows/releaser.yml"
  click tagpushWF "https://github.com/ipdxco/unified-github-workflows/blob/main/.github/workflows/tagpush.yml"

  click copyScript "https://github.com/ipdxco/unified-github-workflows/blob/main/scripts/copy-templates.sh"
  click renderScript "https://github.com/ipdxco/unified-github-workflows/blob/main/scripts/render-template.sh"
  click deleteScript "https://github.com/ipdxco/unified-github-workflows/blob/main/scripts/delete-templates.sh"
  click updateGo "https://github.com/ipdxco/unified-github-workflows/blob/main/scripts/update-go.sh"
  click closePRs "https://github.com/ipdxco/unified-github-workflows/blob/main/scripts/close-prs.sh"

  click templates "https://github.com/ipdxco/unified-github-workflows/tree/main/templates/"
  click defaults "https://github.com/ipdxco/unified-github-workflows/blob/main/defaults.yml"
  click versionData "https://github.com/ipdxco/unified-github-workflows/blob/main/templates/version.json"
  click changelog "https://github.com/ipdxco/unified-github-workflows/blob/main/CHANGELOG.md"
  click licenseAP "https://github.com/ipdxco/unified-github-workflows/tree/main/LICENSE-APACHE"
  click licenseMIT "https://github.com/ipdxco/unified-github-workflows/tree/main/LICENSE-MIT"

  classDef static fill:#9fcdff,stroke:#333,stroke-width:1px
  classDef action fill:#b3e6b3,stroke:#333,stroke-width:1px
  classDef workflow fill:#c2f0c2,stroke:#333,stroke-width:1px
  classDef api fill:#ffcc99,stroke:#333,stroke-width:1px
  classDef repo fill:#cccccc,stroke:#333,stroke-width:1px
  classDef runner fill:#d9d9ff,stroke:#333,stroke-width:1px
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