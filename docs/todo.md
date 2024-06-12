## Todos

#### Agent（GenAI）

- [x] @entity - 生成 Entity 與 Repository
- [x] @ddl - 透過 Word/Excel 貼上的資料表定義，生成 指定的 DDL 檔案
- [x] @i18n - 傳入指定前端交易檔案，截取中文區段內容輸出到訊息檔，並以有意義的名稱做命名，原交易檔案也同步完成修改
- [x] @cht2eng - 依傳入內容轉譯成中英對照表

#### 文字內容轉換 （GenAI 轉換，並以結果中的第一個**程式碼區塊**取代）

- [x] 呼叫`@ddl`，將選取的內容轉換成 SQL DDL
- [x] 套用 `coder-prompt` 目錄下的提示，並以結果中的第一個**程式區**塊後取代 (適用附檔名為 \*.devin)
- [x] 呼叫 `@agent`，將選取的內容轉換成 Open API 格式 (適用附檔名為 \*.devin)
- [x] 掃描 `.vscode/coder-prompt` 目錄下的提示，建立動態選單

#### 程式碼生成 （套版）

- [x] @channel - 透過 OpenAPI 定義內容生成 Channel Server 的 Task / Rq / Rs 等物件
- [x] @business - 透過 OpenAPI 定義內容生成 Business Server 的 Controller / Rq / Rs / Service 等物件
- [x] @junitTest - 透過選取的程式內容以及補充說明文字生成 Junit Test 程式，並依據 Junit Test 程式檔案是否存在而產生新檔案或附加到原有 Junit Test 程式檔案中
- [x] @genDoc - 在開啟的Java檔案中，點擊要產生Document的Java Method中的任一個地方，按右鍵執行 **AutoCoder - Generate Document**，就會針對游標所屬的Java Method產生Document，如果點擊地方不屬於任何Method，但在Class程式範圍內，就針對整個Class內容產生Document。

#### 其它小工具

- [x] 複製功能 - 依選取目錄/檔案，並指定 1.輸出目錄；2.原始交易代號；3.目地交易代號，再執行複製與取代(含內容)
- [ ] 翻譯功能 - 依選取目錄/檔案，截取中文區段 **""** / **''** / **><** 中內含中文的檔案進行轉換，完成後再呼叫 **coder-script/i18n.js** 程式進行後續處理，如果找不到就會使用預設的
- [x] Git功能
    - [x] 產生Commit Message - 在Source Control View在Staged Changes Group上，滑鼠右鍵選擇 **Auto Coder - Generate Commit Message**，會依據已Staged的全部檔案的diff內容，產生建議的commit message.
    - [x] Code Review - 在選取的檔案上滑鼠右鍵選擇 **Auto Coder - Code Review**，依據被選取的檔案的diff內容進行Code Review. 可使用情境如下 :
        - 任一檔案開啟的編輯畫面
        - Source Control視窗，選取一個檔案
        - Source Control視窗，選取一個Group，ex: Staged Changes、Changes
