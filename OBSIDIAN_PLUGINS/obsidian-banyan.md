---
created: 2025-07-01 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/ratiger/obsidian-banyan
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




# obsidian-banyan repo project by ratiger
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for 👨‍🎓 <ins>educational purposes</ins> 👨‍🎓 (<ins>:trollface:sometimes, entertainment purposes:trollface:</ins>), 📖 <ins> personal study </ins> 📖, and 🔖 <ins> technical reference </ins> 🔖.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>



---

```mermaid
---
title: "obsidian-banyan repo project by ratiger"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright © 2025 Cong Le. All Rights Reserved."
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
    subgraph "Obsidian Host"
        Host["Obsidian Host"]:::host
    end

    subgraph "Plugin Core"
        Main["main.ts"]:::core
        Plugin["BanyanPlugin.ts"]:::core
    end

    subgraph "Settings Subsystem"
        SettingsModel["BanyanPluginSettings.ts"]:::settings
        SettingsUI["BanyanSettingTab.tsx"]:::settings
    end

    subgraph "State Management Store"
        StoreIndex["index.ts"]:::store
        DashStore["useDashBoardStore.ts"]:::store
        FilterStore["useFilterSchemeStore.ts"]:::store
        RandomStore["useRandomReviewStore.ts"]:::store
        ViewStore["useViewSchemeStore.ts"]:::store
        SettingsStore["useSettingsStore.ts"]:::store
    end

    subgraph "UI Layer - Pages"
        CardDashboard["CardDashboard.tsx"]:::ui
        FilterView["FilterView.tsx"]:::ui
        RandomReview["RandomReviewInfo.tsx"]:::ui
        Heatmap["Heatmap.tsx"]:::ui
        AddNote["AddNoteView.tsx"]:::ui
        SearchView["SearchView.tsx"]:::ui
    end

    subgraph "UI Layer - Components"
        ConfirmModal["ConfirmModal.tsx"]:::ui
        TagInput["TagInput.tsx"]:::ui
        FolderSuggest["FolderSuggest.ts"]:::ui
        Icon["Icon.tsx"]:::ui
    end

    subgraph "Models"
        FileInfo["FileInfo.ts"]:::model
        FilterScheme["FilterScheme.ts"]:::model
        ViewScheme["ViewScheme.ts"]:::model
        TagFilter["TagFilter.ts"]:::model
        DateRange["DateRange.ts"]:::model
        RandomFilters["RandomReviewFilters.ts"]:::model
    end

    subgraph "Utilities"
        FileUtils["fileUtils.ts"]:::util
        FileWatcher["fileWatcher.ts"]:::util
        I18n["i18n/index.ts"]:::util
    end

    Vault["Vault File System"]:::fs

    %% Connections
    Host -->|"plugin load"| Main
    Host -->|"API calls"| Plugin
    Main -->|"instantiates"| Plugin
    Plugin -->|"uses settings model"| SettingsModel
    Plugin -->|"mounts settings UI"| SettingsUI
    Plugin -->|"initializes store"| StoreIndex
    StoreIndex --> DashStore
    StoreIndex --> FilterStore
    StoreIndex --> RandomStore
    StoreIndex --> ViewStore
    StoreIndex --> SettingsStore

    %% Store to UI pages
    DashStore -->|"state"| CardDashboard
    FilterStore -->|"state"| FilterView
    RandomStore -->|"state"| RandomReview
    ViewStore -->|"state"| Heatmap
    SettingsStore -->|"state"| SettingsUI

    %% Settings interactions
    SettingsUI -->|"saves"| SettingsModel
    SettingsModel -->|"persists"| SettingsStore

    %% UI pages to components
    CardDashboard --> ConfirmModal
    CardDashboard --> TagInput
    CardDashboard --> FolderSuggest
    CardDashboard --> Icon
    FilterView --> TagInput
    RandomReview --> Icon
    Heatmap --> Icon
    AddNote --> FileUtils
    SearchView --> TagInput

    %% Utilities and watchers
    FileWatcher -->|"onFileChange"| StoreIndex
    FileWatcher --> Vault
    FileUtils --> Vault
    I18n --> CardDashboard
    I18n --> FilterView
    I18n --> ConfirmModal

    %% User flows
    AddNote -->|"create note"| FileUtils
    FileUtils -->|"writeFile"| Vault
    FilterView -->|"apply filter"| FilterStore
    CardDashboard -->|"render cards"| CardDashboard

    %% Styles
    classDef host fill:#cccccc,stroke:#333,stroke-width:1px;
    classDef core fill:#add8e6,stroke:#333,stroke-width:1px;
    classDef settings fill:#d8bfd8,stroke:#333,stroke-width:1px;
    classDef store fill:#98fb98,stroke:#333,stroke-width:1px;
    classDef ui fill:#ffffe0,stroke:#333,stroke-width:1px;
    classDef model fill:#ffa500,stroke:#333,stroke-width:1px;
    classDef util fill:#ffdead,stroke:#333,stroke-width:1px;
    classDef fs fill:#c0c0c0,stroke:#333,stroke-width:1px;

    %% Click Events
    click Main "https://github.com/ratiger/obsidian-banyan/blob/main/src/main.ts"
    click Plugin "https://github.com/ratiger/obsidian-banyan/blob/main/src/BanyanPlugin.ts"
    click SettingsModel "https://github.com/ratiger/obsidian-banyan/blob/main/src/BanyanPluginSettings.ts"
    click SettingsUI "https://github.com/ratiger/obsidian-banyan/blob/main/src/BanyanSettingTab.tsx"
    click StoreIndex "https://github.com/ratiger/obsidian-banyan/blob/main/src/store/index.ts"
    click DashStore "https://github.com/ratiger/obsidian-banyan/blob/main/src/store/useDashBoardStore.ts"
    click FilterStore "https://github.com/ratiger/obsidian-banyan/blob/main/src/store/useFilterSchemeStore.ts"
    click RandomStore "https://github.com/ratiger/obsidian-banyan/blob/main/src/store/useRandomReviewStore.ts"
    click ViewStore "https://github.com/ratiger/obsidian-banyan/blob/main/src/store/useViewSchemeStore.ts"
    click SettingsStore "https://github.com/ratiger/obsidian-banyan/blob/main/src/store/useSettingsStore.ts"
    click CardDashboard "https://github.com/ratiger/obsidian-banyan/blob/main/src/pages/CardDashboard.tsx"
    click FilterView "https://github.com/ratiger/obsidian-banyan/blob/main/src/pages/sidebar/filterScheme/FilterView.tsx"
    click RandomReview "https://github.com/ratiger/obsidian-banyan/blob/main/src/pages/sidebar/randomReview/RandomReviewInfo.tsx"
    click Heatmap "https://github.com/ratiger/obsidian-banyan/blob/main/src/pages/sidebar/heatmap/Heatmap.tsx"
    click AddNote "https://github.com/ratiger/obsidian-banyan/blob/main/src/pages/header/AddNoteView.tsx"
    click SearchView "https://github.com/ratiger/obsidian-banyan/blob/main/src/pages/header/searchbar/SearchView.tsx"
    click ConfirmModal "https://github.com/ratiger/obsidian-banyan/blob/main/src/components/ConfirmModal.tsx"
    click TagInput "https://github.com/ratiger/obsidian-banyan/blob/main/src/components/TagInput.tsx"
    click FolderSuggest "https://github.com/ratiger/obsidian-banyan/blob/main/src/components/FolderSuggest.ts"
    click Icon "https://github.com/ratiger/obsidian-banyan/blob/main/src/components/Icon.tsx"
    click FileInfo "https://github.com/ratiger/obsidian-banyan/blob/main/src/models/FileInfo.ts"
    click FilterScheme "https://github.com/ratiger/obsidian-banyan/blob/main/src/models/FilterScheme.ts"
    click ViewScheme "https://github.com/ratiger/obsidian-banyan/blob/main/src/models/ViewScheme.ts"
    click TagFilter "https://github.com/ratiger/obsidian-banyan/blob/main/src/models/TagFilter.ts"
    click DateRange "https://github.com/ratiger/obsidian-banyan/blob/main/src/models/DateRange.ts"
    click RandomFilters "https://github.com/ratiger/obsidian-banyan/blob/main/src/models/RandomReviewFilters.ts"
    click FileUtils "https://github.com/ratiger/obsidian-banyan/blob/main/src/utils/fileUtils.ts"
    click FileWatcher "https://github.com/ratiger/obsidian-banyan/blob/main/src/utils/fileWatcher.ts"
    click I18n "https://github.com/ratiger/obsidian-banyan/blob/main/src/utils/i18n/index.ts"

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