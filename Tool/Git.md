## 大綱
### 1. 建立儲存庫
####  - 遠端
####  - 本地
### 2. 初次上傳專案
####   - 從遠端拉到本地
####   - 從本地上傳遠端
### 3. 後續工作流程
####   - 命令行模式
####   - GitHub desktop

## 1. 建立儲存庫 (以 GitHib 為範例)
###  遠端
1. 登入 [GitHub](https://github.com/login)
2. 登入成功後導航到 [Dashboard](https://github.com/)
3. 點選圖片中 **New** 按鈕
![image](https://github.com/ConnectionOuOb/Share-Notebook/assets/69660530/a6d409b7-eaa8-4fb2-90b2-50659cb0cf9a)
4. 新 Repository 設定
![image](https://github.com/ConnectionOuOb/Share-Notebook/assets/69660530/ea2b275b-c898-48bb-933f-98fc2c8055b7)
    - Owner
        - 可以選擇讓新儲存庫建立到個人或是組織
    - Repository name
        - 設定新儲存庫的名稱，不能與 Owner 設定儲存的地方裡面的專案相同名稱
    - Description (optional)
        - 專案簡短說明，可留空
    - Public / Private
        - Public 是指網路上任何人都可以看到這個儲存庫
        - Private 模式
            - Owner 建立到個人
                - 預設只有自己看的到
                - 可以另外給其他人權限
            - Owner 建立到組織
                - 預設只有自己以及組織的最高權限擁有者看的到
                - 可以另外給其他人或是其他 Team 權限
5. 初始化設定
6. 點選 **Create Repository** 按鈕
7. 建立成功

### 本地
1. 開啟 Terminal
2. 跳轉到以下任一種目錄
    - 想要全新建立的專案
    - 想要上傳專案到 GitHib 的專案
3. 輸入指令 ```git init```
4. 建立成功
