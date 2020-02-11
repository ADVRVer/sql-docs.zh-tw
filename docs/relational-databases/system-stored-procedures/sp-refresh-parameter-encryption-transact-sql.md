---
title: sp_refresh_parameter_encryption （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 01/11/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sp_refresh_parameter_encryption
- sp_refresh_parameter_encryption_TSQL
- sys.sp_refresh_parameter_encryption
- sys.sp_refresh_parameter_encryption_TSQL
helpviewer_keywords:
- sp_refresh_parameter_encryption
- Always Encrypted, sp_refresh_parameter_encryption
ms.assetid: 00b44baf-fcf0-4095-aabe-49fa87e77316
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: a5f699f21b1f28537da2e2f0033fe6b17908186a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68002458"
---
# <a name="sp_refresh_parameter_encryption-transact-sql"></a>sp_refresh_parameter_encryption （Transact-sql）
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

更新目前資料庫中指定非架構系結預存程式、使用者定義函數、view、DML 觸發程式、資料庫層級 DDL 觸發程式或伺服器層級 DDL 觸發程式之參數的 Always Encrypted 中繼資料。 

 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
sys.sp_refresh_parameter_encryption [ @name = ] 'module_name' 
    [ , [ @namespace = ] '<class>' ]
[ ; ]

<class> ::=
{ DATABASE_DDL_TRIGGER | SERVER_DDL_TRIGGER }
```

## <a name="arguments"></a>引數

`[ @name = ] 'module_name'`這是預存程式、使用者定義函數、view、DML 觸發程式、資料庫層級 DDL 觸發程式或伺服器層級 DDL 觸發程式的名稱。 *module_name*不可以是 common language RUNTIME （CLR）預存程式或 CLR 函數。 *module_name*不可以是架構系結。 *module_name*是`nvarchar`，沒有預設值。 *module_name*可以是多部分的識別碼，但只能參考目前資料庫中的物件。

`[ @namespace = ] ' < class > '`這是指定之模組的類別。 當*module_name*是 DDL 觸發程式時`<class>` ，則為必要。 
  `<class>` 為 `nvarchar(20)`。 有效的輸入`DATABASE_DDL_TRIGGER`為`SERVER_DDL_TRIGGER`和。    

## <a name="return-code-values"></a>傳回碼值  

0 (成功) 或非零數字 (失敗)


## <a name="remarks"></a>備註

模組的參數加密中繼資料可能會過時，如果：   
* 模組參考之資料表中資料行的加密屬性已更新。 例如，已經卸載資料行，而且已新增不同的加密類型、加密金鑰或加密演算法的新資料行。  
* 模組參考了具有過期參數加密中繼資料的另一個模組。  

修改資料表的加密屬性時， `sp_refresh_parameter_encryption`應該直接或間接參考該資料表的任何模組執行。 這個預存程式可以依任何順序在那些模組上呼叫，而不需要使用者先重新整理內部模組，再移至其呼叫端。

`sp_refresh_parameter_encryption`不會影響與物件相關聯的任何許可權`SET` 、擴充屬性或選項。 

若要重新整理伺服器層級 DDL 觸發程序，請從任何資料庫的內容執行此預存程序。

> [!NOTE]
>  當您執行`sp_refresh_parameter_encryption`時，會卸載與物件相關聯的任何簽章。

## <a name="permissions"></a>權限

需要`ALTER`模組的許可權，以及`REFERENCES`物件所參考之任何 CLR 使用者自訂類型和 XML 架構集合的許可權。   

當指定的模組是資料庫層級 DDL 觸發程式時， `ALTER ANY DATABASE DDL TRIGGER`需要目前資料庫的許可權。    

當指定的模組是伺服器層級 DDL 觸發程式時， `CONTROL SERVER`需要許可權。

對於以`EXECUTE AS`子句定義的模組， `IMPERSONATE`指定的主體上必須有許可權。 一般而言，重新整理物件並不會變更`EXECUTE AS`其主體，除非模組是使用`EXECUTE AS USER`所定義，而且主體的使用者名稱現在會解析為與建立模組時不同的使用者。
 
## <a name="examples"></a>範例

下列範例會建立資料表和參考資料表的程式，設定 Always Encrypted，然後示範如何改變數據表並`sp_refresh_parameter_encryption`執行程式。  

首先，建立初始資料表和參考資料表的預存程式。
```sql
CREATE TABLE [Patients]([PatientID] [int] IDENTITY(1,1) NOT NULL,
    [SSN] [char](11), 
    [FirstName] [nvarchar](50) NULL,
    [LastName] [nvarchar](50) NOT NULL,
    [MiddleName] [nvarchar](50) NULL,
    [StreetAddress] [nvarchar](50) NOT NULL,
    [City] [nvarchar](50) NOT NULL,
    [ZipCode] [char](5) NOT NULL,
    [State] [char](2) NOT NULL,
    [BirthDate] [date] NOT NULL,
 CONSTRAINT [PK_Patients] PRIMARY KEY CLUSTERED 
(
    [PatientID] ASC
) WITH 
    (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, 
     IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, 
     ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY];
GO

CREATE PROCEDURE [find_patient] @SSN [char](11)
AS
BEGIN
    SELECT * FROM [Patients] WHERE SSN=@SSN
END;
GO
```

然後設定 Always Encrypted 金鑰。
```sql
CREATE COLUMN MASTER KEY [CMK1]
WITH
(
       KEY_STORE_PROVIDER_NAME = N'MSSQL_CERTIFICATE_STORE',
    KEY_PATH = N'CurrentUser/my/A66BB0F6DD70BDFF02B62D0F87E340288E6F9305'
);
GO

CREATE COLUMN ENCRYPTION KEY [CEK1]
WITH VALUES
(
       COLUMN_MASTER_KEY = [CMK1],
    ALGORITHM = 'RSA_OAEP',
    ENCRYPTED_VALUE = 
       0x016E000001630075007200720065006E00740075007300650072002F006D0079002F006100360036006200620030006600360064006400370030006200640066006600300032006200360032006400300066003800370065003300340030003200380038006500360066003900330030003500CA0D0CEC74ECADD1804CF99137B4BD06BBAB15D7EA74E0C249A779C7768A5B659E0125D24FF827F5EA8CA517A8E197ECA1353BA814C2B0B2E6C8AB36E3AE6A1E972D69C3C573A963ADAB6686CF5D24F95FE43140C4F9AF48FBA7DF2D053F3B4A1F5693A1F905440F8015BDB43AF8A04BE4E045B89876A0097E5FBC4E6A3B9C3C0D278C540E46C53938B8C957B689C4DC095821C465C73117CBA95B758232F9E5B2FCC7950B8CA00AFE374DE42847E3FBC2FDD277035A2DEF529F4B735C20D980073B4965B4542A34723276A1646998FC6E1C40A3FDB6ABCA98EE2B447F114D2AC7FF8C7D51657550EC5C2BABFFE8429B851272086DCED94332CF18FA854C1D545A28B1EF4BE64F8E035175C1650F6FC5C4702ACF99850A4542B3747EAEC0CC726E091B36CE24392D801ECAA684DE344FECE05812D12CD72254A014D42D0EABDA41C89FC4F545E88B4B8781E5FAF40D7199D4842D2BFE904D209728ED4F527CBC169E2904F6E711FF81A8F4C25382A2E778DD2A58552ED031AFFDA9D9D891D98AD82155F93C58202FC24A77F415D4F8EF22419D62E188AC609330CCBD97CEE1AEF8A18B01958833604707FDF03B2B386487CC679D7E352D0B69F9FB002E51BCD814D077E82A09C14E9892C1F8E0C559CFD5FA841CEF647DAB03C8191DC46B772E94D579D8C80FE93C3827C9F0AE04D5325BC73111E07EEEDBE67F1E2A73580085
);
GO
```


最後，我們會將 SSN 資料行取代為加密的資料行， `sp_refresh_parameter_encryption`然後執行程式來更新 Always Encrypted 的元件。
```sql
ALTER TABLE [Patients] DROP COLUMN [SSN];
GO

ALTER TABLE [Patients] 
    ADD [SSN] [char](11) COLLATE Latin1_General_BIN2 
    ENCRYPTED WITH 
        (COLUMN_ENCRYPTION_KEY = [CEK1], 
        ENCRYPTION_TYPE = Deterministic, 
        ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') 
    NOT NULL;
GO

EXEC sp_refresh_parameter_encryption [find_patient];
GO
```

## <a name="see-also"></a>另請參閱 

[Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
[Always Encrypted Wizard](../../relational-databases/security/encryption/always-encrypted-wizard.md)   

