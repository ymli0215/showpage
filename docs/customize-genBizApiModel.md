# 用途

產生 Java RESTful API 的請求與回覆物件

## 樣版檔放置位置

- `.vscode/coder-prompt` 目錄
- 檔名為 `genBizApiModel.devin`

## 檔版檔內容

        @javaCode
        as a developer reference [SAMPLE] implemenet [CONTENT], apply following rules
        - no explanation and no response RetrieveCarrierNo code
        - generate Param Class with class and attributes comment in code
        - generate model class and detail class with class and attributes comment in code
        - use: "jakarta.validation", Lombok, BigDecimal represents money or rate, LocalDate, LocalDateTime
        - use lombok @getter and @setter at class level

        SAMPLE input :

        ```

        API: RetrieveCarrierNo
        API說明: 查詢載具號碼

        application name: business-pibmb-xxx-yyy
        application abbreviation: xyz

        欄位說明
        項次 欄位代號 欄位名稱 型別(最大長度) 必填 說明 開發說明
        Request Body：

        1.      custId	歸戶統編	string	Y
            Response Body：
        1.      custId	歸戶統編	string			[INVOICE_CARRIER.CUSTID]
        1.      carrierNo	載具號碼	string			[INVOICE_CARRIER.CARRIER]
        1.      updateTime	更新時間	string			[INVOICE_CARRIER.UPDATETIME]
        1.      status	狀態	number		0：未設定、1：驗證成功、2：驗證失敗	參考下方說明。
        1.      records(以下為一至多筆)
            5.1. reminderPk 提醒設定鍵值 number 值：[PAYMENT_REMINDER_SETTING.PAYMENT_REMINDER_SETTING_PK]
            5.2. itemId 繳費項目代號 string

        ```

        SAMPLE Param Class:

        ```

        package com.ytb.ibmb.business.xyz.param;

        /**
        *
        * <p>
        * RetrieveCarrierNoParam 查詢載具號碼
        * </p>
        */
        @Schema(description = "查詢載具號碼")
        @Getter
        @Setter
        public class RetrieveCarrierNoParam implements Serializable {

            /** serialVersionUID */
            private static final long serialVersionUID = 1L;

            /** 歸戶統編 */
            @NotEmpty
            private String custId;

        }

        ```

        SAMPLE Model Class and Detail Class:

        ```
        package com.ytb.ibmb.business.xyz.model;

        /**
        * <pre>
        * RetrieveCarrierNoModel 查詢載具號碼
        * </pre>
        */
        @Schema(description = "查詢載具號碼")
        @Getter
        @Setter
        public class RetrieveCarrierNoModel implements Serializable {

            /** serialVersionUID */
            private static final long serialVersionUID = 1L;

            /** 歸戶統編 */
            private String custId;

            /** 載具號碼 */
            private String carrierNo;

            /** 更新時間 */
            private LocalDateTime updateTime;

            /**
            * 狀態 0：未設定 1：驗證成功 2：驗證失敗
            */
            private Integer status;

            /**
            * records(以下為一至多筆)
            */
            private List<RetrieveCarrierNoModelRecord> records;

        }

        ```

        ```

        package com.ytb.ibmb.business.xyz.model;

        /**
        * <pre>
        * RetrieveCarrierNoModelRecord 查詢載具號碼
        * </pre>
        */
        @Schema(description = "查詢載具號碼")
        @Getter
        @Setter
        public class RetrieveCarrierNoModelRecord implements Serializable {

            /** serialVersionUID */
            private static final long serialVersionUID = 1L;

            /** 提醒設定鍵值 */
            private Long reminderPk;

            /** 項目代號 */
            private String itemId;

        }

        ```

        [CONTENT]

## 測試案例

