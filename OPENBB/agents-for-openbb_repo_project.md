---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/OpenBB-finance/agents-for-openbb
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




# agents-for-openbb repo project
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
title: "agents-for-openbb repo project"
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
    %% External Systems
    OW["OpenBB Workspace"]:::external
    SDK["OpenBB AI SDK"]:::sdk

    %% Agent Modules Group
    subgraph "Agent Modules" 
        direction TB
        RAW["Raw Widget Data Agent"]:::agent
        REASON["Reasoning Steps Agent"]:::agent
        CITATIONS["Raw Widget Data with Citations Agent"]:::agent
        CHARTS["Charts Agent"]:::agent
        TABLES["Tables Agent"]:::agent
        PDF["PDF Handling Agent"]:::agent
        subgraph "Advanced Example"
            direction TB
            ADV_AGENT["Advanced Portfolio Commentary Agent"]:::agent
            ADV_FUNCS["Business Logic (functions.py)"]:::agent
            ADV_PROMPTS["Prompt Definitions (prompts.py)"]:::agent
        end
    end

    %% Test Harness
    subgraph "Test Harness" 
        direction TB
        PAYLOADS["JSON Payloads"]:::test
        RAW_TEST["Raw Agent Tests"]:::test
        REASON_TEST["Reasoning Steps Agent Tests"]:::test
        CIT_TEST["Citations Agent Tests"]:::test
        CHARTS_TEST["Charts Agent Tests"]:::test
        TABLES_TEST["Tables Agent Tests"]:::test
        PDF_TEST["PDF Agent Tests"]:::test
    end

    %% CI/CD
    subgraph "CI/CD (GitHub Actions)" 
        direction TB
        LINT["Lint Workflow"]:::ci
        TEST_WORKFLOW["Test Workflow"]:::ci
    end

    %% Data Flow Arrows
    OW -->|"sends JSON message"| RAW
    OW -->|"sends JSON message"| REASON
    OW -->|"sends JSON message"| CITATIONS
    OW -->|"sends JSON message"| CHARTS
    OW -->|"sends JSON message"| TABLES
    OW -->|"sends JSON message"| PDF
    OW -->|"sends JSON message"| ADV_AGENT

    RAW -->|"calls SDK"| SDK
    REASON -->|"calls SDK"| SDK
    CITATIONS -->|"calls SDK"| SDK
    CHARTS -->|"calls SDK"| SDK
    TABLES -->|"calls SDK"| SDK
    PDF -->|"calls SDK"| SDK
    ADV_AGENT -->|"calls SDK"| SDK

    SDK -->|"returns data"| RAW
    SDK -->|"returns data"| REASON
    SDK -->|"returns data"| CITATIONS
    SDK -->|"returns data"| CHARTS
    SDK -->|"returns data"| TABLES
    SDK -->|"returns data"| PDF
    SDK -->|"returns data"| ADV_AGENT

    RAW -->|"returns response"| OW
    REASON -->|"returns response"| OW
    CITATIONS -->|"returns response"| OW
    CHARTS -->|"returns response"| OW
    TABLES -->|"returns response"| OW
    PDF -->|"returns response"| OW
    ADV_AGENT -->|"returns response"| OW

    %% CI/CD flows
    LINT -->|"lints code"| RAW
    LINT -->|"lints code"| REASON
    LINT -->|"lints code"| CITATIONS
    LINT -->|"lints code"| CHARTS
    LINT -->|"lints code"| TABLES
    LINT -->|"lints code"| PDF
    LINT -->|"lints code"| ADV_AGENT

    TEST_WORKFLOW -->|"runs tests"| RAW_TEST
    TEST_WORKFLOW -->|"runs tests"| REASON_TEST
    TEST_WORKFLOW -->|"runs tests"| CIT_TEST
    TEST_WORKFLOW -->|"runs tests"| CHARTS_TEST
    TEST_WORKFLOW -->|"runs tests"| TABLES_TEST
    TEST_WORKFLOW -->|"runs tests"| PDF_TEST

    RAW_TEST -->|"uses payloads"| PAYLOADS
    REASON_TEST -->|"uses payloads"| PAYLOADS
    CIT_TEST -->|"uses payloads"| PAYLOADS
    CHARTS_TEST -->|"uses payloads"| PAYLOADS
    TABLES_TEST -->|"uses payloads"| PAYLOADS
    PDF_TEST -->|"uses payloads"| PAYLOADS

    %% Click Events
    click RAW "https://github.com/openbb-finance/agents-for-openbb/blob/main/30-vanilla-agent-raw-widget-data/vanilla_agent_raw_context/main.py"
    click REASON "https://github.com/openbb-finance/agents-for-openbb/blob/main/31-vanilla-agent-reasoning-steps/vanilla_agent_reasoning_steps/main.py"
    click CITATIONS "https://github.com/openbb-finance/agents-for-openbb/blob/main/32-vanilla-agent-raw-widget-data-citations/vanilla_agent_raw_context_citations/main.py"
    click CHARTS "https://github.com/openbb-finance/agents-for-openbb/blob/main/33-vanilla-agent-charts/vanilla_agent_charts/main.py"
    click TABLES "https://github.com/openbb-finance/agents-for-openbb/blob/main/34-vanilla-agent-tables/vanilla_agent_tables/main.py"
    click PDF "https://github.com/openbb-finance/agents-for-openbb/blob/main/35-vanilla-agent-pdf/vanilla_agent_pdf/main.py"
    click ADV_AGENT "https://github.com/openbb-finance/agents-for-openbb/blob/main/99-advanced-examples/70-portfolio-commentary/portfolio_commentary/main.py"
    click ADV_FUNCS "https://github.com/openbb-finance/agents-for-openbb/blob/main/99-advanced-examples/70-portfolio-commentary/portfolio_commentary/functions.py"
    click ADV_PROMPTS "https://github.com/openbb-finance/agents-for-openbb/blob/main/99-advanced-examples/70-portfolio-commentary/portfolio_commentary/prompts.py"
    click PAYLOADS "https://github.com/openbb-finance/agents-for-openbb/tree/main/testing/test_payloads/"
    click RAW_TEST "https://github.com/openbb-finance/agents-for-openbb/blob/main/30-vanilla-agent-raw-widget-data/tests/test_agent.py"
    click REASON_TEST "https://github.com/openbb-finance/agents-for-openbb/blob/main/31-vanilla-agent-reasoning-steps/tests/test_agent.py"
    click CIT_TEST "https://github.com/openbb-finance/agents-for-openbb/blob/main/32-vanilla-agent-raw-widget-data-citations/tests/test_agent.py"
    click CHARTS_TEST "https://github.com/openbb-finance/agents-for-openbb/blob/main/33-vanilla-agent-charts/tests/test_agent.py"
    click TABLES_TEST "https://github.com/openbb-finance/agents-for-openbb/blob/main/34-vanilla-agent-tables/tests/test_agent.py"
    click PDF_TEST "https://github.com/openbb-finance/agents-for-openbb/blob/main/35-vanilla-agent-pdf/tests/test_agent.py"
    click LINT "https://github.com/openbb-finance/agents-for-openbb/blob/main/.github/workflows/lint.yml"
    click TEST_WORKFLOW "https://github.com/openbb-finance/agents-for-openbb/blob/main/.github/workflows/test.yml"
    click SDK "https://github.com/openbb-finance/agents-for-openbb/blob/main/pyproject.toml"

    %% Styles
    classDef external fill:#ffd27f,stroke:#b8860b,color:#000;
    classDef sdk fill:#c2f0c2,stroke:#2e8b57,color:#000;
    classDef agent fill:#add8e6,stroke:#1e90ff,color:#000;
    classDef test fill:#f4cccc,stroke:#cc0000,color:#000;
    classDef ci fill:#d9d2e9,stroke:#6a5acd,color:#000;
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