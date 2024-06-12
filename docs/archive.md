<h1 align="center">VSCode開發小幫手</h1>
<p align="center">

結合 **生成式 AI** 與 **傳統程式生成** ，提供使用 VSCode 進行專案開發時的各種協助，VSCode 擴充套件下載<a href="https://pages.github.ibm.com/twix-ai/twix-all4one-vscode/twix-all4one-vscode-0.0.1.vsix" class="download-link" download>
請按此
</a>

> 使用前需開啟 Settings -> search `>twix`，並設定以下兩個參數
>
> - twix.agentUrl：後端 Server 位置
> - twix.token: 存取權限

## 特色

#### 1. GenAI 檔案執行

找到 `*.devin` 檔案，按右鍵執行 **AutoCoder - Run Devin File** ，檔案內的 @{agentName} 會判斷使用那個 Agent 與 GenAI 進行對話，並回傳結果

- @entity: 產成 Entity 與 Repository
- @business: 產成 Business Controller / Rq/ Rq / Service / ControllerTest
- @ddl: Excel/Word 中的資料表轉換成 DB DDL
- @wild: (搭配 Custom Prompt 使用)不做任何加工，直接後送 GenAI
- @i18n: (搭配 Custom Prompt 使用)執行檔案/目錄的翻譯

#### 2. 選取內容並以 GenAI 回覆取代

選取要處理的內容，再選取定義於 `.vscode/coder-prompt` 的提示內容，由系統進行 GenAI 對話並將使用回傳的第一個程式區塊取代編輯器上的內容

- @wild ： 取代原內容
- @wild appendBefore ： 新增內容到前面
- @wild appendBefore ： 新增內容到後面

#### 3. 檔案/目錄處理

- 複製功能：依選取目錄/檔案，按右鍵執行 **AutoCoder - Clone File/Folder**， 指定 1.輸出目錄；2.原始交易代號；3.目地交易代號，接下來就會自行執行目錄/檔案的複製與取代(含內容)
- 翻譯功能 - 依選取目錄/檔案，按右鍵執行 **AutoCoder - I18n**，接下來就會自行執行目錄/檔案的中文內容翻譯，如果過程中沒有找到要輸出的翻譯檔，則中英對照內容會輸出到第一個檔案最下方
