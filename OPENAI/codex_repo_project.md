---
created: 2025-06-012 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/openai/codex
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExMm1wY3UwbTcxZ3Y1ajJ6enBkM3g1bXRrOHZlaWdlYmd2eWJqdDFwcCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/THZv19DxEFx1sDexIH/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----


# codex repo project
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
title: "codex repo project"
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
    %% UI / CLI Layer
    subgraph "UI / CLI Layer"
        direction TB
        CLIFrontend["CLI Frontend"]:::ui
        CmdParser["Command Parser &\nFlag Handling"]:::ui
        UIComponents["React-style UI\nComponents"]:::ui
        ConfigMgr["Config Manager &\nEnvironment Loader"]:::ui
    end

    %% Core Logic Layer
    subgraph "Core Logic Layer"
        direction TB
        AgentCore["Agent Core\n(Loop, Prompt, API)"]:::core
        DiffParser["Diff Parser &\nPatch Applier"]:::core
    end

    %% Sandbox & Execution Layer
    subgraph "Sandbox & Execution Layer"
        direction TB
        MacSandbox["macOS Seatbelt Sandbox"]:::sandbox
        LinuxSandbox["Docker + Firewall Sandbox"]:::sandbox
        RustExecPolicy["Rust ExecPolicy Engine"]:::sandbox
    end

    %% Rust Libraries & Binaries
    subgraph "Rust Binaries & Libraries"
        direction TB
        RustCore["core AI Client & State"]:::core
        RustCLI["CLI Entrypoint & Sandbox Integration"]:::core
        RustApplyPatch["apply-patch Library"]:::core
        RustANSIEsc["ANSI-Escape Library"]:::core
        RustExec["Execution Wrapper"]:::core
        MCPProtocol["MCP Tool-Call Protocol"]:::core
        TUIFallback["Terminal UI Fallback (TUI)"]:::core
    end

    %% External Services & Resources
    subgraph "External Services & Resources"
        direction TB
        OpenAIAPI["OpenAI Chat Completions API"]:::external
        GitRepo["Git Repository"]:::external
        FileSystem["Local File System\n& Temp Storage"]:::external
    end

    %% Connections
    CLIFrontend -->|"user issues codex"| CmdParser
    CmdParser -->|"parses flags"| ConfigMgr
    ConfigMgr -->|"loads config & AGENTS.md"| AgentCore
    UIComponents -->|"renders interactive UI"| AgentCore

    AgentCore -->|"HTTP JSON"| OpenAIAPI
    OpenAIAPI -->|"JSON response"| AgentCore

    AgentCore -->|"diff patch data"| DiffParser
    DiffParser -->|"shell commands"| MacSandbox
    DiffParser -->|"shell commands"| LinuxSandbox

    MacSandbox -->|"exec commands"| RustExecPolicy
    LinuxSandbox -->|"exec commands"| RustExecPolicy

    RustExecPolicy -->|"sandbox policies"| RustExec
    RustExec -->|"invoke"| RustCLI

    AgentCore -->|"IPC calls"| MCPProtocol
    MCPProtocol -->|"calls"| RustCore

    RustCore -->|"apply diff"| RustApplyPatch
    RustCore -->|"format styling"| RustANSIEsc
    RustCore -->|"fallback UI"| TUIFallback

    DiffParser -->|"writes files"| FileSystem
    FileSystem -->|"git staging"| GitRepo

    %% Click Events
    click CLIFrontend "https://github.com/openai/codex/tree/main/codex-cli/src"
    click CmdParser "https://github.com/openai/codex/blob/main/codex-cli/src/cli.tsx"
    click UIComponents "https://github.com/openai/codex/tree/main/codex-cli/src/components"
    click ConfigMgr "https://github.com/openai/codex/blob/main/codex-cli/src/utils/config.ts"
    click ConfigMgr "https://github.com/openai/codex/blob/main/codex-cli/src/utils/session.ts"
    click AgentCore "https://github.com/openai/codex/blob/main/codex-cli/src/utils/agent/agent-loop.ts"
    click AgentCore "https://github.com/openai/codex/blob/main/codex-cli/src/utils/agent/apply-patch.ts"
    click AgentCore "https://github.com/openai/codex/blob/main/codex-cli/src/utils/agent/parse-apply-patch.ts"
    click AgentCore "https://github.com/openai/codex/blob/main/codex-cli/src/utils/agent/exec.ts"
    click AgentCore "https://github.com/openai/codex/blob/main/codex-cli/src/utils/openai-client.ts"
    click DiffParser "https://github.com/openai/codex/blob/main/codex-cli/src/parse-apply-patch.ts"
    click DiffParser "https://github.com/openai/codex/blob/main/codex-cli/src/utils/agent/parse-apply-patch.ts"
    click MacSandbox "https://github.com/openai/codex/blob/main/codex-cli/src/utils/agent/sandbox/macos-seatbelt.ts"
    click LinuxSandbox "https://github.com/openai/codex/blob/main/codex-cli/scripts/run_in_container.sh"
    click RustExecPolicy "https://github.com/openai/codex/tree/main/codex-rs/execpolicy"
    click RustCore "https://github.com/openai/codex/tree/main/codex-rs/core"
    click RustCLI "https://github.com/openai/codex/tree/main/codex-rs/cli"
    click RustApplyPatch "https://github.com/openai/codex/tree/main/codex-rs/apply-patch"
    click RustANSIEsc "https://github.com/openai/codex/tree/main/codex-rs/ansi-escape"
    click RustExec "https://github.com/openai/codex/tree/main/codex-rs/exec"
    click MCPProtocol "https://github.com/openai/codex/tree/main/codex-rs/mcp-client"
    click MCPProtocol "https://github.com/openai/codex/tree/main/codex-rs/mcp-server"
    click MCPProtocol "https://github.com/openai/codex/tree/main/codex-rs/mcp-types"
    click TUIFallback "https://github.com/openai/codex/tree/main/codex-rs/tui"
    click GitRepo "https://github.com/openai/codex/tree/main/.github/workflows"
    click GitRepo "https://github.com/openai/codex/blob/main/pnpm-workspace.yaml"
    click GitRepo "https://github.com/openai/codex/blob/main/flake.nix"
    click GitRepo "https://github.com/openai/codex/blob/main/AGENTS.md"
    click GitRepo "https://github.com/openai/codex/blob/main/README.md"

    %% Styles
    classDef ui fill:#D0E8FF,stroke:#0366d6,stroke-width:1px
    classDef core fill:#D5F5D5,stroke:#1e6823,stroke-width:1px
    classDef sandbox fill:#FFE5B4,stroke:#d9730d,stroke-width:1px
    classDef external fill:#EEEEEE,stroke:#555555,stroke-width:1px
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
