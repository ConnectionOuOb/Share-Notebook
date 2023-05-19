SoftVC VITS Singing Voice Conversion 4.0
===

簡介
---

- 使用 SoftVC 內容編碼器或獲得音特徵，直接輸入 VITS 生成語音
- 官方網站 : [傳送門](https://github.com/svc-develop-team/so-vits-svc)

安裝方法
---

1. [安裝 Git](Tool/ProgramEnvironment/Git/README.md)
2. [安裝 Conda](Tool/ProgramEnvironment/Conda/README.md)
3. 開一個 Terminal，輸入 ```cd {目標目錄}``` 移動到要下載的目錄
4. ```git clone https://github.com/svc-develop-team/so-vits-svc```
5. ```cd so-vits-svc``` 進入 so-vits-svc 資料夾
6. ```conda create -n so-vits-svc python=3.8 -y```
7. ```conda activate so-vits-svc```
8. 安裝套件
    - Windows
        1. ```conda install pytorch==1.13.1 torchvision==0.14.1 torchaudio==0.13.1 pytorch-cuda=11.7 -c pytorch -c nvidia```
        2. ```pip install -r requirements_win.txt```
    - Linux
        1. ```pip install -r requirements.txt```

前置動作
---

1. 擇一 encoder 下載到 **pretrain** 資料夾
    1. ContentVec:
        - [載點](http://obs.cstcloud.cn/share/obs/sankagenkeshi/checkpoint_best_legacy_500.pt)  
        - ```wget -P pretrain/ http://obs.cstcloud.cn/share/obs/sankagenkeshi/checkpoint_best_legacy_500.pt```
        - 也可以放在 **hubert** 資料夾
    2. hubertsoft:
        - [載點](https://github.com/bshall/hubert/releases/download/v0.1/hubert-soft-0d54a1f4.pt)
2. (可選，但強烈推薦) 下載 svc-develop-team 的 Pre-trained model 到 **logs/44k** 資料夾
3. (可選) 要用 NSF-HIFIGAN enhancer 的話，下載預訓練模型並解壓縮到 **pretrain/nsf_hifigan** 資料夾
    - [載點](https://github.com/openvpi/vocoders/releases/download/nsf-hifigan-v1/nsf_hifigan_20221211.zip)
    - ```wget -P pretrain/ https://github.com/openvpi/vocoders/releases/download/nsf-hifigan-v1/nsf_hifigan_20221211.zip```

資料前處理
---

- 目標 : 每個訓練的音檔都 5 到 15 秒，並且盡量乾淨無雜音
- 可用工具
    1. 分離人聲以及背景的軟體
        - [UVR](https://github.com/Connection2Peter/ConnectionNotebook/blob/main/Tool/Media/Audio/UVR5/README.md)
    2. 音擋切分軟體
        - [Audio Slicer](https://github.com/Connection2Peter/ConnectionNotebook/blob/main/Tool/Media/Audio/AudioSlicer/README.md)
- 要訓練的資料集放在 **dataset_raw** 資料夾中，格式如下
```
dataset_raw
├───speaker0 (可改成任意名稱)
│   ├───xxx1-xxx1.wav
│   ├───...
│   └───Lxx-0xx8.wav
└───speaker1 (可改成任意名稱)
    ├───xx2-0xxx2.wav
    ├───...
    └───xxx7-xxx007.wav
```

使用指令
---

1. ```python resample.py```
2. ```python preprocess_flist_config.py --speech_encoder vec768l12```
    - **speech_encoder** 可以改成 ```vec768l12```(預設)、```vec256l9```、```hubertsoft```
3. ```python preprocess_hubert_f0.py --f0_predictor dio```
    - **f0_predictor** 可以改成
        - ```crepe```，使用在資料及很 noisy
        - ```dio```，這是預設
        - ```pm```
        - ```harvest```
4. 正式訓練 : ```python train.py -c configs/config.json -m 44k```
5. 推導出結果
    - 指令
        - ```python inference_main.py -m "logs/44k/G_30400.pth" -c "configs/config.json" -n "君の知らない物語-src.wav" -t 0 -s "nen"```
    - 必備參數
        1. -m | --model_path : path to the model.
        2. -c | --config_path : path to the configuration file.
        3. -n | --clean_names : a list of wav file names located in the raw folder.
        4. -t | --trans : pitch adjustment, supports positive and negative (semitone) values.
        5. -s | --spk_list : target speaker name for synthesis.
        6. -cl | --clip : voice forced slicing, set to 0 to turn off(default), duration in seconds.
    - 可選參數
        1. -lg | --linear_gradient: The cross fade length of two audio slices in seconds. If there is a discontinuous voice after forced slicing, you can adjust this value. Otherwise, it is recommended to use the default value of 0.
        2. -f0p | --f0_predictor: Select F0 predictor, can select crepe,pm,dio,harvest, default pm(note: crepe is original F0 meaning pooling)
        3. -a | --auto_predict_f0: automatic pitch prediction for voice conversion, do not enable this when converting songs as it can cause serious pitch issues.
        4. -cm | --cluster_model_path: path to the clustering model, fill in any value if clustering is not trained.
        5. -cr | --cluster_infer_ratio: proportion of the clustering solution, range 0-1, fill in 0 if the clustering model is not trained.
        6. -eh | --enhance: Whether to use NSF_HIFIGAN enhancer, this option has certain effect on sound quality enhancement for some models with few training sets, but has negative effect on well-trained models, so it is turned off by default.

參考來源
---
1. https://github.com/svc-develop-team/so-vits-svc
