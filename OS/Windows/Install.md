Windows USB 安裝流程
===

事前準備
---

1. 材料
    1. 下載 Windows 安裝 ISO 檔
    2. 一個 USB，至少 16 GB 
    3. 一台要安裝的電腦 or 伺服器
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
        1. 開機過程中會出現按某些按鍵(如 Del, F10, F12)可以進入 Bios setting
        2. 上網查詢主機板說明書
3. Bios 需要調整的設定
    1. (重要) 開機順序
        - 把 USB 安裝碟拉到第一順位
    2. (可選) 效能設定
        - 關閉自動效能調節，強制鎖在最高效能
        - 關閉風扇調節，強制使用最高散熱
4. 儲存 Bios 設定
5. 重新啟動


Windows 11 安裝設定
---

1. 開機
    1. **機器**
    2. **主控台**
    3. **啟動**
2. 立即安裝
    ![image](https://github.com/Connection2Peter/ConnectionNotebook/assets/69660530/36b0729f-1b9b-4a84-9017-ae3812b40c25)
3. 選 Windows 11 的版本
    - 如果要開啟遠端桌面，必須至少要為專業版以上
    ![image](https://github.com/Connection2Peter/ConnectionNotebook/assets/69660530/40ef8c16-a7fb-4083-9793-15b1f8b98174)
4. 接受
    ![image](https://github.com/Connection2Peter/ConnectionNotebook/assets/69660530/d1270b18-c777-4543-88e5-ed1f8c1b16a0)
5. 選自訂
    ![image](https://github.com/Connection2Peter/ConnectionNotebook/assets/69660530/e82672b5-61ff-4016-bc95-6d0c96192c9c)
6. 選系統碟，選自動分割確認後繼續
7. 下一步
8. 電腦重啟   


系統內設定
---

1. 設定地區
2. 設定輸入法
3. 沒有網際網路
4. 進行有限的設定
5. 設定 **名稱**
6. 設定 **密碼**
7. 填寫安全性問題
8. 關閉所有隱私設定
9. **設定** -> **系統** -> **關於** -> **進階系統設定** -> **效能設定** -> **調整為最佳效能** -> **確定**
10. **設定** -> **系統** -> **重新命名** -> **立即重新啟動**
11. **設定** -> **系統** -> **遠端桌面** -> 開啟
12. **設定** -> **系統** -> **開啟/關閉** -> **螢幕與睡眠** -> **永不**
13. 系統更新到最新
13. 完成，關機

