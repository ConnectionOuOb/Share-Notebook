Conda
===

安裝
---
- 官方教學 : [傳送門](https://docs.anaconda.com/free/anaconda/install/)

常用指令
---

1. updte
    1. 更新全部套件
        - ```conda update --all```
    2. 更新 conda
        - 建議下載完就跑這指令
        - ```conda update conda```
    3. 更新套件
        - ```conda update {套件名稱}```
2. install
    1. 下載單一套件
        - ```conda install {套件名稱}```
    2. 下載多個套件
        - ```conda install {套件名稱1} {套件名稱2} {套件名稱3}```
    3. 下載特定套件版本
        - ```conda install {套件名稱}={套件版本}```
        - 如 Tensorflow 2.5.0 版，就是 ```conda install Tensorflow=2.5.0```
3. uninstall
    1. 刪除套件
        - ```conda uninstall {套件名稱}```
4. env
    1. 列出所有已經建立的環境
        - ```conda env list```
    2. 建立空的虛擬環境
        - ```conda create -n {新虛擬環境名稱}```
    3. 建立有特定版本Python的虛擬環境
        - ```conda create -n {新虛擬環境名稱} python={python版本}```
    4. 進入虛擬環境
        - ```conda activate {虛擬環境名稱}```
    5. 離開虛擬環境
        - ```conda deactivate```
    6. 輸出虛擬環境設定到 yml
        - ```conda env export > {yml檔案位置}```
    7. 用 yml 建立虛擬環境
        - ```conda env create -f {yml檔案位置}```
    8. 重新命名虛擬環境
        - ```conda rename -n {舊名稱} {新名稱}```
