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
6. 切到 **硬體** -> **CD/DVD** -> 換成 **virtio** ISO
7. 選對應 driver
    ![image](https://github.com/Connection2Peter/ConnectionNotebook/assets/69660530/f744d9ae-e1ed-49bc-a614-d83068114c66)
8. 切到 **硬體** -> **CD/DVD** -> 換回 **Win 11** ISO
9. 下一步
10. 虛擬機自動重啟   
11. 設定地區
12. 設定輸入法
13. 沒有網際網路
14. 進行有限的設定
15. 設定 **名稱**
16. 設定 **密碼**
17. 填寫安全性問題
18. 關閉所有隱私設定
19. 切到 **硬體** -> **CD/DVD** -> 換成 **virtio** ISO
20. **裝置管理員** -> **Ethernet 控制卡** -> 右鍵 **更新驅動程式** -> 瀏覽 VirtIO ISO 的驅動
![image](https://github.com/Connection2Peter/ConnectionNotebook/assets/69660530/918d90d4-15d7-47ca-ae62-2ac7db2f13da)
21. **設定** -> **系統** -> **關於** -> **進階系統設定** -> **效能設定** -> **調整為最佳效能** -> **確定**
22. (可選) **設定** -> **應用程式** -> **應用程式與功能** -> 移除掉 :
    ```Groove 音樂、Microsoft OneDrive、Microsoft Solitaire Collection、Microsoft 新聞、Office、Microsoft TODO、Microsoft Automate、Xbox*、天氣、便籤、語音與電視、電影與電視```
23. **設定** -> **系統** -> **重新命名** -> **立即重新啟動**
24. **設定** -> **系統** -> **遠端桌面** -> 開啟
25. **設定** -> **系統** -> **開啟/關閉** -> **螢幕與睡眠** -> **永不**
26. 關掉虛擬機
27. 加硬碟
28. 設定參數
29. 加網路裝置
30. 設定如下
![image](https://github.com/Connection2Peter/ConnectionNotebook/assets/69660530/6f7de7d8-3d3d-4c2c-ba58-1d0e310649e6)
31. 退出 CD/DVD
32. **機器** -> **主控台** -> **啟動**
33. **磁碟管理** -> **GPT格式化** -> **簡單磁區格式化**
34. 完成，關機
