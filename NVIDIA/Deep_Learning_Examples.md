---
created: 2025-03-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExMWV1Z3FlaW4yZ20ydGppNHAyeTE2cGlmN3lxMGNtOGttYnhic3QyaSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/SP3PM4hfVbyPhKfnf1/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# Deep Learning Examples
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
title: "NVIDIA - Deep Learning Examples"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: default
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "graph": { "htmlLabels": false, 'curve': 'linear' },
    'themeVariables': {
        'fontFamily': 'Comic Sans MS',
        'fontSize': '20px',
        'primaryColor': '#ffff',
        'primaryTextColor': '#55ff',
        'primaryBorderColor': '#7c2',
        'lineColor': '#F8B229',
        'secondaryColor': '#006100',
        'tertiaryColor': '#fff'
    }
  }
}%%
flowchart LR
    %% Central Hub
    H["Deep Learning Examples Repository"]:::hub

    %% Domain Clusters
    subgraph "Computer Vision"
        CV_Hub["Computer Vision"]:::domain
        CV_Py["PyTorch Classification"]:::framework
        CV_MX["MXNet Classification"]:::framework
        CV_PP["PaddlePaddle Classification"]:::framework
        CV_TF["TensorFlow Classification"]:::framework
        CV_TF2["TensorFlow2 Classification"]:::framework
        CV_Hub --> CV_Py
        CV_Hub --> CV_MX
        CV_Hub --> CV_PP
        CV_Hub --> CV_TF
        CV_Hub --> CV_TF2
    end

    subgraph "Natural Language Processing"
        NLP_Hub["Natural Language Processing"]:::domain
        NLP_PyBERT["PyTorch NLP (BERT)"]:::framework
        NLP_PyTransformer["PyTorch NLP (Transformer‑XL)"]:::framework
        NLP_TF["TensorFlow NLP (BERT)"]:::framework
        NLP_TF2_BERT["TensorFlow2 NLP (BERT)"]:::framework
        NLP_TF2_ELECTRA["TensorFlow2 NLP (ELECTRA)"]:::framework
        NLP_JAX["JAX Language Modeling"]:::framework
        NLP_Hub --> NLP_PyBERT
        NLP_Hub --> NLP_PyTransformer
        NLP_Hub --> NLP_TF
        NLP_Hub --> NLP_TF2_BERT
        NLP_Hub --> NLP_TF2_ELECTRA
        NLP_Hub --> NLP_JAX
    end

    subgraph "Speech Recognition"
        SR_Hub["Speech Recognition"]:::domain
        SR_Kaldi["Kaldi Speech Recognition"]:::framework
        SR_Py["PyTorch Speech Recognition"]:::framework
        SR_Hub --> SR_Kaldi
        SR_Hub --> SR_Py
    end

    subgraph "Speech Synthesis"
        SS_Hub["Speech Synthesis"]:::domain
        SS_CUDA_FastSpeech["CUDA‑Optimized FastSpeech"]:::framework
        SS_CUDA_Tacotron2["CUDA‑Optimized Tacotron2"]:::framework
        SS_Py_FastPitch["PyTorch Speech Synthesis FastPitch"]:::framework
        SS_Py_HiFiGAN["PyTorch Speech Synthesis HiFiGAN"]:::framework
        SS_Py_Tacotron2["PyTorch Speech Synthesis Tacotron2"]:::framework
        SS_Hub --> SS_CUDA_FastSpeech
        SS_Hub --> SS_CUDA_Tacotron2
        SS_Hub --> SS_Py_FastPitch
        SS_Hub --> SS_Py_HiFiGAN
        SS_Hub --> SS_Py_Tacotron2
    end

    subgraph "Graph Neural Networks"
        GNN_Hub["Graph Neural Networks"]:::domain
        GNN_SE3["Drug Discovery (SE3Transformer)"]:::framework
        GNN_MoFlow["MoFlow Graph Discovery"]:::framework
        GNN_Hub --> GNN_SE3
        GNN_Hub --> GNN_MoFlow
    end

    subgraph "Recommendation Systems"
        REC_Hub["Recommendation Systems"]:::domain
        REC_Py["PyTorch Recommendation"]:::framework
        REC_TF["TensorFlow Recommendation"]:::framework
        REC_TF2["TensorFlow2 Recommendation"]:::framework
        REC_Hub --> REC_Py
        REC_Hub --> REC_TF
        REC_Hub --> REC_TF2
    end

    subgraph "Time Series Forecasting"
        TS_Hub["Time Series Forecasting"]:::domain
        TS_Py["PyTorch Forecasting"]:::framework
        TS_TSPP["Time Series Prediction Platform"]:::framework
        TS_Hub --> TS_Py
        TS_Hub --> TS_TSPP
    end

    %% Common Processing Pipeline
    DP["Data Ingestion & Preprocessing"]:::data
    TM["Training Modules"]:::train
    ME["Model Export & Conversion"]:::export
    ID["Inference & Deployment"]:::inference

    %% External NVIDIA Integration
    NS["NVIDIA Software Stack Integration"]:::external

    %% Connections from Repository to Domains
    H --> CV_Hub
    H --> NLP_Hub
    H --> SR_Hub
    H --> SS_Hub
    H --> GNN_Hub
    H --> REC_Hub
    H --> TS_Hub

    %% Connections from Domain Hubs to Common Pipeline
    CV_Hub --> DP
    NLP_Hub --> DP
    SR_Hub --> DP
    SS_Hub --> DP
    GNN_Hub --> DP
    REC_Hub --> DP
    TS_Hub --> DP

    %% Common Pipeline Flow
    DP --> TM
    TM --> ME
    ME --> ID

    %% External Integration links
    NS --> TM
    NS --> ID

    %% Click Events for Central Hub
    click H "https://github.com/nvidia/deeplearningexamples/blob/master/README.md"

    %% Click Events for Computer Vision
    click CV_Py "https://github.com/nvidia/deeplearningexamples/tree/master/PyTorch/Classification/ConvNets"
    click CV_MX "https://github.com/nvidia/deeplearningexamples/blob/master/MxNet/Classification/RN50v1.5"
    click CV_PP "https://github.com/nvidia/deeplearningexamples/blob/master/PaddlePaddle/Classification/RN50v1.5"
    click CV_TF "https://github.com/nvidia/deeplearningexamples/tree/master/TensorFlow/Classification/ConvNets"
    click CV_TF2 "https://github.com/nvidia/deeplearningexamples/tree/master/TensorFlow2/Classification/ConvNets"

    %% Click Events for Natural Language Processing
    click NLP_PyBERT "https://github.com/nvidia/deeplearningexamples/tree/master/PyTorch/LanguageModeling/BERT"
    click NLP_PyTransformer "https://github.com/nvidia/deeplearningexamples/tree/master/PyTorch/LanguageModeling/Transformer‑XL"
    click NLP_TF "https://github.com/nvidia/deeplearningexamples/tree/master/TensorFlow/LanguageModeling/BERT"
    click NLP_TF2_BERT "https://github.com/nvidia/deeplearningexamples/tree/master/TensorFlow2/LanguageModeling/BERT"
    click NLP_TF2_ELECTRA "https://github.com/nvidia/deeplearningexamples/tree/master/TensorFlow2/LanguageModeling/ELECTRA"
    click NLP_JAX "https://github.com/nvidia/deeplearningexamples/tree/master/JAX/LanguageModeling"

    %% Click Events for Speech Recognition
    click SR_Kaldi "https://github.com/nvidia/deeplearningexamples/tree/master/Kaldi/SpeechRecognition"
    click SR_Py "https://github.com/nvidia/deeplearningexamples/tree/master/PyTorch/SpeechRecognition"

    %% Click Events for Speech Synthesis
    click SS_CUDA_FastSpeech "https://github.com/nvidia/deeplearningexamples/tree/master/CUDA-Optimized/FastSpeech"
    click SS_CUDA_Tacotron2 "https://github.com/nvidia/deeplearningexamples/tree/master/CUDA-Optimized/Tacotron2"
    click SS_Py_FastPitch "https://github.com/nvidia/deeplearningexamples/tree/master/PyTorch/SpeechSynthesis/FastPitch"
    click SS_Py_HiFiGAN "https://github.com/nvidia/deeplearningexamples/tree/master/PyTorch/SpeechSynthesis/HiFiGAN"
    click SS_Py_Tacotron2 "https://github.com/nvidia/deeplearningexamples/tree/master/PyTorch/SpeechSynthesis/Tacotron2"

    %% Click Events for Graph Neural Networks
    click GNN_SE3 "https://github.com/nvidia/deeplearningexamples/tree/master/DGLPyTorch/DrugDiscovery/SE3Transformer"
    click GNN_MoFlow "https://github.com/nvidia/deeplearningexamples/tree/master/PyTorch/DrugDiscovery/MoFlow"

    %% Click Events for Recommendation Systems
    click REC_Py "https://github.com/nvidia/deeplearningexamples/tree/master/PyTorch/Recommendation"
    click REC_TF "https://github.com/nvidia/deeplearningexamples/tree/master/TensorFlow/Recommendation"
    click REC_TF2 "https://github.com/nvidia/deeplearningexamples/tree/master/TensorFlow2/Recommendation"

    %% Click Events for Time Series Forecasting
    click TS_Py "https://github.com/nvidia/deeplearningexamples/tree/master/PyTorch/Forecasting/TFT"
    click TS_TSPP "https://github.com/nvidia/deeplearningexamples/tree/master/Tools/PyTorch/TimeSeriesPredictionPlatform"

    %% Styles
    classDef hub fill:#9fdf9f,stroke:#333,stroke-width:2px;
    classDef domain fill:#9cdff3,stroke:#333,stroke-width:2px;
    classDef framework fill:#e8e8e8,stroke:#333,stroke-width:1px;
    classDef data fill:#cce5ff,stroke:#333,stroke-width:2px;
    classDef train fill:#ffd699,stroke:#333,stroke-width:2px;
    classDef export fill:#ffdd99,stroke:#333,stroke-width:2px;
    classDef inference fill:#ccffcc,stroke:#333,stroke-width:2px;
    classDef external fill:#f9c0c0,stroke:#333,stroke-width:2px;
    
```





---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
