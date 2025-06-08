---
created: 2025-06-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ipdxco/github-as-code
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




# github-as-code repo project
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
title: "github-as-code repo project"
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
flowchart TD
    %% Actors and external
    Dev["Developer"]:::actor
    TargetOrgs["Target GitHub Orgs & Repos"]:::external

    %% Management Repository grouping
    subgraph "Management Repository (Code & Config)" 
        direction TB
        RepoRoot["/"]:::code

        subgraph "CI/CD Workflows" 
            direction TB
            Workflows[".github/workflows/*.yml"]:::ci
        end

        subgraph "Custom GitHub Actions"
            direction TB
            LocalActions[".github/actions/"]:::ci
        end

        Docs["docs/"]:::code
        Files["files/"]:::code

        subgraph "Config Templates & Schema"
            direction TB
            OrgTemplates["github/$ORGANIZATION_NAME.yml"]:::code
            JSONSchema["github/.schema.json"]:::code
        end

        subgraph "Scripts Source"
            direction TB
            subgraph "Entry & Env"
                MainTS["scripts/src/main.ts"]:::code
                EnvTS["scripts/src/env.ts"]:::code
                UtilsTS["scripts/src/utils.ts"]:::code
            end
            SyncTS["scripts/src/sync.ts"]:::code
            GitHubTS["scripts/src/github.ts"]:::code

            subgraph "YAML Parsing & Validation"
                SchemaTS["scripts/src/yaml/schema.ts"]:::code
                ConfigTS["scripts/src/yaml/config.ts"]:::code
            end

            subgraph "Resource Models & CRUD"
                direction TB
                memberTS["member.ts"]:::code
                repoTS["repository.ts"]:::code
                branchProtTS["repository-branch-protection-rule.ts"]:::code
                collabTS["repository-collaborator.ts"]:::code
                fileTS["repository-file.ts"]:::code
                labelTS["repository-label.ts"]:::code
                teamTS["repository-team.ts"]:::code
                teamMemberTS["team-member.ts"]:::code
                baseResourceTS["resource.ts"]:::code
            end

            subgraph "Action Modules"
                direction TB
                findShaTS["find-sha-for-plan.ts"]:::code
                fixYamlTS["fix-yaml-config.ts"]:::code
                formatYamlTS["format-yaml-config.ts"]:::code
                removeMembersTS["remove-inactive-members.ts"]:::code
                syncLabelsTS["sync-labels.ts"]:::code
                updatePRsTS["update-pull-requests.ts"]:::code
                SharedActions["shared/"]:::code
            end

            subgraph "Terraform Integration in CLI"
                direction TB
                LocalTS["scripts/src/terraform/locals.ts"]:::code
                SchemaTFTS["scripts/src/terraform/schema.ts"]:::code
                StateTFTS["scripts/src/terraform/state.ts"]:::code
            end
        end

        subgraph "Terraform Modules & Bootstrap"
            direction TB
            TFModules["terraform/"]:::infra
        end

        subgraph "Test Suite"
            direction TB
            TestsRoot["scripts/__tests__/"]:::code
        end
    end

    %% CI/CD Layer
    Dev -->|"opens PR"| RepoRoot
    RepoRoot -->|"triggers"| Workflows
    Workflows -->|"runs on"| LocalActions
    Workflows -->|"step: validate YAML"| SchemaTS
    SchemaTS -->|"uses"| ConfigTS
    Workflows -->|"step: terraform bootstrap"| TFModules
    TFModules -->|"state read/write"| StateTFTS
    Workflows -->|"step: sync"| MainTS
    MainTS -->|"invokes"| SyncTS
    SyncTS -->|"calls"| GitHubTS
    SyncTS -->|"uses"| LocalTS
    SyncTS -->|"uses"| SchemaTFTS
    SyncTS -->|"uses"| StateTFTS
    GitHubTS -->|"calls API"| TargetOrgs

    %% Test coverage
    TestsRoot ---|tests scripts| MainTS

    %% Click events
    click RepoRoot "https://github.com/ipdxco/github-as-code/tree/master//"
    click Workflows "https://github.com/ipdxco/github-as-code/blob/master/.github/workflows/*.yml"
    click LocalActions "https://github.com/ipdxco/github-as-code/tree/master/.github/actions/"
    click Docs "https://github.com/ipdxco/github-as-code/tree/master/docs/"
    click Files "https://github.com/ipdxco/github-as-code/tree/master/files/"
    click OrgTemplates "https://github.com/ipdxco/github-as-code/blob/master/github/$ORGANIZATION_NAME.yml"
    click JSONSchema "https://github.com/ipdxco/github-as-code/blob/master/github/.schema.json"
    click MainTS "https://github.com/ipdxco/github-as-code/blob/master/scripts/src/main.ts"
    click EnvTS "https://github.com/ipdxco/github-as-code/blob/master/scripts/src/env.ts"
    click UtilsTS "https://github.com/ipdxco/github-as-code/blob/master/scripts/src/utils.ts"
    click SyncTS "https://github.com/ipdxco/github-as-code/blob/master/scripts/src/sync.ts"
    click GitHubTS "https://github.com/ipdxco/github-as-code/blob/master/scripts/src/github.ts"
    click SchemaTS "https://github.com/ipdxco/github-as-code/blob/master/scripts/src/yaml/schema.ts"
    click ConfigTS "https://github.com/ipdxco/github-as-code/blob/master/scripts/src/yaml/config.ts"
    click memberTS "https://github.com/ipdxco/github-as-code/blob/master/scripts/src/resources/member.ts"
    click repoTS "https://github.com/ipdxco/github-as-code/blob/master/scripts/src/resources/repository.ts"
    click branchProtTS "https://github.com/ipdxco/github-as-code/blob/master/scripts/src/resources/repository-branch-protection-rule.ts"
    click collabTS "https://github.com/ipdxco/github-as-code/blob/master/scripts/src/resources/repository-collaborator.ts"
    click fileTS "https://github.com/ipdxco/github-as-code/blob/master/scripts/src/resources/repository-file.ts"
    click labelTS "https://github.com/ipdxco/github-as-code/blob/master/scripts/src/resources/repository-label.ts"
    click teamTS "https://github.com/ipdxco/github-as-code/blob/master/scripts/src/resources/repository-team.ts"
    click teamMemberTS "https://github.com/ipdxco/github-as-code/blob/master/scripts/src/resources/team-member.ts"
    click baseResourceTS "https://github.com/ipdxco/github-as-code/blob/master/scripts/src/resources/resource.ts"
    click findShaTS "https://github.com/ipdxco/github-as-code/blob/master/scripts/src/actions/find-sha-for-plan.ts"
    click fixYamlTS "https://github.com/ipdxco/github-as-code/blob/master/scripts/src/actions/fix-yaml-config.ts"
    click formatYamlTS "https://github.com/ipdxco/github-as-code/blob/master/scripts/src/actions/format-yaml-config.ts"
    click removeMembersTS "https://github.com/ipdxco/github-as-code/blob/master/scripts/src/actions/remove-inactive-members.ts"
    click syncLabelsTS "https://github.com/ipdxco/github-as-code/blob/master/scripts/src/actions/sync-labels.ts"
    click updatePRsTS "https://github.com/ipdxco/github-as-code/blob/master/scripts/src/actions/update-pull-requests.ts"
    click SharedActions "https://github.com/ipdxco/github-as-code/tree/master/scripts/src/actions/shared/"
    click LocalTS "https://github.com/ipdxco/github-as-code/blob/master/scripts/src/terraform/locals.ts"
    click SchemaTFTS "https://github.com/ipdxco/github-as-code/blob/master/scripts/src/terraform/schema.ts"
    click StateTFTS "https://github.com/ipdxco/github-as-code/blob/master/scripts/src/terraform/state.ts"
    click TFModules "https://github.com/ipdxco/github-as-code/tree/master/terraform/"
    click TestsRoot "https://github.com/ipdxco/github-as-code/tree/master/scripts/__tests__/"

    %% Styles
    classDef code fill:#cce5ff,stroke:#66a3ff,color:#003366;
    classDef ci fill:#d4f7d4,stroke:#29a329,color:#006600;
    classDef infra fill:#e6e6e6,stroke:#999999,color:#333333;
    classDef external fill:#ffe6cc,stroke:#ff9933,color:#663300;
    classDef actor fill:#f2f2f2,stroke:#666666,color:#333333;
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