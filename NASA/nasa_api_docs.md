---
created: 2025-03-16 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExcDR0b2Zib2hrbXYzNDFiZnNrc3I0bDE0a2drcXc2M2Fyb3l3dmo5cCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/nEFaVNgFGGRQdWbmRq/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# NASA API Docs
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
title: "CHANGE_ME_DADDY"
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
    'graph': {'htmlLabels': true, 'curve': 'basis' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#ffff',
      'primaryTextColor': '#2ff9',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph TD
    %% Hosting Environment
    subgraph GitHub_Pages_Hosting["GitHub Pages<br>(Hosting)"]
        gp["GitHub Pages"]
    end

    %% Client: Web Browser
    subgraph Client_Web_Browser["Client:<br>Web Browser"]
        direction TB

        subgraph HTML_Pages["HTML Pages"]
            index["index.html"]
            auth["authentication.html"]
            browse["browseAPI.html"]
            recover["recoverKey.html"]
        end

        subgraph Template_Components["Template Components"]
            subgraph "Header Templates"
                header["header.html"]
                headerNo["header_noButtons.html"]
            end
            subgraph Footer_Components["Footer Components"]
                footerHtml["OIT-footer.html"]
                footerCss["OIT-footer.css"]
                footerJs["OIT-footer.js"]
            end
        end

        subgraph CSS_SCSS_Assets["CSS/SCSS Assets"]
            nasawdscss["NASA WDS CSS"]
            customcss["Custom Styles<br>(indexFormat.css)"]
            scss["SCSS Files"]
        end

        subgraph JavaScript_Components["JavaScript Components"]
            apiLoader["APILoader.js"]
            contentLoader["contentLoader.js"]
            gui["gui.js"]
            setup["setup.js"]
            nasawdsjs["nasawds.js"]
        end
    end

    %% Data Layer
    subgraph Data_Layer["Data Layer"]
        apis["apis.json"]
    end

    %% External Services
    subgraph External_API_Services["External API Services"]
        extApi["External API<br>(GSA/NASA)"]
    end

    %% Supporting Assets
    subgraph Supporting_Assets["Supporting Assets"]
        fonts["Fonts"]
        images["Images"]
        footerImages["Footer Images"]
    end

    %% Connections
    index -->|"load assets"| gp
    nasawdscss -->|"load CSS"| gp
    customcss -->|"load CSS"| gp
    scss -->|"load styles"| gp

    apiLoader -->|"fetch data"| apis
    contentLoader -->|"fetch data"| apis

    gui -->|"form submit"| extApi
    setup -->|"init UI"| index

    index -->|"load fonts"| fonts
    index -->|"load images"| images
    footerHtml -->|"load footer image"| footerImages

    %% Styles
    classDef browser fill:#cce5f,stroke:#003366,stroke-width:1px;
    classDef template fill:#e6ffe,stroke:#006600,stroke-width:1px;
    classDef css fill:#fff0e,stroke:#cc6600,stroke-width:1px;
    classDef js fill:#e6f7f,stroke:#005266,stroke-width:1px;
    classDef data fill:#f9e6f,stroke:#8a2be2,stroke-width:1px;
    classDef external fill:#ffe6e,stroke:#cc0000,stroke-width:1px;
    classDef support fill:#ffc5,stroke:#999900,stroke-width:1px;
    classDef host fill:#e6e6e,stroke:#666666,stroke-width:1px;

    class index,auth,browse,recover browser
    class header,headerNo,footerHtml,footerCss,footerJs template
    class nasawdscss,customcss,scss css
    class apiLoader,contentLoader,gui,setup,nasawdsjs js
    class apis data
    class extApi external
    class fonts,images,footerImages support
    class gp host

%% Click Events
click index "https://github.com/nasa/api-docs/blob/gh-pages//index.html"
click auth "https://github.com/nasa/api-docs/blob/gh-pages//assets/html/authentication.html"
click browse "https://github.com/nasa/api-docs/blob/gh-pages//assets/html/browseAPI.html"
click recover "https://github.com/nasa/api-docs/blob/gh-pages//assets/html/recoverKey.html"

click header "https://github.com/nasa/api-docs/blob/gh-pages//assets/html/header.html"
click headerNo "https://github.com/nasa/api-docs/blob/gh-pages//assets/html/header_noButtons.html"
click footerHtml "https://github.com/nasa/api-docs/blob/gh-pages//assets/footer/OIT-footer.html"
click footerCss "https://github.com/nasa/api-docs/blob/gh-pages//assets/footer/OIT-footer.css"
click footerJs "https://github.com/nasa/api-docs/blob/gh-pages//assets/footer/OIT-footer.js"

click nasawdscss "https://github.com/nasa/api-docs/blob/gh-pages//assets/css/nasawds.css"
click customcss "https://github.com/nasa/api-docs/blob/gh-pages//assets/css/indexFormat.css"
click scss "https://github.com/nasa/api-docs/tree/gh-pages//assets/scss/"

click apiLoader "https://github.com/nasa/api-docs/blob/gh-pages//assets/js/APILoader.js"
click contentLoader "https://github.com/nasa/api-docs/blob/gh-pages//assets/js/contentLoader.js"
click gui "https://github.com/nasa/api-docs/blob/gh-pages//assets/js/gui.js"
click setup "https://github.com/nasa/api-docs/blob/gh-pages//assets/js/setup.js"
click nasawdsjs "https://github.com/nasa/api-docs/blob/gh-pages//assets/js/nasawds.js"

click apis "https://github.com/nasa/api-docs/blob/gh-pages//assets/json/apis.json"

click fonts "https://github.com/nasa/api-docs/tree/gh-pages//assets/fonts/"
click images "https://github.com/nasa/api-docs/tree/gh-pages//assets/img/"
click footerImages "https://github.com/nasa/api-docs/tree/gh-pages//assets/footer/img/"

```






---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
