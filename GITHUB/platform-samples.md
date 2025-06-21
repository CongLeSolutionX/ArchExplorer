---
created: 2025-06-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/github/platform-samples
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


# platform-samples repo project
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
title: "platform-samples repo project"
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
    %% CI Workflows
    subgraph ".github/workflows"
        CI_CodeQL["codeql.yml"]:::ci
        CI_Combine["combine-prs.yml"]:::ci
    end

    %% API Samples
    subgraph "API Samples"
        API_Bash["bash"]:::sample
        API_Go["golang"]:::sample
        API_Groovy["groovy"]:::sample
        API_Java["java"]:::sample
        API_JS["javascript"]:::sample
        API_PS["powershell"]:::sample
        API_Py["python"]:::sample
        API_Rb["ruby"]:::sample
        API_Scala["scala"]:::sample
    end

    %% GitHub App Example
    subgraph "GitHub App Example"
        App_Ruby["app-issue-creator (Ruby)"]:::sample
    end

    %% GraphQL Samples
    subgraph "GraphQL Samples"
        GraphQL["graphql"]:::sample
    end

    %% Webhook Consumers
    subgraph "Webhook Consumers"
        Hooks_Jenkins["jenkins"]:::sample
        Hooks_Python["python"]:::sample
        Hooks_Ruby["ruby"]:::sample
    end

    %% Pre-receive Hooks
    subgraph "Pre-receive Hooks"
        PR_Hooks["shell scripts"]:::sample
    end

    %% Maintenance Scripts
    subgraph "Maintenance Scripts"
        Scripts["scripts"]:::sample
    end

    %% SQL Reports
    subgraph "SQL Reports"
        SQL_Audit["audit"]:::sample
        SQL_Metrics["metrics"]:::sample
        SQL_Security["security"]:::sample
    end

    %% Microsoft Graph Docs
    subgraph "Microsoft Graph Docs"
        MSGraph["microsoft-graph-api"]:::doc
    end

    %% External Services
    GitHubREST["GitHub REST API"]:::external
    GitHubGraphQL["GitHub GraphQL API"]:::external
    GitHubWebhooks["GitHub Webhooks"]:::external
    GHEnterprise["GitHub Enterprise Server"]:::external
    EnterpriseDB["Enterprise DB"]:::external
    AzureAD["Microsoft Graph API / Azure AD"]:::external

    %% CI to Samples
    CI_CodeQL -->|lint/test/build| API_Bash
    CI_CodeQL -->|lint/test/build| API_Go
    CI_CodeQL -->|lint/test/build| API_Groovy
    CI_CodeQL -->|lint/test/build| API_Java
    CI_CodeQL -->|lint/test/build| API_JS
    CI_CodeQL -->|lint/test/build| API_PS
    CI_CodeQL -->|lint/test/build| API_Py
    CI_CodeQL -->|lint/test/build| API_Rb
    CI_CodeQL -->|lint/test/build| API_Scala
    CI_CodeQL -->|lint/test/build| App_Ruby
    CI_CodeQL -->|lint/test/build| GraphQL
    CI_CodeQL -->|lint/test/build| Hooks_Jenkins
    CI_CodeQL -->|lint/test/build| Hooks_Python
    CI_CodeQL -->|lint/test/build| Hooks_Ruby
    CI_CodeQL -->|lint/test/build| PR_Hooks
    CI_CodeQL -->|lint/test/build| Scripts
    CI_CodeQL -->|lint/test/build| SQL_Audit
    CI_CodeQL -->|lint/test/build| SQL_Metrics
    CI_CodeQL -->|lint/test/build| SQL_Security
    CI_CodeQL -->|lint/test/build| MSGraph

    CI_Combine -->|combine PRs| API_Bash
    CI_Combine -->|combine PRs| API_Go
    CI_Combine -->|combine PRs| API_Groovy
    CI_Combine -->|combine PRs| API_Java
    CI_Combine -->|combine PRs| API_JS
    CI_Combine -->|combine PRs| API_PS
    CI_Combine -->|combine PRs| API_Py
    CI_Combine -->|combine PRs| API_Rb
    CI_Combine -->|combine PRs| API_Scala
    CI_Combine -->|combine PRs| App_Ruby
    CI_Combine -->|combine PRs| GraphQL
    CI_Combine -->|combine PRs| Hooks_Jenkins
    CI_Combine -->|combine PRs| Hooks_Python
    CI_Combine -->|combine PRs| Hooks_Ruby
    CI_Combine -->|combine PRs| PR_Hooks
    CI_Combine -->|combine PRs| Scripts
    CI_Combine -->|combine PRs| SQL_Audit
    CI_Combine -->|combine PRs| SQL_Metrics
    CI_Combine -->|combine PRs| SQL_Security
    CI_Combine -->|combine PRs| MSGraph

    %% Sample interactions
    API_Bash -->|HTTP| GitHubREST
    API_Go -->|HTTP| GitHubREST
    API_Groovy -->|HTTP| GitHubREST
    API_Java -->|HTTP| GitHubREST
    API_JS -->|HTTP| GitHubREST
    API_PS -->|HTTP| GitHubREST
    API_Py -->|HTTP| GitHubREST
    API_Rb -->|HTTP| GitHubREST
    API_Scala -->|HTTP| GitHubREST
    App_Ruby -->|HTTP| GitHubREST
    GraphQL -->|HTTP| GitHubGraphQL
    GraphQL -->|UI Demo| GraphQL
    Hooks_Jenkins -->|POST| GitHubWebhooks
    Hooks_Python -->|POST| GitHubWebhooks
    Hooks_Ruby -->|POST| GitHubWebhooks
    PR_Hooks -->|invoke| GHEnterprise
    SQL_Audit -->|SQL| EnterpriseDB
    SQL_Metrics -->|SQL| EnterpriseDB
    SQL_Security -->|SQL| EnterpriseDB
    Scripts -->|CLI| GHEnterprise
    MSGraph -->|HTTP| AzureAD

    %% Click Events
    click CI_CodeQL "https://github.com/github/platform-samples/blob/master/.github/workflows/codeql.yml"
    click CI_Combine "https://github.com/github/platform-samples/blob/master/.github/workflows/combine-prs.yml"
    click API_Bash "https://github.com/github/platform-samples/tree/master/api/bash/"
    click API_Go "https://github.com/github/platform-samples/blob/master/api/golang/basics-of-authentication/server.go"
    click API_Groovy "https://github.com/github/platform-samples/tree/master/api/groovy/"
    click API_Java "https://github.com/github/platform-samples/blob/master/api/java/deployment/src/main/java/com/github/DeployServer.java"
    click API_JS "https://github.com/github/platform-samples/blob/master/api/javascript/es2015-nodejs/libs/GitHubClient.js"
    click API_PS "https://github.com/github/platform-samples/blob/master/api/powershell/invite_members_to_org.ps1"
    click API_Py "https://github.com/github/platform-samples/blob/master/api/python/building-a-ci-server/server.py"
    click API_Rb "https://github.com/github/platform-samples/blob/master/api/ruby/basics-of-authentication/server.rb"
    click API_Scala "https://github.com/github/platform-samples/blob/master/api/scala.with.sbt/octocat-samples/src/main/scala/github/Client.scala"
    click App_Ruby "https://github.com/github/platform-samples/blob/master/app/ruby/app-issue-creator/server.rb"
    click GraphQL "https://github.com/github/platform-samples/tree/master/graphql/bin/run-query"
    click Hooks_Jenkins "https://github.com/github/platform-samples/tree/master/hooks/jenkins/jira-issue-validator/Jenkinsfile"
    click Hooks_Python "https://github.com/github/platform-samples/blob/master/hooks/python/flask-github-webhooks/webhooks.py"
    click Hooks_Ruby "https://github.com/github/platform-samples/blob/master/hooks/ruby/delete-repository-event/app.rb"
    click PR_Hooks "https://github.com/github/platform-samples/blob/master/pre-receive-hooks/always_reject.sh"
    click Scripts "https://github.com/github/platform-samples/tree/master/scripts/"
    click SQL_Audit "https://github.com/github/platform-samples/tree/master/sql/audit/"
    click SQL_Metrics "https://github.com/github/platform-samples/tree/master/sql/metrics/"
    click SQL_Security "https://github.com/github/platform-samples/tree/master/sql/security/"
    click MSGraph "https://github.com/github/platform-samples/blob/master/microsoft-graph-api/EMU-OIDC-tokenlifetime-policy.md"

    %% Styles
    classDef ci fill:#ddd,stroke:#666,stroke-width:1px;
    classDef sample fill:#bbf,stroke:#333,stroke-width:1px;
    classDef external fill:#dfd,stroke:#090,stroke-width:1px;
    classDef doc fill:#fff,stroke:#999,stroke-dasharray:5 5,stroke-width:1px;
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