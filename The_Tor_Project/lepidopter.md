---
created: 2025-06-16 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/TheTorProject/lepidopter
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


# lepidopter repo project
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
title: "lepidopter repo project"
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
    %% Build Environment
    subgraph "Build Environment"
        direction TB
        SetupScript["setup.sh"]:::build
        VMDBDriver["lepidopter-vmdebootstrap_build.sh"]:::build
        VMDBEngine["vmdebootstrap engine"]:::build
        subgraph "Configuration Inputs"
            direction TB
            Conf1["lepidopter-image.conf"]:::config
            Conf2["tor-pt.conf"]:::config
        end
        subgraph "Package Lists"
            direction TB
            Pkg1["lepidopter-v1.0.0-armel-apt-packages"]:::config
            Pkg2["lepidopter-v1.0.0-armel-pip-packages"]:::config
        end
        Customize["customize"]:::build
        Cleanup["cleanup.sh"]:::build
        RootfsTemplateDir["lepidopter-fh/"]:::input
        ImageOutput["images/"]:::input
        SigningScript["lepidopter-sign.sh"]:::build
        ReleaseScript["release"]:::build

        SetupScript --> VMDBDriver
        VMDBDriver --> VMDBEngine
        VMDBEngine --> Conf1
        VMDBEngine --> Conf2
        VMDBEngine --> Pkg1
        VMDBEngine --> Pkg2
        VMDBEngine --> Customize
        VMDBEngine --> Cleanup
        VMDBEngine --> RootfsTemplateDir
        VMDBEngine --> ImageOutput
        ImageOutput --> SigningScript
        SigningScript --> ReleaseScript
    end

    %% Device Runtime
    subgraph "Device Runtime"
        direction TB
        BootConfig["config.txt"]:::config
        APTConfig["02compress-indexes"]:::config
        subgraph "Avahi Services"
            direction TB
            AvahiProbe["ooniprobe.service"]:::config
            AvahiSSH["ssh.service"]:::config
        end
        subgraph "Cron Jobs"
            direction TB
            CronDaily["remove_old_logs"]:::config
            CronTab["crontab"]:::config
        end
        subgraph "Systemd Units"
            direction TB
            SDProbe["ooniprobe.service"]:::runtime
            SDUpdate["lepidopter-update.service"]:::runtime
        end
        subgraph "Update Mechanism"
            direction TB
            Updater["updater.py"]:::runtime
            PublicKey["public.asc"]:::config
            Versions["versions/"]:::input
        end
        subgraph "Logrotate Configs"
            direction TB
            LRProbe["ooniprobe"]:::config
            LRUpdate["lepidopter-update"]:::config
        end
        subgraph "OONI Config"
            direction TB
            OONIConf["ooniprobe.conf"]:::config
            OONIScript["ooniconfig.sh"]:::config
        end
        WatchdogCfg["watchdog.conf"]:::config
        SSHRegen["regenerate_ssh_host_keys"]:::config
        UI["OONI Web UI (HTTP)"]:::runtime
        SSHD["sshd"]:::runtime
        AvahiDaemon["Avahi Daemon"]:::runtime
        Watchdog["watchdog"]:::runtime

        RootfsTemplateDir --> BootConfig
        RootfsTemplateDir --> APTConfig
        RootfsTemplateDir --> AvahiProbe
        RootfsTemplateDir --> AvahiSSH
        RootfsTemplateDir --> CronDaily
        RootfsTemplateDir --> CronTab
        RootfsTemplateDir --> SDProbe
        RootfsTemplateDir --> SDUpdate
        RootfsTemplateDir --> Updater
        RootfsTemplateDir --> PublicKey
        RootfsTemplateDir --> Versions
        RootfsTemplateDir --> LRProbe
        RootfsTemplateDir --> LRUpdate
        RootfsTemplateDir --> OONIConf
        RootfsTemplateDir --> OONIScript
        RootfsTemplateDir --> WatchdogCfg
        RootfsTemplateDir --> SSHRegen

        SDProbe --> UI
        SDUpdate --> Updater
        Updater -->|"fetch updates"| Internet
        CronDaily -->|"remove logs"| VarLog
        VarLog["/var/log"]:::runtime
        LogRotate["logrotate"]:::runtime
        CronTab --> LogRotate
        AvahiDaemon --> UI
        AvahiDaemon --> SSHD
        Watchdog -->|monitors| SDProbe
    end

    %% External
    Internet(("Internet")):::cloud
    User(("User")):::external

    Internet -->|"update server"| Updater
    User -->|HTTP| UI
    User -->|SSH| SSHD

    %% Click Events
    click SetupScript "https://github.com/thetorproject/lepidopter/blob/master/scripts/setup.sh"
    click VMDBDriver "https://github.com/thetorproject/lepidopter/blob/master/lepidopter-vmdebootstrap_build.sh"
    click Conf1 "https://github.com/thetorproject/lepidopter/blob/master/conf/lepidopter-image.conf"
    click Conf2 "https://github.com/thetorproject/lepidopter/blob/master/conf/tor-pt.conf"
    click Pkg1 "https://github.com/thetorproject/lepidopter/blob/master/pkglist/lepidopter-v1.0.0-armel-apt-packages"
    click Pkg2 "https://github.com/thetorproject/lepidopter/blob/master/pkglist/lepidopter-v1.0.0-armel-pip-packages"
    click Customize "https://github.com/thetorproject/lepidopter/tree/master/customize"
    click Cleanup "https://github.com/thetorproject/lepidopter/blob/master/lepidopter-fh/cleanup.sh"
    click RootfsTemplateDir "https://github.com/thetorproject/lepidopter/tree/master/lepidopter-fh/"
    click ImageOutput "https://github.com/thetorproject/lepidopter/tree/master/images/"
    click SigningScript "https://github.com/thetorproject/lepidopter/blob/master/scripts/lepidopter-sign.sh"
    click ReleaseScript "https://github.com/thetorproject/lepidopter/tree/master/scripts/release"
    click BootConfig "https://github.com/thetorproject/lepidopter/blob/master/lepidopter-fh/boot/config.txt"
    click APTConfig "https://github.com/thetorproject/lepidopter/tree/master/lepidopter-fh/etc/apt/apt.conf.d/02compress-indexes"
    click AvahiProbe "https://github.com/thetorproject/lepidopter/blob/master/lepidopter-fh/etc/avahi/services/ooniprobe.service"
    click AvahiSSH "https://github.com/thetorproject/lepidopter/blob/master/lepidopter-fh/etc/avahi/services/ssh.service"
    click CronDaily "https://github.com/thetorproject/lepidopter/tree/master/lepidopter-fh/etc/cron.daily/remove_old_logs"
    click CronTab "https://github.com/thetorproject/lepidopter/tree/master/lepidopter-fh/etc/crontab"
    click SDProbe "https://github.com/thetorproject/lepidopter/blob/master/lepidopter-fh/etc/systemd/system/ooniprobe.service"
    click SDUpdate "https://github.com/thetorproject/lepidopter/blob/master/lepidopter-fh/etc/systemd/system/lepidopter-update.service"
    click Updater "https://github.com/thetorproject/lepidopter/blob/master/lepidopter-fh/opt/ooni/lepidopter-update/updater.py"
    click PublicKey "https://github.com/thetorproject/lepidopter/blob/master/lepidopter-fh/opt/ooni/lepidopter-update/public.asc"
    click Versions "https://github.com/thetorproject/lepidopter/tree/master/lepidopter-fh/opt/ooni/lepidopter-update/versions/"
    click LRProbe "https://github.com/thetorproject/lepidopter/tree/master/lepidopter-fh/etc/logrotate.d/ooniprobe"
    click LRUpdate "https://github.com/thetorproject/lepidopter/tree/master/lepidopter-fh/etc/logrotate.d/lepidopter-update"
    click OONIConf "https://github.com/thetorproject/lepidopter/blob/master/lepidopter-fh/etc/ooniprobe.conf"
    click OONIScript "https://github.com/thetorproject/lepidopter/blob/master/lepidopter-fh/etc/ooniprobe/ooniconfig.sh"
    click WatchdogCfg "https://github.com/thetorproject/lepidopter/blob/master/lepidopter-fh/etc/watchdog.conf"
    click SSHRegen "https://github.com/thetorproject/lepidopter/tree/master/lepidopter-fh/etc/init.d/regenerate_ssh_host_keys"

    %% Styles
    classDef build fill:#bbdefb,stroke:#1e88e5;
    classDef input fill:#c8e6c9,stroke:#2e7d32;
    classDef runtime fill:#ffe0b2,stroke:#ef6c00;
    classDef config fill:#eeeeee,stroke:#757575;
    classDef cloud fill:#b3e5fc,stroke:#039be5;
    classDef external fill:#f3e5f5,stroke:#8e24aa;

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