選擇以下內容，按下「Shift + Cmd + R」或 右鍵選「Autocoder - Run」，完成後會產成最下方的檔案內容

        API: ValidateCardValidity
        API說明: 檢核信用卡有效性

        Request Body：

        1.      authType	驗證類型	number	Y	1：金融驗證2：本人本行信用卡
        2.      custId	歸戶統編	string	Y
        3.      cardNo	卡號	string	Y
        4.      expirationDate	有效日期	string	Y	MMYY
        5.      securityCode	安全碼	string	Y
        6.      mobile	電話	string
        7.      logType	紀錄驗證結果類別	string		1：開戶 2：辦卡(無值代表不紀錄驗證結果)
        8.      applyCaseNo	申請案件編號	string		(開戶才需填入)
        9.      authCustType	驗證客戶類型	number		(開戶才需填入)1：開戶申請人2：法定代理人
        10.     reptNo	法定代理人編號	number		(開戶才需填入)1：法定代理人12：法定代理人2

        Response Body：

        1.      authResult	驗證結果	number		1：驗證成功0：驗證失敗
        2.      authFailReason	驗證失敗原因	number		※[Rs.authResult]=“0”才會回傳此欄位
        3.      records(以下為一到多筆)
            3.1. programCode 分期計畫代碼 string [1440035_Rs.Record.PROGRAM]
            3.2. programDesc 分期計畫代碼說明 string [1440035_Rs.Record.INSTDESCR]
            3.3. installmentTerm 分期期數 number [1440035_Rs.Record.INSTTERM]
            3.4. fee 分期手續費 number [1440033_Rs.Record.INSTFEE]
            3.5. rate 分期利率 number [1440035_Rs.Record.INSTRATE]
            3.6. downPayment 首期應繳金額 number [1440035_Rs.Record.FIRST_INST]
            3.7. totalInterest 分期總利息 number [1440035_Rs.Record.TOTAL_INT]
            3.8 lastPayDate 上次交易日期 string

### 產生以下三個檔案與其對應內容

```java
package com.ytb.ibmb.business.xyz.param;

import io.swagger.v3.oas.annotations.OpenAPIDescription;
import lombok.Getter;
import lombok.Setter;
import java.io.Serializable;

/**
* <p>
* ValidateCardValidityParam 檢核信用卡有效性
* </p>
*/
@OpenAPIDescription("檢核信用卡有效性")
@Getter
@Setter
public class ValidateCardValidityParam implements Serializable {
    /** serialVersionUID */
    private static final long serialVersionUID = 1L;
    /**
    * 驗證類型 1：金融驗證2：本人本行信用卡
    */
    @NotEmpty
    private Integer authType;
    /**
    * 歸戶統編
    */
    @NotEmpty
    private String custId;
    /**
    * 卡號
    */
    @NotEmpty
    private String cardNo;
    /**
    * 有效日期 MMYY
    */
    @NotEmpty
    private String expirationDate;
    /**
    * 安全碼
    */
    @NotEmpty
    private String securityCode;
    /**
    * 電話
    */
    private String mobile;
    /**
    * 紀錄驗證結果類別 1：開戶 2：辦卡(無值代表不紀錄驗證結果)
    */
    private String logType;
    /**
    * 申請案件編號 (開戶才需填入)
    */
    private String applyCaseNo;
    /**
    * 驗證客戶類型 (開戶才需填入)1：開戶申請人2：法定代理人
    */
    private Integer authCustType;
    /**
    * 法定代理人編號 (開戶才需填入)1：法定代理人12：法定代理人2
    */
    private Integer reptNo;
}
```

```java
package com.ytb.ibmb.business.xyz.model;

import io.swagger.v3.oas.annotations.OpenAPIDescription;
import lombok.Getter;
import lombok.Setter;
import java.io.Serializable;
import java.time.LocalDateTime;

/**
* <pre>
* ValidateCardValidityModel 檢核信用卡有效性
* </pre>
*/
@OpenAPIDescription("檢核信用卡有效性")
@Getter
@Setter
public class ValidateCardValidityModel implements Serializable {
    /** serialVersionUID */
    private static final long serialVersionUID = 1L;
    /**
    * 驗證結果 0：驗證失敗1：驗證成功
    */
    private Integer authResult;
    /**
    * 驗證失敗原因 (※[Rs.authResult]=“0”才會回傳此欄位)
    */
    private String authFailReason;
    /**
    * 记錄(以下為一到多筆)
    */
    private List<ValidateCardValidityModelRecord> records;
}
```

```java
package com.ytb.ibmb.business.xyz.model;

import io.swagger.v3.oas.annotations.OpenAPIDescription;
import lombok.Getter;
import lombok.Setter;
import java.io.Serializable;

/**
* <pre>
* ValidateCardValidityModelRecord 檢核信用卡有效性
* </pre>
*/
@OpenAPIDescription("檢核信用卡有效性")
@Getter
@Setter
public class ValidateCardValidityModelRecord implements Serializable {
    /** serialVersionUID */
    private static final long serialVersionUID = 1L;
    /**
    * 分期計畫代碼
    */
    private String programCode;
    /**
    * 分期計畫代碼說明
    */
    private String programDesc;
    /**
    * 分期期數
    */
    private Integer installmentTerm;
    /**
    * 分期手續費
    */
    private BigDecimal fee;
    /**
    * 分期利率
    */
    private BigDecimal rate;
    /**
    * 首期應繳金額
    */
    private BigDecimal downPayment;
    /**
    * 分期總利息
    */
    private BigDecimal totalInterest;
    /**
    * 上次交易日期
    */
    private LocalDate lastPayDate;
}
```
