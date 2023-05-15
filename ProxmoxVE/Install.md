Proxmox VE USB 安裝流程
===

事前準備
---

1. 材料
    1. 下載 Proxmox VE 安裝 ISO 檔
        - [Proxmox VE 官方網站](https://www.proxmox.com/en/proxmox-ve)
        - [Proxmox VE ISO 檔載點](https://www.proxmox.com/en/downloads/category/iso-images-pve)
    2. 一個 至少 8 GB 的 USB
    3. 一台要安裝的伺服器
        - CPU
          - 64 位元
          - 具有虛擬化指令集
        - 記憶體
          - Proxmox VE host 需要至少 1 GB
          - 看之後會增加幾台虛擬機，依照會配置的系統要求增加記憶體大小
        - 網卡
          - 至少一張，安裝的時候要用
        - 硬碟
          - 強烈建議用 SSD 安裝，可以的話上 NVME SSD
    4. Rufus 應用程式
        - 用途為把 ISO 檔燒錄成開機 USB
        - [Rufus 官網](https://rufus.ie/)

開機 USB 建立
---

1. 開啟 Rufus
2. 設定
    - 裝置 : 選擇要安裝的 USB
    - 開機模式 : 選擇要安裝的 ISO 檔案
3. 點選 **執行**
4. 開機 USB 建立完成

Bios 設定
---

1. 確保電腦是關機的，然後插上開機的 USB
2. 開機並進入主機板 Bios
    - 每張主機板開啟 Bios 方式都不同，查詢方法 :
        1. 開機過程中會出現按某些按鍵可以進入 Bios setting
        2. 上網查詢主機板說明書
3. Bios 需要調整的設定
    1. (重要) 開機順序
        - 把 USB 安裝碟拉到第一順位
    2. (重要) CPU 設定
        - Intel
            - 開啟 VT-x 指令集
            - 開啟 VT-d 指令集
        - AMD
            - 開啟 AMD SVM 指令集
            - 開啟 AMD-d 指令集
    3. (可選) 效能設定
        - 關閉自動效能調節，強制鎖在最高效能
        - 關閉風扇調節，強制使用最高散熱
4. 儲存 Bios 設定
5. 重新啟動

Proxmox VE 基本安裝
---

1. 選取 Install Proxmox VE
2. 同意授權內容
3. 設定安裝目的地硬碟以及檔案系統設定
4. 設定位置與時區
5. 輸入系統密碼以及管理者信箱
6. 設定網路裝置
7. 開始安裝
8. 系統安裝成功
9. 移除 USB

參考文章
---
1. https://ithelp.ithome.com.tw/articles/10265378
