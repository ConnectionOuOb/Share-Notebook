建立 Windows 11 虛擬機模板
===

Proxmox 設定
---

1. 點選右上角 **建立 VM**
    ![image](https://github.com/Connection2Peter/ConnectionNotebook/assets/69660530/9bf4cd84-7449-4b21-a88c-7fc6096189f4)
2. 設定模板資訊
    1. 設定 **ID**
    2. 設定 **名稱**
    3. 點選 **繼續**
    ![image](https://github.com/Connection2Peter/ConnectionNotebook/assets/69660530/8943c6d0-8b19-488e-b130-19115aad59da)
3. 設定作業系統
    1. **使用 CD/DVD 光碟映像檔案（ISO）** 選 **Windows 11 ISO 檔** (必須先上傳到 local)
    2. **客體作業系統** 設定成 **Microsoft Windows** 的 **11/2022** 版本
    3. 點選 **繼續**
    ![image](https://github.com/Connection2Peter/ConnectionNotebook/assets/69660530/f21cd7e3-3ac8-4633-bcb1-571dc84ee5b8)
4. 設定系統
    1. 設定 **EFI 儲存** 及 **TPM 儲存** 位置
    2. 其餘設定按照照片
    3. 點選 **繼續**
    ![image](https://github.com/Connection2Peter/ConnectionNotebook/assets/69660530/f864134a-d8bb-49a6-9ab6-161d4e990d3a)
5. 磁碟設定
    ![image](https://github.com/Connection2Peter/ConnectionNotebook/assets/69660530/3103bb32-e971-456c-95d3-a3a3b1d7252e)
6. CPU 設定
    ![image](https://github.com/Connection2Peter/ConnectionNotebook/assets/69660530/aadff596-9b0b-43be-bab1-1f1d96ffb031)
7. 記憶體設定
    ![image](https://github.com/Connection2Peter/ConnectionNotebook/assets/69660530/9a9143cd-1ea3-4a00-930e-f59343225b4e)
8. 網路設定
    ![image](https://github.com/Connection2Peter/ConnectionNotebook/assets/69660530/b5727d4c-83d4-4ffd-8fee-966958449f47)
9. 按完成

Windows 11 設定
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
22. (可選) **設定** -> **應用程式** -> **應用程式與功能**
    移除掉 :
    ```Groove 音樂、Microsoft OneDrive、Microsoft Solitaire Collection、Microsoft 新聞
    Office、Microsoft TODO、Microsoft Automate、Xbox*、天氣、便籤、語音與電視、電影與電視```
23. **設定** -> **系統** -> **重新命名** 填成 ```Template``` -> '''立即重新啟動'''
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
