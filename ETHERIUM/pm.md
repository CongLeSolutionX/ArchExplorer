---
created: 2025-06-15 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ethereum/pm
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExanZydm52NDcyNWIwMWtneG9uOWk4aGpseXQ1bHR4b3c1N2x3MnB6bSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/m3XqQ8QhuIUuQau7n5/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# pm repo project
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
title: "pm repo project"
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
    subgraph "Orchestration Layer"
        GHWF["GitHub Actions<br/>(Workflows)"]:::orchestration
    end

    subgraph "Application Layer"
        subgraph "Configuration"
            Pyproj["pyproject.toml"]:::config
            Req["requirements.txt"]:::config
            Mapping["meeting_topic_mapping.json"]:::config
        end
        CLI["ACDbot CLI (cli.py)"]:::app

        subgraph "Plugin Layer"
            GCal["GCal Module"]:::plugin
            ZoomM["Zoom Module"]:::plugin
            YT["YouTube Utils"]:::plugin
            Trans["Transcript Module"]:::plugin
            RSSMod["RSS Utils"]:::plugin
            DiscordM["Discord Notify"]:::plugin
            TG["Telegram Module"]:::plugin
            EmailM["Email Utils"]:::plugin
            Farc["Farcaster Module"]:::plugin
            Disc["Discourse Module"]:::plugin
        end

        subgraph "Scripts"
            SN["discord_notify.py"]:::script
            PZ["poll_zoom_recordings.py"]:::script
            UZ["upload_zoom_recording.py"]:::script
            SE["send_recording_email.py"]:::script
            SR["serve_rss.py"]:::script
            HI["handle_issue.py"]:::script
            GRT["get_refresh_token.py"]:::script
            GZT["get_zoom_token.py"]:::script
            RYT["refresh_youtube_token.py"]:::script
        end
    end

    subgraph "Data Layer"
        Markdown[(Meeting Archives)]:::data
        Processes[(processes/ docs)]:::data
        README["README.md"]:::data
    end

    subgraph "External Services"
        GC["Google Calendar API"]:::external
        Zm["Zoom API"]:::external
        YTapi["YouTube API"]:::external
        DiscWS["Discord Webhook"]:::external
        TgWS["Telegram"]:::external
        EmailS["Email SMTP"]:::external
        FarcWS["Farcaster"]:::external
        DiscService["Discourse"]:::external
        RSSfeed["RSS Consumers"]:::external
    end

    %% Connections
    GHWF -->|"triggers"| CLI
    CLI -->|"loads config"| Pyproj
    CLI -->|"loads config"| Req
    CLI -->|"loads config"| Mapping

    CLI -->|"calls"| GCal
    CLI -->|"calls"| ZoomM
    CLI -->|"calls"| YT
    CLI -->|"calls"| Trans
    CLI -->|"calls"| RSSMod
    CLI -->|"calls"| DiscordM
    CLI -->|"calls"| TG
    CLI -->|"calls"| EmailM
    CLI -->|"calls"| Farc
    CLI -->|"calls"| Disc

    CLI -->|"runs script"| SN
    CLI -->|"runs script"| PZ
    CLI -->|"runs script"| UZ
    CLI -->|"runs script"| SE
    CLI -->|"runs script"| SR
    CLI -->|"runs script"| HI
    CLI -->|"runs script"| GRT
    CLI -->|"runs script"| GZT
    CLI -->|"runs script"| RYT

    GCal -->|"fetches events"| GC
    ZoomM -->|"polls recordings"| Zm
    YT -->|"uploads/refreshes"| YTapi
    Trans -->|"processes transcripts"| Zm
    Trans -->|"processes transcripts"| GC
    RSSMod -->|"reads markdown"| Markdown
    RSSMod -->|"generates feed"| RSSfeed

    GCal -->|"writes metadata"| Markdown
    ZoomM -->|"writes transcripts"| Markdown
    YT -->|"writes recordings"| Markdown
    Trans -->|"writes cleaned text"| Markdown
    CLI -->|"commits & pushes"| Markdown

    DiscordM -->|"posts message"| DiscWS
    TG -->|"sends message"| TgWS
    EmailM -->|"sends email"| EmailS
    Farc -->|"posts update"| FarcWS
    Disc -->|"creates post"| DiscService

    %% Click Events
    click GHWF "https://github.com/ethereum/pm/tree/master/.github/workflows/"
    click CLI "https://github.com/ethereum/pm/blob/master/.github/ACDbot/cli.py"
    click Pyproj "https://github.com/ethereum/pm/blob/master/.github/ACDbot/pyproject.toml"
    click Req "https://github.com/ethereum/pm/blob/master/.github/ACDbot/requirements.txt"
    click Mapping "https://github.com/ethereum/pm/blob/master/.github/ACDbot/meeting_topic_mapping.json"
    click GCal "https://github.com/ethereum/pm/blob/master/.github/ACDbot/modules/gcal.py"
    click ZoomM "https://github.com/ethereum/pm/blob/master/.github/ACDbot/modules/zoom.py"
    click YT "https://github.com/ethereum/pm/blob/master/.github/ACDbot/modules/youtube_utils.py"
    click Trans "https://github.com/ethereum/pm/blob/master/.github/ACDbot/modules/transcript.py"
    click RSSMod "https://github.com/ethereum/pm/blob/master/.github/ACDbot/modules/rss_utils.py"
    click DiscordM "https://github.com/ethereum/pm/blob/master/.github/ACDbot/modules/discord_notify.py"
    click TG "https://github.com/ethereum/pm/blob/master/.github/ACDbot/modules/tg.py"
    click EmailM "https://github.com/ethereum/pm/blob/master/.github/ACDbot/modules/email_utils.py"
    click Farc "https://github.com/ethereum/pm/blob/master/.github/ACDbot/modules/farcaster.py"
    click Disc "https://github.com/ethereum/pm/blob/master/.github/ACDbot/modules/discourse.py"
    click SN "https://github.com/ethereum/pm/blob/master/.github/ACDbot/scripts/discord_notify.py"
    click PZ "https://github.com/ethereum/pm/blob/master/.github/ACDbot/scripts/poll_zoom_recordings.py"
    click UZ "https://github.com/ethereum/pm/blob/master/.github/ACDbot/scripts/upload_zoom_recording.py"
    click SE "https://github.com/ethereum/pm/blob/master/.github/ACDbot/scripts/send_recording_email.py"
    click SR "https://github.com/ethereum/pm/blob/master/.github/ACDbot/scripts/serve_rss.py"
    click HI "https://github.com/ethereum/pm/blob/master/.github/ACDbot/scripts/handle_issue.py"
    click GRT "https://github.com/ethereum/pm/blob/master/.github/ACDbot/scripts/get_refresh_token.py"
    click GZT "https://github.com/ethereum/pm/blob/master/.github/ACDbot/scripts/get_zoom_token.py"
    click RYT "https://github.com/ethereum/pm/blob/master/.github/ACDbot/scripts/refresh_youtube_token.py"
    click README "https://github.com/ethereum/pm/blob/master/README.md"
    click Processes "https://github.com/ethereum/pm/tree/master/processes/"

    %% Styles
    classDef orchestration fill:#D6E9F8,stroke:#4A90E2
    classDef app fill:#E8F5E9,stroke:#2E7D32
    classDef plugin fill:#C8E6C9,stroke:#388E3C
    classDef script fill:#DCEDC8,stroke:#558B2F
    classDef config fill:#FFF9C4,stroke:#FBC02D
    classDef data fill:#D7CCC8,stroke:#6D4C41
    classDef external fill:#ECEFF1,stroke:#90A4AE
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