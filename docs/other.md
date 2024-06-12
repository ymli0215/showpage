## Agent

撰寫 \*.devin 檔案，裡面描述包含以下三種內容，執行後的回傳內容會依 Agent 不同而進行不同類型的檔案新增或修改，以@entity 為例，就會輸出對應的 Java Entity 與 Repository 檔案

- 使用的 Agent, EX: @entity
- 自訂的參數, EX: -->package:tw.ibm.com
- 要執行的內容，在上述內容之下

### wild agent

可以使用以下範例做測試，等待幾秒後就可以看到內容被取代

1. 內容寫到 `.vscode/coder-prompt/javaMethodGenerate.devin`
2. 任意編輯器選取 **hello world**
3. 按右鍵執行 **Auto Coder - Dynamic** > **javaMethodGenerate.devin**

```
@wild

- no explain, only response code
- Profession at Java and SpringBoot development
- split business logic to sub method by spec description
- only create method
```
