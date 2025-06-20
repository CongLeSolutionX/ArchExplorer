---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/google-deepmind/dm_control
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




# dm_control repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes (<ins>sometimes, entertainment purposes</ins>), personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>


----

```mermaid
---
title: "dm_control repo project"
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
    %% Layers
    subgraph "User Layer"
        direction TB
        UserScript["User Script / RL Code"]:::external_gray
    end

    subgraph "dm_control Python API"
        direction TB
        subgraph "Simulation API"
            direction TB
            MujocoPkg["dm_control.mujoco"]:::sub_blue
            MJCFPkg["dm_control.mjcf"]:::sub_blue
            ComposerPkg["dm_control.composer"]:::sub_blue
            SuitePkg["dm_control.suite"]:::sub_blue
            AutowrapPkg["dm_control.autowrap"]:::sub_blue
            BlenderPkg["dm_control.blender.mujoco_exporter"]:::sub_blue
            UtilsPkg["dm_control.utils"]:::sub_blue
            RLPkg["dm_control.rl.control"]:::sub_blue
            ThirdParty["dm_control.third_party"]:::sub_blue
        end
    end

    subgraph "Binding Layer"
        direction TB
        WrapperDir["pybind11 Wrapper"]:::sub_blue
        EngineIntegration["engine.py"]:::sub_blue
        IndexModule["index.py"]:::sub_blue
        MathModule["math.py"]:::sub_blue
    end

    subgraph "Core Engine"
        direction TB
        MuJoCoCore["MuJoCo C/C++ Engine"]:::core_green
    end

    subgraph "Viewer & Rendering"
        direction TB
        ViewerPkg["dm_control.viewer"]:::sub_blue
        subgraph "Rendering Backends"
            direction TB
            GLFW["glfw_renderer.py"]:::render_orange
            EGL["egl_renderer.py"]:::render_orange
            OSMesa["osmesa_renderer.py"]:::render_orange
        end
    end

    subgraph "External Dependencies"
        direction TB
        OpenGL["OpenGL / GLEW / OS libs"]:::external_gray
        Assets["Asset Files (XML, STL, MSH)"]:::external_gray
    end

    Hardware["Hardware / OS"]:::external_gray

    %% Connections
    UserScript -->|"imports & calls"| MujocoPkg
    UserScript -->|"imports & calls"| MJCFPkg
    UserScript -->|"imports & calls"| ComposerPkg
    UserScript -->|"imports & calls"| SuitePkg
    UserScript -->|"imports & calls"| ViewerPkg

    MujocoPkg -->|"calls wrapper"| WrapperDir
    WrapperDir --> IndexModule
    WrapperDir --> MathModule
    WrapperDir --> EngineIntegration
    WrapperDir -->|"binds to"| MuJoCoCore

    MJCFPkg -->|"generates XML"| MuJoCoCore
    ComposerPkg -->|"builds tasks/envs"| MuJoCoCore
    SuitePkg -->|"loads assets & env definitions"| MuJoCoCore

    MuJoCoCore -->|"state & images"| ViewerPkg
    ViewerPkg -->|"renders via"| GLFW
    ViewerPkg -->|"renders via"| EGL
    ViewerPkg -->|"renders via"| OSMesa

    MJCFPkg -->|"loads"| Assets
    SuitePkg -->|"loads"| Assets
    ViewerPkg -->|"uses"| OpenGL
    GLFW -->|calls| OpenGL
    EGL -->|calls| OpenGL
    OSMesa -->|calls| OpenGL

    MuJoCoCore --> Hardware

    %% Click Events
    click WrapperDir "https://github.com/google-deepmind/dm_control/tree/main/dm_control/mujoco/wrapper/"
    click EngineIntegration "https://github.com/google-deepmind/dm_control/blob/main/dm_control/mujoco/engine.py"
    click IndexModule "https://github.com/google-deepmind/dm_control/blob/main/dm_control/mujoco/index.py"
    click MathModule "https://github.com/google-deepmind/dm_control/blob/main/dm_control/mujoco/math.py"
    click MJCFPkg "https://github.com/google-deepmind/dm_control/tree/main/dm_control/mjcf/"
    click MJCFPkg "https://github.com/google-deepmind/dm_control/blob/main/dm_control/mjcf/element.py"
    click MJCFPkg "https://github.com/google-deepmind/dm_control/blob/main/dm_control/mjcf/parser.py"
    click MJCFPkg "https://github.com/google-deepmind/dm_control/blob/main/dm_control/mjcf/physics.py"
    click ComposerPkg "https://github.com/google-deepmind/dm_control/tree/main/dm_control/composer/"
    click ComposerPkg "https://github.com/google-deepmind/dm_control/blob/main/dm_control/composer/environment.py"
    click ComposerPkg "https://github.com/google-deepmind/dm_control/blob/main/dm_control/composer/entity.py"
    click ComposerPkg "https://github.com/google-deepmind/dm_control/blob/main/dm_control/composer/task.py"
    click SuitePkg "https://github.com/google-deepmind/dm_control/tree/main/dm_control/suite/"
    click SuitePkg "https://github.com/google-deepmind/dm_control/blob/main/dm_control/suite/cartpole.py"
    click SuitePkg "https://github.com/google-deepmind/dm_control/blob/main/dm_control/suite/cheetah.py"
    click SuitePkg "https://github.com/google-deepmind/dm_control/blob/main/dm_control/suite/humanoid.py"
    click GLFW "https://github.com/google-deepmind/dm_control/blob/main/dm_control/_render/glfw_renderer.py"
    click EGL "https://github.com/google-deepmind/dm_control/blob/main/dm_control/_render/pyopengl/egl_renderer.py"
    click OSMesa "https://github.com/google-deepmind/dm_control/blob/main/dm_control/_render/pyopengl/osmesa_renderer.py"
    click ViewerPkg "https://github.com/google-deepmind/dm_control/tree/main/dm_control/viewer/"
    click ViewerPkg "https://github.com/google-deepmind/dm_control/blob/main/dm_control/viewer/application.py"
    click ViewerPkg "https://github.com/google-deepmind/dm_control/blob/main/dm_control/viewer/gui/glfw_gui.py"
    click ViewerPkg "https://github.com/google-deepmind/dm_control/blob/main/dm_control/viewer/renderer.py"
    click ViewerPkg "https://github.com/google-deepmind/dm_control/blob/main/dm_control/viewer/viewer.py"
    click AutowrapPkg "https://github.com/google-deepmind/dm_control/tree/main/dm_control/autowrap/"
    click AutowrapPkg "https://github.com/google-deepmind/dm_control/blob/main/dm_control/autowrap/autowrap.py"
    click AutowrapPkg "https://github.com/google-deepmind/dm_control/blob/main/dm_control/autowrap/binding_generator.py"
    click BlenderPkg "https://github.com/google-deepmind/dm_control/tree/main/dm_control/blender/mujoco_exporter/"
    click BlenderPkg "https://github.com/google-deepmind/dm_control/blob/main/dm_control/blender/mujoco_exporter/blender_scene.py"
    click BlenderPkg "https://github.com/google-deepmind/dm_control/blob/main/dm_control/blender/mujoco_exporter/mujoco_assets.py"
    click UtilsPkg "https://github.com/google-deepmind/dm_control/tree/main/dm_control/utils/"
    click UtilsPkg "https://github.com/google-deepmind/dm_control/blob/main/dm_control/utils/containers.py"
    click UtilsPkg "https://github.com/google-deepmind/dm_control/blob/main/dm_control/utils/inverse_kinematics.py"
    click UtilsPkg "https://github.com/google-deepmind/dm_control/blob/main/dm_control/utils/rewards.py"
    click RLPkg "https://github.com/google-deepmind/dm_control/blob/main/dm_control/rl/control.py"
    click ThirdParty "https://github.com/google-deepmind/dm_control/tree/main/dm_control/third_party/kinova/"
    click ThirdParty "https://github.com/google-deepmind/dm_control/tree/main/dm_control/third_party/ant/"

    %% Styles
    classDef sub_blue fill:#AED6F1,stroke:#21618C,color:#154360;
    classDef core_green fill:#ABEBC6,stroke:#196F3D,color:#145A32;
    classDef render_orange fill:#F5B041,stroke:#B9770E,color:#7E5109;
    classDef external_gray fill:#D5D8DC,stroke:#566573,color:#2E4053;

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