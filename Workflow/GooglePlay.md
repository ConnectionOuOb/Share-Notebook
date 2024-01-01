# GooglePlay 上架流程

## 規範
1. 2021起，Google Play 上的新應用程式都必須以 Android App Bundle 檔案格式發布
  - 如果大小超過 200 MB，可以使用 Play Asset Delivery 或 Play Feature Delivery
2. 應用程式測試規定
  - 若開發人員的個人帳戶是在 2023 年 11 月 13 日之後建立，**就必須符合特定測試規定才能上架**
  - 測試群組
    - 內部測試
      - 必要性 : 非必要
      - 時間點 : 應用程式設定前
      - 使用者 : 一小群信任的測試人員
    - 封閉測試
      - 必要性 : **必要**
      - 時間點 : 完成應用程式設定後，就可以開始執行封閉測試
      - 使用者 : 自行控管的一大群使用者
      - 申請正式版權限時，至少須有 20 名測試人員選擇參與封閉測試，且必須在過去 14 天內持續參加測試
    - 公開測試
      - 時間點 : 應用程式和商店資訊已經準備好在 Google Play 發布
      - 需要取得正式版權限，才能執行公開測試
    - 正式版
      - 必要性 : **必要**
      - 時間點 : 執行符合標準的封閉測試，才能申請發布正式版應用程式
      - 使用者 : 數十億 Google Play 使用者

## 步驟
1. 註冊 Google Play 開發人員帳戶
  - 開通使用 **Play 管理中心/google play console** 的權限
  - 需要付 $25 美金註冊費
  - 需用身分證、駕照驗證註冊者身分
2. 數位簽署
  - 產生 ```.keystore```
    - 機敏資訊，切勿外流
    - 記錄了開發者數位簽署資訊
    - 一個keystore可以簽署多個app
    - 流程
      1. 進入想要存放keystore的位置
      2. 在當前路徑之下產生key，透過工具keytool(Android環境下載的JDK中)產生
        - ```keytool -genkey -v -keystore YOUR_KEYSTORE_NAME.jks -alias ALIAS_OF_KEY -keyalg RSA -keysize 2048 -validity 10000```
        - ```-keystore``` : 設定我們想命名的.keystore檔案名稱
        - ```-alias``` : 設定對這個key的代稱
  - ```key.properties```
    - 專案中 **/android** 目錄下
    - 密碼為明碼輸入，不可外流 or Commit
    - 設定以下內容
```
storePassword=keystore的密碼
keyPassword=key的密碼，由於這次是用keytool產生的，會跟keystore一樣
keyAlias=下指令時輸入的的ALIAS_OF_KEY
storeFile=在本機存放.keystore的位置
```
3. 專案打包
  1. 設定gradle
  2. 在 **/android/app/build.gradle** 設定如下，讓 gradle 讀到 key.properties
```
def keystoreProperties = new Properties()
def keystorePropertiesFile = rootProject.file('key.properties') // 放在/android下的key.properties檔案
if (keystorePropertiesFile.exists()) {
    keystoreProperties.load(new FileInputStream(keystorePropertiesFile))
}
```
  3. buildTypes區域加入release相關設定，並新增signingConfigs(簽署設定)，將keystoreProperties加進去
```
signingConfigs {
   release {
       keyAlias keystoreProperties['keyAlias']
       keyPassword keystoreProperties['keyPassword']
       storeFile keystoreProperties['storeFile'] ? file(keystoreProperties['storeFile']) : null
       storePassword keystoreProperties['storePassword']
   }
}
buildTypes {
   release {
       signingConfig signingConfigs.release // 將signingConfigs.debug改為.release
   }
}
```
  4. 編譯成 bundle
    - ```flutter build appbundle```

## 參考文章
1. [使用應用程式套件探索工具檢查應用程式版本](https://support.google.com/googleplay/android-developer/answer/9844279)
2. [適用於新建個人開發人員帳戶的應用程式測試規定](https://support.google.com/googleplay/android-developer/answer/14151465)
3. [from start to store](https://ithelp.ithome.com.tw/users/20152234/ironman/5606)
