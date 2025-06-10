---
created: 2025-03-21 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExNTIzMjFxZmYwcXBqeGZ0eWR4cXduOGtndzlrZXNjOWd4eDl1YTRjMyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/Kn5YFlengdRmw/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# Docling TS
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
title: "Docling TS"
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
    'flowchart': {'htmlLabels': true, 'curve': 'basis' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'lineColor': '#F8B229'
    }
  }
}%%
flowchart TD
    %% Docling Core Subgraph
    subgraph Docling_Core["Docling Core"]
        core_index("Index"):::core
        core_typesIndex("Types Index"):::core
        core_models("Models"):::core
        core_typing("Typing"):::core
        core_tsconfig("tsconfig.json"):::core
        core_tsup("tsup.config.ts"):::core
        core_vitest("vitest.config.ts"):::core
    end

    %% Docling Components Subgraph
    subgraph Docling_Components["Docling Components"]
        comp_imgPage("ImgPage<br>(svelte)"):::component
        comp_imgPages("ImgPages<br>(svelte)"):::component
        comp_cropped("CroppedItem<br>(svelte)"):::component
        comp_parsed("ParsedItem<br>(svelte)"):::component
        comp_tableItem("TableItem<br>(svelte)"):::component
        comp_itemIndex("Item Index"):::component
        comp_tablePage("TablePage<br>(svelte)"):::component
        comp_tablePages("TablePages<br>(svelte)"):::component
        comp_tableRow("TableRow<br>(svelte)"):::component
        comp_props("Props"):::component
        comp_util("Util"):::component
        comp_tsconfig("tsconfig.json"):::component
        comp_svelteup("svelteup.config.js"):::component
        comp_eslint("eslint.config.mjs"):::component
        comp_prettierrc(".prettierrc"):::component
        comp_stylelintrc(".stylelintrc"):::component
    end

    %% Example Application (Deno) Subgraph
    subgraph Example_Application["Example Application<br>(Deno)"]
        ex_readme("Deno README"):::example
        ex_denoConfig("deno.json"):::example
        ex_serve("serve.sh"):::example
        ex_src("Source Code"):::example
        ex_static("Static Assets"):::example
    end

    %% Documentation & Supporting Assets Subgraph
    subgraph Documentation_and_Supporting_Assets["Documentation & Supporting Assets"]
        docs_dir("Docs Directory"):::docs
        root_readme("README.md"):::docs
        root_code("CODE_OF_CONDUCT.md"):::docs
        root_license("LICENSE"):::docs
        root_gitignore(".gitignore"):::docs
    end

    %% External dependencies
    svelte("Svelte Framework"):::external
    deno("Deno Runtime"):::external

    %% High-level dependency relationships using representative nodes
    core_index -->|"provides types"| comp_imgPage
    core_index -->|"integrated"| ex_readme
    comp_imgPage -->|"renders UI"| ex_readme
    comp_imgPage -->|"built with"| svelte
    ex_readme -->|"runs on"| deno

    %% Click Events for Docling Core
    click core_index "https://github.com/docling-project/docling-ts/blob/main/docling-core/src/index.ts"
    click core_typesIndex "https://github.com/docling-project/docling-ts/blob/main/docling-core/src/types/index.ts"
    click core_models "https://github.com/docling-project/docling-ts/blob/main/docling-core/src/types/models.ts"
    click core_typing "https://github.com/docling-project/docling-ts/blob/main/docling-core/src/types/typing.ts"
    click core_tsconfig "https://github.com/docling-project/docling-ts/blob/main/docling-core/tsconfig.json"
    click core_tsup "https://github.com/docling-project/docling-ts/blob/main/docling-core/tsup.config.ts"
    click core_vitest "https://github.com/docling-project/docling-ts/blob/main/docling-core/vitest.config.ts"

    %% Click Events for Docling Components
    click comp_imgPage "https://github.com/docling-project/docling-ts/blob/main/docling-components/src/img/ImgPage.svelte"
    click comp_imgPages "https://github.com/docling-project/docling-ts/blob/main/docling-components/src/img/ImgPages.svelte"
    click comp_cropped "https://github.com/docling-project/docling-ts/blob/main/docling-components/src/item/CroppedItem.svelte"
    click comp_parsed "https://github.com/docling-project/docling-ts/blob/main/docling-components/src/item/ParsedItem.svelte"
    click comp_tableItem "https://github.com/docling-project/docling-ts/blob/main/docling-components/src/item/TableItem.svelte"
    click comp_itemIndex "https://github.com/docling-project/docling-ts/blob/main/docling-components/src/item/index.ts"
    click comp_tablePage "https://github.com/docling-project/docling-ts/blob/main/docling-components/src/table/TablePage.svelte"
    click comp_tablePages "https://github.com/docling-project/docling-ts/blob/main/docling-components/src/table/TablePages.svelte"
    click comp_tableRow "https://github.com/docling-project/docling-ts/blob/main/docling-components/src/table/TableRow.svelte"
    click comp_props "https://github.com/docling-project/docling-ts/blob/main/docling-components/src/props.ts"
    click comp_util "https://github.com/docling-project/docling-ts/blob/main/docling-components/src/util.ts"
    click comp_tsconfig "https://github.com/docling-project/docling-ts/blob/main/docling-components/tsconfig.json"
    click comp_svelteup "https://github.com/docling-project/docling-ts/blob/main/docling-components/svelteup.config.js"
    click comp_eslint "https://github.com/docling-project/docling-ts/blob/main/docling-components/eslint.config.mjs"
    click comp_prettierrc "https://github.com/docling-project/docling-ts/blob/main/docling-components/.prettierrc"
    click comp_stylelintrc "https://github.com/docling-project/docling-ts/blob/main/docling-components/.stylelintrc"

    %% Click Events for Example Application (Deno)
    click ex_readme "https://github.com/docling-project/docling-ts/blob/main/examples/deno/README.md"
    click ex_denoConfig "https://github.com/docling-project/docling-ts/blob/main/examples/deno/deno.json"
    click ex_serve "https://github.com/docling-project/docling-ts/blob/main/examples/deno/serve.sh"
    click ex_src "https://github.com/docling-project/docling-ts/tree/main/examples/deno/src/"
    click ex_static "https://github.com/docling-project/docling-ts/tree/main/examples/deno/static/"

    %% Click Events for Documentation & Supporting Assets
    click docs_dir "https://github.com/docling-project/docling-ts/tree/main/docs/"
    click root_readme "https://github.com/docling-project/docling-ts/blob/main/README.md"
    click root_code "https://github.com/docling-project/docling-ts/blob/main/CODE_OF_CONDUCT.md"
    click root_license "https://github.com/docling-project/docling-ts/tree/main/LICENSE"
    click root_gitignore "https://github.com/docling-project/docling-ts/blob/main/.gitignore"

    %% Styles
    classDef core fill:#f9c3,stroke:#000,stroke-width:2px
    classDef component fill:#bbf3,stroke:#000,stroke-width:2px
    classDef example fill:#cfc3,stroke:#000,stroke-width:2px
    classDef docs fill:#ff93,stroke:#000,stroke-width:2px
    classDef external fill:#ddd3,stroke:#000,stroke-width:2px

```






---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
