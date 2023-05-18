CodeFormer
===

簡介
---

- 圖片影片超分辨率、修復軟體
- 官方網站 : [傳送門](https://github.com/sczhou/CodeFormer)

安裝方法
---

1. [安裝 Git](https://github.com/Connection2Peter/ConnectionNotebook/blob/main/Git/README.md)
2. [安裝 Conda](https://github.com/Connection2Peter/ConnectionNotebook/blob/main/Conda/README.md)
3. 開一個 Terminal，輸入 ```cd {目標目錄}``` 移動到要下載的目錄
4. 輸入 ```git clone https://github.com/sczhou/CodeFormer``` CodeFormer 下來
5. 輸入 ```cd CodeFormer``` 進入 CodeFormer 資料夾
6. ```conda create -n codeformer python=3.8 -y```
7. ```conda activate codeformer```
8. ```pip3 install -r requirements.txt```
9. ```python basicsr/setup.py develop```
10. 要用 dlib 跑臉部辨識就下載 ```conda install -c conda-forge dlib```
11. 要用跑影片增強就下載 ```conda install -c conda-forge ffmpeg```

前置動作
---

1. 下載 facelib 預訓練模型到 **weights/facelib** 資料夾
    - ```python scripts/download_pretrained_models.py facelib```
    - ```python scripts/download_pretrained_models.py dlib``` (要用 dlib 跑臉部辨識再下載)
2. 下載 CodeFormer 預訓練模型到 **weights/CodeFormer** 資料夾
    - ```python scripts/download_pretrained_models.py CodeFormer```

使用指令
---

- 通用參數
    - ```-i```、```--input_path```，輸入的影片或圖片路徑
    - ```-o```、```--output_path```，輸出的影片或圖片路徑
    - ```-w```， 0 到 1，w調到小的話結果會比較好，調整到大的話會失真，不過沒有絕對關係

- 臉部修復
    - ```python inference_codeformer.py -w 0.5 --has_aligned --input_path {Input資料夾或圖片的位置}```

- 圖像全局加強
    - ```python inference_codeformer.py -w 0.7 --input_path {Input資料夾或圖片的位置}```

- 影片修復/加強
    - ```python inference_codeformer.py --bg_upsampler realesrgan --face_upsample -w 1.0 --input_path {Input影片的路徑}```

參考來源
---
1. https://github.com/sczhou/CodeFormer
