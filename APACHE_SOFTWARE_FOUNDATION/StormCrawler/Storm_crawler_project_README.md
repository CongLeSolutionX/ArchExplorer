---
created: 2025-06-04 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/apache/stormcrawler/blob/main/README.md
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExZmJ5Zm5hYzUwbGZld2k4cWFiZTczbDJ6czd6cnR1MjhlYmxnYzRldCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/qWx5C3iSfwa6Q/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----

# StormCrawler Project README - A diagrammatic version 
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---

# Apache StormCrawler: A Deep Dive 🕷️💨

Apache StormCrawler is an open-source collection of resources designed for building low-latency, scalable web crawlers. It leverages the power of [Apache Storm](http://storm.apache.org/) for distributed stream processing. The project is licensed under the [Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0) and is primarily written in Java.

---

## 🎯 Core Goal

To provide a flexible and robust framework for developers to create custom web crawlers that can handle large volumes of data with minimal delay.

---

## 🏛️ Ecosystem Overview

StormCrawler doesn't exist in a vacuum. It interacts with several other key technologies to provide its functionality.

<details open>
<summary>Click to show/hide the full native DOT implementation</summary>


```dot
/*
 * title: Ecosystem Overview
 * author: Cong Le
 * version: 1.0
 * license(s): MIT, CC BY-SA 4.0
 * copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
 */
digraph StormCrawlerEcosystem {
    bgcolor="transparent";
    node [shape=component, style=filled, fillcolor="#F2F2F2", fontname="Arial"];
    edge [fontname="Arial", fontsize=10];

    user [label="Developer/User", shape=invhouse, fillcolor="#B0E0E6"];
    project [label="Your StormCrawler\nProject", fillcolor="#D3D3D3"];
    archetype [label="Maven Archetype\n(stormcrawler-archetype)", fillcolor="#ADD8E6"];
    stormcrawler_core [label="StormCrawler Core\n(Java Libraries)"];
    storm [label="Apache Storm Cluster", shape=cylinder, fillcolor="#FFDAC1"];
    maven [label="Apache Maven", shape=cds, fillcolor="#FFEBCD"];
    java [label="Java 17+", shape=octagon, fillcolor="#98FB98"];
    docker [label="Docker\n(for Tests)", shape=box, style=rounded, fillcolor="#E6E6FA"];
    resources [label="Configuration Files\n(crawler.flux, crawler-conf.yaml)", shape=note, fillcolor="#FAFAD2"];

    user -> archetype [label="uses to generate"];
    archetype -> project [label="generates"];
    project -> stormcrawler_core [label="depends on"];
    project -> storm [label="deploys as topology on"];
    project -> resources [label = "configures with"];
    stormcrawler_core -> java [label="requires"];
    project -> maven [label="built with"];
    stormcrawler_core -> maven [label="managed by"];
    project [ peripheries=2 ]; // Indicates the user's main focus

    subgraph TestEnvironment {
        label = "Testing Environment";
        style = "filled";
        color = "lightgrey";
        node [style=filled,color=white];
        stormcrawler_core -> docker [label="tests run using", style=dashed];
    }
}
```

</details>


This diagram illustrates:
*   A **Developer/User** :🧑‍💻 interacts with the **Maven Archetype** to generate a new **StormCrawler Project**.
*   This project depends on **StormCrawler Core** libraries.
*   The project is configured using files like `crawler.flux` and `crawler-conf.yaml`.
*   **Apache Maven** :hammer_and_wrench: is used to build the project and manage dependencies.
*   The crawler itself runs as a topology on an **Apache Storm Cluster** :cyclone:.
*   **Java 17+** :coffee: is a fundamental requirement.
*   **Docker** :whale: is needed if you intend to run the tests.

---

## 🚀 Quickstart Guide

Getting a basic StormCrawler instance up and running is straightforward, especially using the Maven archetype.

**Prerequisites:**
1.  **Apache Maven** installed ([Installation Guide](https://maven.apache.org/install.html)).
2.  **Apache Storm 2.8.0** installed ([Downloads](http://storm.apache.org/)).
3.  **Java 17 or above.**
4.  **Docker** environment (if running tests).

**Steps:**

```mermaid
---
title: "Quickstart Guide"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  theme: base
  look: classic
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': { 'htmlLabels': true, 'curve': 'basis' },
    'fontFamily': 'Comic Sans MS, cursive, sans-serif',
    'themeVariables': {
      'primaryColor': '#F3E333',
      'primaryTextColor': '#145A32',
      'lineColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#EBDEF0',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD',
      'fontSize': '15px'
    }
  }
}%%
flowchart TD
    A["Install Apache Maven"] --> B["Install Apache Storm 2.8.0"]
    B --> C["Ensure Java 17+ is active"]
    C --> D{"Want to run tests?"}
    D -- Yes --> E["Install Docker"]
    D -- No --> F["Generate Project via Maven Archetype"]
    E --> F
    F -- Run Command --> G["<code>mvn archetype:generate ...</code>"]
    G --> H["Enter Project Details <br/> e.g., groupId, artifactId, version, user-agent"]
    H --> I["Project Directory Created! 🎉"]
    I --> J["Navigate to Project Directory"]
    J --> K["Follow README instructions in new project"]
```

**Maven Archetype Command:**  
Execute this in your terminal:
```bash
mvn archetype:generate -DarchetypeGroupId=org.apache.stormcrawler -DarchetypeArtifactId=stormcrawler-archetype -DarchetypeVersion=3.3.0
```
You'll be prompted for:
*   `groupId` (e.g., `com.mycompany.crawler`)
*   `artifactId` (e.g., `mycrawler`) - this will also be your project directory name.
*   `version` (e.g., `1.0-SNAPSHOT`)
*   `package` (e.g., `com.mycompany.crawler`)
*   `agentName`, `agentVersion`, `agentURL`, `agentEmail` - for the User-Agent string.

**What the Archetype Creates:**  
The archetype doesn't just create a `pom.xml` with dependencies; it bootstraps a complete project structure.

```mermaid
---
title: "What the Archetype Creates"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  theme: base
  look: classic
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': { 'htmlLabels': true, 'curve': 'basis' },
    'fontFamily': 'Comic Sans MS, cursive, sans-serif',
    'themeVariables': {
      'primaryColor': '#F3E333',
      'primaryTextColor': '#145A32',
      'lineColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#EBDEF0',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD',
      'fontSize': '15px'
    }
  }
}%%
flowchart LR
    A["Generated Project<br/>(e.g., 'mycrawler')"] --> B("<b>pom.xml</b>")
    A --> C["<b>README.md</b>"]
    A --> D["<b>src/main/java/.../CrawlTopology.java</b>"]
    A --> E["<b>src/main/resources/</b>"]
    E --> F("<b>crawler.flux</b>")
    E --> G("<b>crawler-conf.yaml</b>")
    E --> H("<b>es-conf.yaml</b>")
    E --> I("<b>urlfilters.json</b>")
    E --> J("<b>robots.txt</b> parser specific files, etc.")

    subgraph Key_Configuration["Key Configuration"]
    direction LR
        F; G; H; I; J;
    end

    style A fill:#D3D3D3,stroke:#333,stroke-width:2px
    style F fill:#FAFAD2,stroke:#333
    style G fill:#FAFAD2,stroke:#333
```
*   **`CrawlTopology.java`**: Your main class that defines the Storm topology.
*   **`crawler.flux`**: A [Flux](https://storm.apache.org/releases/current/flux.html) file defining the Storm topology components and their connections. This is where you define your spouts and bolts for crawling.
*   **`crawler-conf.yaml`**: The primary configuration file for StormCrawler specific settings (e.g., fetch intervals, user agent details if not from archetype).
*   Other files in `src/main/resources/` provide default configurations for various aspects like URL filtering, Elasticsearch indexing, etc.

**Alternative Setup (Manual):**  
If you prefer not to use the Maven archetype, you can manually copy the resources from the [archetype-resources](https://github.com/apache/stormcrawler/tree/master/archetype/src/main/resources/archetype-resources) directory on GitHub.

**Core Concept: The Crawler Topology 🌀**  
The `crawler.flux` file is central to defining your crawler. It describes a directed acyclic graph (DAG) of spouts (data sources) and bolts (data processors).

```mermaid
---
title: "The Crawler Topology"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  theme: base
  look: classic
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': { 'htmlLabels': true, 'curve': 'basis' },
    'fontFamily': 'Comic Sans MS, cursive, sans-serif',
    'themeVariables': {
      'primaryColor': '#F3E333',
      'primaryTextColor': '#145A32',
      'lineColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#EBDEF0',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD',
      'fontSize': '15px'
    }
  }
}%%
flowchart TD
    subgraph Storm_Topology["Storm Topology Defined in <b>crawler.flux</b>"]
        Spout["Spout(s)<br/>(e.g., <b>URLInjectorSpout</b>, <b>StatusStreamSpout</b>)"] -- URLs /<br/> Status --> Bolt1
        Bolt1["Bolt 1<br/>(e.g., <b>SiteMapParserBolt</b>)"] -- Parsed URLs --> Bolt2
        Bolt2["Bolt 2<br/>(e.g., <b>FetcherBolt</b>)"] -- Fetched Content --> Bolt3
        Bolt3["Bolt 3<br/>(e.g., <b>JSoupParserBolt</b>)"] -- Parsed Data /<br/> Outlinks --> Bolt4
        Bolt4["Bolt 4<br/>(e.g., <b>IndexerBolt</b> / <b>StatusUpdaterBolt</b>)"] -- To Storage /<br/> Status Update --> Output["Output<br/>(e.g., <b>Elasticsearch</b>, <b>Solr</b>, <b>Status Storage</b>)"]
    end

    style Spout fill:#B0E0E6,stroke:#333
    style Bolt1 fill:#ADD8E6,stroke:#333
    style Bolt2 fill:#ADD8E6,stroke:#333
    style Bolt3 fill:#ADD8E6,stroke:#333
    style Bolt4 fill:#ADD8E6,stroke:#333
    style Output fill:#98FB98,stroke:#333
```
This is a simplified, conceptual representation. The actual components and their connections are detailed in your `crawler.flux` file and configured via `crawler-conf.yaml`.

---

## 🆘 Getting Help

If you encounter issues or have questions:
1.  📚 **[WIKI](https://github.com/apache/stormcrawler/wiki)**: A great starting point for documentation and common questions.
2.  ❓ **StackOverflow**: Use the tag [`stormcrawler`](http://stackoverflow.com/questions/tagged/stormcrawler).
3.  🗣️ **GitHub Discussions**: Ask questions in the [discussions section](https://github.com/apache/stormcrawler/discussions).
4.  🏢 **Commercial Support**: A list of companies providing commercial support is available on the [project website](https://stormcrawler.apache.org/support/).

---

## 🛠️ Contributing & Building from Source

Contributions are welcome! 🤗

**Code Formatting:**  
Before submitting a Pull Request (PR), please format your code:
```bash
mvn git-code-format:format-code -Dgcf.globPattern="**/*" -Dskip.format.code=false
```
To enable pre-commit format hooks (recommended):
```bash
mvn clean install -Dskip.format.code=false
```

**Contribution Workflow:**

```mermaid
---
title: "Contribution Workflow"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  theme: base
  look: classic
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': { 'htmlLabels': true, 'curve': 'basis' },
    'fontFamily': 'Comic Sans MS, cursive, sans-serif',
    'themeVariables': {
      'primaryColor': '#F3E333',
      'primaryTextColor': '#145A32',
      'lineColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#EBDEF0',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD',
      'fontSize': '15px'
    }
  }
}%%
flowchart TD
    A["Write/Modify Code"] --> B{"Did you make changes?"}
    B -- Yes --> C["Format Code:<br/> <code>mvn git-code-format:format-code ...</code>"]
    C --> D["Commit Changes"]
    D --> E["Push to your Fork"]
    E --> F["Create Pull Request on GitHub"]
    B -- No --> G["No changes, no PR needed"]

    subgraph Setup_Pre_commit_Hook["Optional:<br/> Setup Pre-commit Hook"]
    direction LR
        H["Run <code>mvn clean install -Dskip.format.code=false</code> once"] --> I["Hook auto-formats on commit"]
    end
```

**Build Requirements:**
*   JDK 17+
*   Apache Maven 3
*   Docker (if you want to run tests, which is highly recommended for contributors)

**Building:**  
It's a standard Maven build process:
```bash
# 1. Clone the repository (if you haven't already)
# git clone https://github.com/apache/stormcrawler.git
# cd stormcrawler

# 2. Build
mvn clean install
```

**Build Process Flow:**

```mermaid
---
title: "Build Process Flow"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  theme: base
  look: classic
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': { 'htmlLabels': true, 'curve': 'basis' },
    'fontFamily': 'Comic Sans MS, cursive, sans-serif',
    'themeVariables': {
      'primaryColor': '#F3E333',
      'primaryTextColor': '#145A32',
      'lineColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#EBDEF0',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD',
      'fontSize': '15px'
    }
  }
}%%
flowchart TD
    AA["Clone StormCrawler Git Repo"] --> BB["Ensure JDK 17+, Maven 3 installed"]
    BB --> CC{"Want to run tests during build?"}
    CC -- Yes --> DD["Ensure Docker is running"]
    CC -- No --> EE["Run <code>mvn clean install -DskipTests</code> <br/>(Tests Recommended!)"]
    DD --> FF["Run <code>mvn clean install</code>"]
    FF --> GG{"Build Successful?"}
    EE -.-> GG
    GG -- Yes --> HH["Artifacts built! ✅"]
    GG -- No --> II["Build Failed ❌ - Check logs"]
```

**Note on Binary Files:**  
The project uses some binary files specifically for testing advanced crawler functionalities. These are located *only* within `src/test` directories of the relevant modules. They are not part of the core runtime dependencies.

---

## 🙏 Thanks

A special thank you to:

[![YourKit Logo](https://camo.githubusercontent.com/5ea9673ea42bd7754bdc762e8649bb3d1664481ca3ca678c52e9908e99a9782f/68747470733a2f2f7777772e796f75726b69742e636f6d2f696d616765732f796b6c6f676f2e706e67)](https://www.yourkit.com)

YourKit supports open source projects with its full-featured Java Profiler. YourKit, LLC is the creator of [YourKit Java Profiler](https://www.yourkit.com/java/profiler/index.jsp) and [YourKit .NET Profiler](https://www.yourkit.com/.net/profiler/index.jsp).

---

## 📖 References & Citations

*   Apache StormCrawler Official GitHub: [https://github.com/apache/stormcrawler](https://github.com/apache/stormcrawler)
*   Apache Storm: [http://storm.apache.org/](http://storm.apache.org/)
*   Apache Maven: [https://maven.apache.org/](https://maven.apache.org/)
*   Flux for Storm: [https://storm.apache.org/releases/current/flux.html](https://storm.apache.org/releases/current/flux.html)

----

I hope this detailed explanation with diagrams helps in understanding Apache StormCrawler better! 

Let me know if you have more questions. 😊



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
