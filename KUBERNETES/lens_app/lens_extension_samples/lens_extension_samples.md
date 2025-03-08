---
created: 2025-03-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# Lens App - Lens Extension Samples
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## A Diagrammatic Guide 


```mermaid
---
title: "Lens App - Lens Extension Samples"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "flowchart": {"htmlLabels": true, 'curve': 'natural'},
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#f231',
      'primaryTextColor': '#239',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
flowchart LR
    L["Lens Application Environment"]:::lens

    subgraph Hello_World_Sample["Hello World Sample"]
    style Hello_World_Sample fill:#cf31,stroke:#333,stroke-width:2px
        H1["Entry: renderer.tsx"]:::entry
        H2["UI: example-page.tsx"]:::ui
        subgraph Build_Configuration["Build/Configuration"]
        style Build_Configuration fill:#cf52,stroke:#333,stroke-width:2px
            H3["package.json"]:::config
            H4["tsconfig.json"]:::config
            H5["webpack.config.js"]:::config
            H6["Makefile"]:::config
        end
        H3 --> H1
        H4 --> H1
        H5 --> H1
        H6 --> H1
        H1 --> H2
        H1 -->|"integrateswith"| L
    end

    subgraph Custom_Resource_Page_Sample["Custom Resource Page Sample"]
    style Custom_Resource_Page_Sample fill:#2252,stroke:#333,stroke-width:2px
        CR1["Entry: renderer.tsx"]:::entry
        subgraph Business_Logic["Business Logic"]
        style Business_Logic fill:#cf52,stroke:#333,stroke-width:2px
            CR2["certificate-store.ts"]:::logic
            CR3["certificate.ts"]:::logic
        end
        subgraph UI_Components["UI Components"]
            CR4["certificate-details.tsx"]:::ui
            CR5["certificate-page.tsx"]:::ui
        end
        subgraph Build_Configuration["Build/Configuration"]
            CR6["package.json"]:::config
            CR7["tsconfig.json"]:::config
            CR8["webpack.config.js"]:::config
            CR9["Makefile"]:::config
        end
        CR6 --> CR1
        CR7 --> CR1
        CR8 --> CR1
        CR9 --> CR1
        CR1 --> CR2
        CR1 --> CR3
        CR2 --> CR4
        CR2 --> CR5
        CR3 --> CR4
        CR3 --> CR5
        CR1 -->|"integrateswith"| L
    end

    subgraph Styling_with_CSS_Modules_Sample["Styling with CSS Modules Sample"]
        CSS1["Entry: renderer.tsx"]:::entry
        CSS2["UI: page.tsx"]:::ui
        subgraph Styling_Subsystem["Styling Subsystem"]
            CSS3["styles.module.scss"]:::styling
            CSS4["styles.d.ts"]:::styling
        end
        subgraph Build_Configuration["Build/Configuration"]
            CSS5["package.json"]:::config
            CSS6["tsconfig.json"]:::config
            CSS7["webpack.config.js"]:::config
            CSS8["Makefile"]:::config
        end
        CSS5 --> CSS1
        CSS6 --> CSS1
        CSS7 --> CSS1
        CSS8 --> CSS1
        CSS1 --> CSS2
        CSS3 --> CSS2
        CSS4 --> CSS2
        CSS1 -->|"integrateswith"| L
    end

    subgraph Styling_with_Emotion_Sample["Styling with Emotion Sample"]
        E1["Entry: renderer.tsx"]:::entry
        E2["UI: page.tsx"]:::ui
        subgraph Build_Configuration["Build/Configuration"]
            E3["package.json"]:::config
            E4["tsconfig.json"]:::config
            E5["webpack.config.js"]:::config
            E6["Makefile"]:::config
        end
        E3 --> E1
        E4 --> E1
        E5 --> E1
        E6 --> E1
        E1 --> E2
        E1 -->|"integrateswith"| L
    end

    subgraph Styling_with_SASS_Sample["Styling with SASS Sample"]
        S1["Entry: renderer.tsx"]:::entry
        S2["UI: page.tsx"]:::ui
        S3["styles.scss"]:::styling
        subgraph Build_Configuration["Build/Configuration"]
            S4["package.json"]:::config
            S5["tsconfig.json"]:::config
            S6["webpack.config.js"]:::config
            S7["Makefile"]:::config
        end
        S4 --> S1
        S5 --> S1
        S6 --> S1
        S7 --> S1
        S1 --> S2
        S3 --> S2
        S1 -->|"integrateswith"| L
    end

    %% Click Events for Hello World Sample
    click H1 "https://github.com/lensapp/lens-extension-samples/blob/master/helloworld-sample/renderer.tsx"
    click H2 "https://github.com/lensapp/lens-extension-samples/blob/master/helloworld-sample/src/example-page.tsx"
    click H3 "https://github.com/lensapp/lens-extension-samples/blob/master/helloworld-sample/package.json"
    click H4 "https://github.com/lensapp/lens-extension-samples/blob/master/helloworld-sample/tsconfig.json"
    click H5 "https://github.com/lensapp/lens-extension-samples/blob/master/helloworld-sample/webpack.config.js"
    click H6 "https://github.com/lensapp/lens-extension-samples/tree/master/helloworld-sample/Makefile"

    %% Click Events for Custom Resource Page Sample
    click CR1 "https://github.com/lensapp/lens-extension-samples/blob/master/custom-resource-page/renderer.tsx"
    click CR2 "https://github.com/lensapp/lens-extension-samples/blob/master/custom-resource-page/src/certificate-store.ts"
    click CR3 "https://github.com/lensapp/lens-extension-samples/blob/master/custom-resource-page/src/certificate.ts"
    click CR4 "https://github.com/lensapp/lens-extension-samples/blob/master/custom-resource-page/src/components/certificate-details.tsx"
    click CR5 "https://github.com/lensapp/lens-extension-samples/blob/master/custom-resource-page/src/components/certificate-page.tsx"
    click CR6 "https://github.com/lensapp/lens-extension-samples/blob/master/custom-resource-page/package.json"
    click CR7 "https://github.com/lensapp/lens-extension-samples/blob/master/custom-resource-page/tsconfig.json"
    click CR8 "https://github.com/lensapp/lens-extension-samples/blob/master/custom-resource-page/webpack.config.js"
    click CR9 "https://github.com/lensapp/lens-extension-samples/tree/master/custom-resource-page/Makefile"

    %% Click Events for Styling with CSS Modules Sample
    click CSS1 "https://github.com/lensapp/lens-extension-samples/blob/master/styling-css-modules-sample/renderer.tsx"
    click CSS2 "https://github.com/lensapp/lens-extension-samples/blob/master/styling-css-modules-sample/page.tsx"
    click CSS3 "https://github.com/lensapp/lens-extension-samples/blob/master/styling-css-modules-sample/styles.module.scss"
    click CSS4 "https://github.com/lensapp/lens-extension-samples/blob/master/styling-css-modules-sample/styles.d.ts"
    click CSS5 "https://github.com/lensapp/lens-extension-samples/blob/master/styling-css-modules-sample/package.json"
    click CSS6 "https://github.com/lensapp/lens-extension-samples/blob/master/styling-css-modules-sample/tsconfig.json"
    click CSS7 "https://github.com/lensapp/lens-extension-samples/blob/master/styling-css-modules-sample/webpack.config.js"
    click CSS8 "https://github.com/lensapp/lens-extension-samples/tree/master/styling-css-modules-sample/Makefile"

    %% Click Events for Styling with Emotion Sample
    click E1 "https://github.com/lensapp/lens-extension-samples/blob/master/styling-emotion-sample/renderer.tsx"
    click E2 "https://github.com/lensapp/lens-extension-samples/blob/master/styling-emotion-sample/page.tsx"
    click E3 "https://github.com/lensapp/lens-extension-samples/blob/master/styling-emotion-sample/package.json"
    click E4 "https://github.com/lensapp/lens-extension-samples/blob/master/styling-emotion-sample/tsconfig.json"
    click E5 "https://github.com/lensapp/lens-extension-samples/blob/master/styling-emotion-sample/webpack.config.js"
    click E6 "https://github.com/lensapp/lens-extension-samples/tree/master/styling-emotion-sample/Makefile"

    %% Click Events for Styling with SASS Sample
    click S1 "https://github.com/lensapp/lens-extension-samples/blob/master/styling-sass-sample/renderer.tsx"
    click S2 "https://github.com/lensapp/lens-extension-samples/blob/master/styling-sass-sample/page.tsx"
    click S3 "https://github.com/lensapp/lens-extension-samples/blob/master/styling-sass-sample/styles.scss"
    click S4 "https://github.com/lensapp/lens-extension-samples/blob/master/styling-sass-sample/package.json"
    click S5 "https://github.com/lensapp/lens-extension-samples/blob/master/styling-sass-sample/tsconfig.json"
    click S6 "https://github.com/lensapp/lens-extension-samples/blob/master/styling-sass-sample/webpack.config.js"
    click S7 "https://github.com/lensapp/lens-extension-samples/tree/master/styling-sass-sample/Makefile"

classDef entry fill:#FC33,stroke:#333,stroke-width:2px
classDef ui fill:#66CC,stroke:#333,stroke-width:2px
classDef logic fill:#9F21,stroke:#333,stroke-width:2px
classDef config fill:#1F92,stroke:#333,stroke-width:2px
classDef styling fill:#CC92,stroke:#333,stroke-width:2px
classDef lens fill:#FD75,stroke:#333,stroke-width:2px

```



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---