---
created: 2025-06-27 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/grpc/psm-interop
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExM2dyNWNxMWc5dDJzbWNiY2RyMzV6MXVmdWM0ZDF3d3QwNGMyc2NsOCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/jSDRVBcoaBqTCfr6ZX/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# psm-interop repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for 👨‍🎓 <ins>educational purposes</ins> 👨‍🎓 (<ins>:trollface:sometimes, entertainment purposes:trollface:</ins>), 📖 <ins> personal study </ins> 📖, and 🔖 <ins> reference </ins> 🔖.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>



---

```mermaid
---
title: "psm-interop repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': { 'htmlLabels': true, 'curve': 'linear'},
    'fontFamily': 'Monaco',
    'themeVariables': {
      'primaryColor': '#22BB',
      'primaryTextColor': '#F8B229',
      'lineColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#EEF2',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD',
      'fontSize': '15px'
    }
  }
}%%
flowchart LR
    %% Classes
    classDef onprem fill:#AEDFF7,stroke:#333,stroke-width:1px
    classDef cloud fill:#A3E4A3,stroke:#333,stroke-width:1px
    classDef storage fill:#F5CBA7,stroke:#333,stroke-width:1px
    classDef infra fill:#AED6F1,stroke:#333,stroke-width:1px
    classDef k8s fill:#D2B4DE,stroke:#333,stroke-width:1px
    classDef rpc fill:#F9E79F,stroke:#333,stroke-width:1px
    classDef app fill:#F5B7B1,stroke:#333,stroke-width:1px

    %% Control Plane
    subgraph "Control Plane"
        CLI["Developer CLI & Helper Scripts"]:::onprem
        Config["Abseil-style Configuration"]:::onprem
        CLI -->|uses| Config

        subgraph "Framework Infrastructure - GCP"
            API["api.py"]:::infra
            NS["network_services.py"]:::infra
            NSEC["network_security.py"]:::infra
            CMP["compute.py"]:::infra
            IAMg["iam.py"]:::infra
            CRg["cloud_run.py"]:::infra
        end
        CLI -->|invokes| API
        API --> NS
        API --> NSEC
        API --> CMP
        API --> IAMg
        API --> CRg

        subgraph "Framework Infrastructure - Kubernetes"
            K8sWrap["k8s.py"]:::infra
            K8sInt["k8s_internal/..."]:::infra
        end
        CLI -->|invokes| K8sWrap
        K8sWrap -->|manages| K8sInt

        subgraph "Framework Infrastructure - Mesh Resource Managers"
            SPIFFE["spiffe_mesh_manager.py"]:::infra
            CRm["cloud_run_mesh_manager.py"]:::infra
        end
        API -->|optional| CRm
        API -->|optional| SPIFFE

        subgraph "Framework RPC Helpers & Protos Imports"
            GRPC["grpc.py"]:::rpc
            CHZ["grpc_channelz.py"]:::rpc
            CSDS["grpc_csds.py"]:::rpc
            GTEST["grpc_testing.py"]:::rpc
            XDSPI["xds_protos_imports.py"]:::rpc
        end
        CLI -->|uses| GRPC

        subgraph "Framework Test Applications"
            ServerApp["server_app.py"]:::app
            ClientApp["client_app.py"]:::app
        end
        CLI -->|launches| ServerApp
        CLI -->|launches| ClientApp

        subgraph "Framework Test Runners"
            BaseRun["base_runner.py"]:::app
            subgraph "K8s Runners"
                K8sSrv["k8s_xds_server_runner.py"]:::app
                K8sCli["k8s_xds_client_runner.py"]:::app
                GammaSrv["gamma_server_runner.py"]:::app
            end
            subgraph "Cloud Run Runners"
                CRSrv["cloud_run_xds_server_runner.py"]:::app
                CRCli["cloud_run_xds_client_runner.py"]:::app
            end
        end
        CLI -->|orchestrates| BaseRun
        BaseRun --> K8sSrv
        BaseRun --> K8sCli
        BaseRun --> GammaSrv
        BaseRun --> CRSrv
        BaseRun --> CRCli
    end

    %% Google Cloud Services
    subgraph "Google Cloud Services"
        TD["Traffic Director API"]:::cloud
        IAMsvc["IAM"]:::cloud
        ComputeSvc["Compute"]:::cloud
        Artifact["Artifact Registry"]:::cloud
    end
    API -->|configures| TD
    API -->|configures| IAMsvc
    API -->|configures| ComputeSvc
    CMP -->|push images| Artifact

    %% Kubernetes Cluster
    subgraph "Kubernetes Cluster (GKE)"
        Namespaces["Namespaces per Test"]:::k8s
        subgraph "Pods & Services"
            ServerDep["psm-grpc-server Deployment"]:::k8s
            ClientDep["psm-grpc-client Deployment"]:::k8s
            ServicePSM["ClusterIP/LoadBalancer & Policies"]:::k8s
        end
    end
    K8sWrap -->|applies manifests| Namespaces
    K8sInt -->|executes| ServerDep
    K8sInt -->|executes| ClientDep
    K8sInt -->|sets| ServicePSM

    %% Data Plane
    ClientDep -->|"gRPC Data"| ServicePSM
    ServicePSM -->|"forwards"| ServerDep
    ClientDep -->|"xDS Control Streams"| TD
    TD -->|"configures"| ClientDep
    TD -->|"configures"| ServerDep

    %% Click Events
    click CLI "https://github.com/grpc/psm-interop/tree/main/bin/"
    click Config "https://github.com/grpc/psm-interop/tree/main/config/"
    click API "https://github.com/grpc/psm-interop/blob/main/framework/infrastructure/gcp/api.py"
    click NS "https://github.com/grpc/psm-interop/blob/main/framework/infrastructure/gcp/network_services.py"
    click NSEC "https://github.com/grpc/psm-interop/blob/main/framework/infrastructure/gcp/network_security.py"
    click CMP "https://github.com/grpc/psm-interop/blob/main/framework/infrastructure/gcp/compute.py"
    click IAMg "https://github.com/grpc/psm-interop/blob/main/framework/infrastructure/gcp/iam.py"
    click CRg "https://github.com/grpc/psm-interop/blob/main/framework/infrastructure/gcp/cloud_run.py"
    click K8sWrap "https://github.com/grpc/psm-interop/blob/main/framework/infrastructure/k8s.py"
    click K8sInt "https://github.com/grpc/psm-interop/tree/main/framework/infrastructure/k8s_internal/"
    click SPIFFE "https://github.com/grpc/psm-interop/blob/main/framework/infrastructure/mesh_resource_manager/spiffe_mesh_manager.py"
    click CRm "https://github.com/grpc/psm-interop/blob/main/framework/infrastructure/mesh_resource_manager/cloud_run_mesh_manager.py"
    click GRPC "https://github.com/grpc/psm-interop/blob/main/framework/rpc/grpc.py"
    click CHZ "https://github.com/grpc/psm-interop/blob/main/framework/rpc/grpc_channelz.py"
    click CSDS "https://github.com/grpc/psm-interop/blob/main/framework/rpc/grpc_csds.py"
    click GTEST "https://github.com/grpc/psm-interop/blob/main/framework/rpc/grpc_testing.py"
    click XDSPI "https://github.com/grpc/psm-interop/blob/main/framework/rpc/xds_protos_imports.py"
    click ServerApp "https://github.com/grpc/psm-interop/blob/main/framework/test_app/server_app.py"
    click ClientApp "https://github.com/grpc/psm-interop/blob/main/framework/test_app/client_app.py"
    click BaseRun "https://github.com/grpc/psm-interop/blob/main/framework/test_app/runners/base_runner.py"
    click K8sSrv "https://github.com/grpc/psm-interop/blob/main/framework/test_app/runners/k8s/k8s_xds_server_runner.py"
    click K8sCli "https://github.com/grpc/psm-interop/blob/main/framework/test_app/runners/k8s/k8s_xds_client_runner.py"
    click GammaSrv "https://github.com/grpc/psm-interop/blob/main/framework/test_app/runners/k8s/gamma_server_runner.py"
    click CRSrv "https://github.com/grpc/psm-interop/blob/main/framework/test_app/runners/cloud_run/cloud_run_xds_server_runner.py"
    click CRCli "https://github.com/grpc/psm-interop/blob/main/framework/test_app/runners/cloud_run/cloud_run_xds_client_runner.py"

    %% Styles
    class CLI,Config onprem
    class API,NS,NSEC,CMP,IAMg,CRg,K8sWrap,K8sInt,SPIFFE,CRm infra
    class GRPC,CHZ,CSDS,GTEST,XDSPI rpc
    class ServerApp,ClientApp,BaseRun,K8sSrv,K8sCli,GammaSrv,CRSrv,CRCli app
    class TD,IAMsvc,ComputeSvc,Artifact cloud
    class Namespaces,ServerDep,ClientDep,ServicePSM k8s

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
