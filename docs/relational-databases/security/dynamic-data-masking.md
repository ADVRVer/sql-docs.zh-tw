---
title: "動態資料遮罩 | Microsoft Docs"
ms.custom: 
ms.date: 09/26/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: security
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a62f4ff9-2953-42ca-b7d8-1f8f527c4d66
caps.latest.revision: 41
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.translationtype: HT
ms.sourcegitcommit: d9a995f7d29fe91e14affa9266a9bce73acc9010
ms.openlocfilehash: 6ea14b40f988028a714323bc4e35fcd7a357e27c
ms.contentlocale: zh-tw
ms.lasthandoff: 09/27/2017

---
# <a name="dynamic-data-masking"></a>動態資料遮罩
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

![動態資料遮罩](../../relational-databases/security/media/dynamic-data-masking.png)

動態資料遮罩 (DDM) 會對不具權限的使用者遮罩機密資料，從而限制其曝光。 它可用來大幅簡化您的應用程式中安全性的設計和編碼。  

動態資料遮罩讓使用者能夠指定要顯示多少機密資料，藉此協助防止未經授權存取機密資料，同時盡可能減少對應用程式層的影響。 可以在資料庫上設定 DDM，隱藏在指定資料庫欄位查詢結果集內的機密資料，而資料庫中的資料則不會變更。 在現有應用程式使用動態資料遮罩相當容易，原因是遮罩規則已套用到查詢結果中。 許多應用程式都不需要修改現有查詢，就能遮罩機密資料。

* 中央資料遮罩原則可直接作用於資料庫中的機密欄位上。
* 指定無法存取敏感性資料之特殊權限的使用者或角色。
* DDM 的特色在於完整遮罩和部分遮罩功能，以及數值資料的隨機遮罩。
* 簡單的 [!INCLUDE[tsql_md](../../includes/tsql-md.md)] 命令可定義和管理遮罩。

例如，話務中心支援人員可以從來電者的社會安全號碼或信用卡號碼其中幾個數字加以識別，但這些資料項目都不應該完全對支援人員曝光。 此時可以定義遮罩規則，使其遮罩任何查詢結果集內的任何社會安全號碼或信用卡號碼，只顯示最後四碼。 另一個例子是，開發人員可以使用適當的資料遮罩保護個人識別資訊 (PII) 資料，為疑難排解目的查詢生產環境，而不會違反法務遵循規定。

 動態資料遮罩的目的在於限制機密限制的曝光，防止不該存取資料的使用者檢視該資料。 動態資料遮罩並不是用來防止資料庫使用者直接連接到資料庫，以及執行會讓機密資料片段曝光的全面查詢。 動態資料遮罩旨在補足其他 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安全性功能 (稽核、加密、資料列層級安全性…)，強烈建議您額外搭配這些功能使用此功能，讓資料庫中的敏感性資料獲得更妥善的保護。  
  
 動態資料遮罩提供於 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 和 [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)]，並且使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 命令來設定。 如需使用 Azure 入口網站設定動態資料遮罩的其他資訊，請參閱 [開始使用 SQL Database 動態資料遮罩 (Azure 入口網站)](http://azure.microsoft.com/documentation/articles/sql-database-dynamic-data-masking-get-started/)。  
  
## <a name="defining-a-dynamic-data-mask"></a>定義動態資料遮罩  
 您可以在資料庫中的資料行定義遮罩規則，以模糊該資料行中的資料。 遮罩有四種類型。  
  
|函數|描述|範例|  
|--------------|-----------------|--------------|  
|預設值|請依據指定欄位的資料類型進行完整遮罩。<br /><br /> 對於字串資料類型，請使用 XXXX，或在欄位大小少於 4 個字元時使用較少的 X (**char**、**nchar**、**varchar**、**nvarchar**、**text**、**ntext**)。  <br /><br /> 對於數值資料類型，請使用零值 (**bigint**、**bit**、**decimal**、**int**、**money****numeric****smallint**、**smallmoney**、**tinyint**、**float**、**real**)。<br /><br /> 對於日期與時間資料類型，請使用 01.01.1900 00:00:00.0000000 (**date**、**datetime2**、**datetime**、**datetimeoffset**、**smalldatetime**、**time**)。<br /><br />對於二進位資料類型，請使用單一位元組的 ASCII 值 0 (**binary**、 **varbinary**、 **image**)。|範例資料行定義語法： `Phone# varchar(12) MASKED WITH (FUNCTION = 'default()') NULL`<br /><br /> 範例替代語法： `ALTER COLUMN Gender ADD MASKED WITH (FUNCTION = 'default()')`|  
|Email|此遮罩方法可讓電子郵件地址的第一個字母和常數後置詞 ".com" 曝光，形式為電子郵件地址。 。 `aXXX@XXXX.com`。|範例定義語法： `Email varchar(100) MASKED WITH (FUNCTION = 'email()') NULL`<br /><br /> 範例替代語法： `ALTER COLUMN Email ADD MASKED WITH (FUNCTION = 'email()'`)|  
|隨機|此隨機遮罩函數可用在任何數值類型，會以指定範圍內隨機的值遮罩原始值。|範例定義語法： `Account_Number bigint MASKED WITH (FUNCTION = 'random([start range], [end range])')`<br /><br /> 範例替代語法： `ALTER COLUMN [Month] ADD MASKED WITH (FUNCTION = 'random(1, 12)')`|  
|自訂字串|此遮罩方法會讓第一個及最後一個字母曝光，並在中間加入自訂填補字串。 `prefix,[padding],suffix`<br /><br /> 注意：如果原始的值過短，而無法完成整個遮罩，一部分的前置詞或後置詞就不會曝光。|範例定義語法： `FirstName varchar(100) MASKED WITH (FUNCTION = 'partial(prefix,[padding],suffix)') NULL`<br /><br /> 範例替代語法： `ALTER COLUMN [Phone Number] ADD MASKED WITH (FUNCTION = 'partial(1,"XXXXXXX",0)')`<br /><br /> 其他範例：<br /><br /> `ALTER COLUMN [Phone Number] ADD MASKED WITH (FUNCTION = 'partial(5,"XXXXXXX",0)')`<br /><br /> `ALTER COLUMN [Social Security Number] ADD MASKED WITH (FUNCTION = 'partial(0,"XXX-XX-",4)')`|  
  
## <a name="permissions"></a>Permissions  
 您不需要任何特殊權限，只要有結構描述的標準 **CREATE TABLE** 和 **ALTER** 權限，就能建立含有動態資料遮罩的資料表。  
  
 新增、取代或移除資料行遮罩則需要資料表的 **ALTER ANY MASK** 權限和 **ALTER** 權限。 將 **ALTER ANY MASK** 授與資訊安全人員是適當作法。  
  
 具有資料表 **SELECT** 權限的使用者可以檢視資料表資料。 定義為已遮罩的資料行會顯示遮罩的資料。 請將 **UNMASK** 權限授與使用者，使其能夠從已定義遮罩的資料行擷取未遮罩的資料。  
  
 資料庫的 **CONTROL** 權限同時包括 **ALTER ANY MASK** 和 **UNMASK** 權限。  
  
## <a name="best-practices-and-common-use-cases"></a>最佳做法與常見使用案例  
  
-   在資料行建立遮罩並不會防止該資料行更新。 所以儘管使用者在查詢遮罩資料行時會收到遮罩的資料，相同的使用者還是可在具有寫入權限時更新資料。 您仍應使用適當的存取控制原則來限制更新權限。  
  
-   使用 `SELECT INTO` 或 `INSERT INTO` 將資料從遮罩的資料行複製到另一個資料表，會讓資料在目標資料表中也有遮罩。  
  
-   執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 匯入與匯出時會套用動態資料遮罩。 包含遮罩資料行的資料庫會導致備份檔案含有遮罩資料 (假設檔案是由不具 **UNMASK** 權限的使用者所匯出)，匯入的資料庫則會包含靜態遮罩的資料。  
  
## <a name="querying-for-masked-columns"></a>查詢遮罩的資料行  
 使用 **sys.masked_columns** 檢視來查詢已套用遮罩函數的資料表資料行。 此檢視繼承自 **sys.columns** 檢視。 它會傳回 **sys.columns** 檢視中的所有資料行，加上 **is_masked** 和 **masking_function** 資料行，指出資料行是否已遮罩，若已遮罩，則指出定義了哪個遮罩函數。 此檢視只會顯示已套用遮罩函數的資料行。  
  
```  
SELECT c.name, tbl.name as table_name, c.is_masked, c.masking_function  
FROM sys.masked_columns AS c  
JOIN sys.tables AS tbl   
    ON c.[object_id] = tbl.[object_id]  
WHERE is_masked = 1;  
```  
  
## <a name="limitations-and-restrictions"></a>限制事項  
 下列資料行類型無法定義遮罩規則：  
  
-   加密資料行 (永遠加密)  
  
-   FILESTREAM  
  
-   COLUMN_SET 或屬於疏鬆資料行集的資料行。  
  
-   在計算資料行上無法設定遮罩，但如果計算資料行相依於具有 MASK 的資料行，計算資料行就會傳回遮罩的資料。  
  
-   有資料遮罩的資料行不能是 FULLTEXT 索引的索引鍵。  
  
 對於不具 **UNMASK** 權限的使用者，已遭取代的 **READTEXT**、 **UPDATETEXT**和 **WRITETEXT** 陳述式在為動態資料遮罩設定的資料行上無法正常作用。 
 
 新增動態資料遮罩會實作為基礎資料表上的結構描述變更，因此無法在具有相依性的資料行上執行。 若要暫時解決這項限制，您可以先移除相依性，並新增動態資料遮罩，然後重新建立相依性。 例如，如果相依性是基於相依於該資料行索引，則您可以卸除索引，並新增遮罩，然後重新建立相依索引。
 

## <a name="security-note-bypassing-masking-using-inference-or-brute-force-techniques"></a>安全性注意事項︰使用推斷或暴力破解方法略過遮罩

動態資料遮罩的設計是要藉由限制應用程式所使用之預先定義查詢集的資料曝光，簡化應用程式開發。 雖然動態資料遮罩也可以用來避免在直接存取生產資料庫時意外洩露機密資料，您必須特別注意具有特定查詢權限的無特殊權限使用者，可以套用技術以存取實際的資料。 如果需要授與這類特定存取權，應該使用稽核來監視所有的資料庫活動，並減輕這種情況。
 
例如，請考慮資料庫主體具有足夠的權限對資料庫執行特定查詢，並嘗試猜測基礎資料，最終推斷實際的值。 假設我們在 `[Employee].[Salary]` 資料行上定義了遮罩，而這位使用者直接連接到資料庫並開始猜測值，最後推斷一組員工的 `[Salary]` 值︰
 

```
SELECT ID, Name, Salary FROM Employees
WHERE Salary > 99999 and Salary < 100001;
```

>    |  Id | 名稱| Salary |   
>    | ----- | ---------- | ------ | 
>    |  62543 | Jane Doe | 0 | 
>    |  91245 | John Smith | 0 |  

此示範了動態資料遮罩不應該用來作為隔離的措施，完全保護機密資料不受對資料庫執行特定查詢的使用者存取。 它適合防止機密資料不慎洩露，但無法防止惡意推斷基礎資料。
 
務必要正確管理資料庫的權限，並隨時遵守最小必要權限的原則。 此外，請記得啟用稽核來追蹤資料庫上發生的所有活動。

  
## <a name="examples"></a>範例  
  
### <a name="creating-a-dynamic-data-mask"></a>建立動態資料遮罩  
 下列範例將建立有三種不同動態資料遮罩類型的資料表。 範例會填入資料表，並選擇顯示結果。  
  
```  
CREATE TABLE Membership  
  (MemberID int IDENTITY PRIMARY KEY,  
   FirstName varchar(100) MASKED WITH (FUNCTION = 'partial(1,"XXXXXXX",0)') NULL,  
   LastName varchar(100) NOT NULL,  
   Phone# varchar(12) MASKED WITH (FUNCTION = 'default()') NULL,  
   Email varchar(100) MASKED WITH (FUNCTION = 'email()') NULL);  
  
INSERT Membership (FirstName, LastName, Phone#, Email) VALUES   
('Roberto', 'Tamburello', '555.123.4567', 'RTamburello@contoso.com'),  
('Janice', 'Galvin', '555.123.4568', 'JGalvin@contoso.com.co'),  
('Zheng', 'Mu', '555.123.4569', 'ZMu@contoso.net');  
SELECT * FROM Membership;  
```  
  
 新的使用者已建立，並已授與資料表的 **SELECT** 權限。 在 `TestUser` 檢視遮罩資料時執行了查詢。  
  
```  
CREATE USER TestUser WITHOUT LOGIN;  
GRANT SELECT ON Membership TO TestUser;  
  
EXECUTE AS USER = 'TestUser';  
SELECT * FROM Membership;  
REVERT;  
```  
  
 結果會顯示遮罩，方法是將資料從  
  
 `1    Roberto     Tamburello    555.123.4567    RTamburello@contoso.com`  
  
 into  
  
 `1    RXXXXXXX    Tamburello    xxxx            RXXX@XXXX.com`  
  
### <a name="adding-or-editing-a-mask-on-an-existing-column"></a>在現有資料行上新增或編輯遮罩  
 使用 **ALTER TABLE** 陳述式將遮罩加入資料表的現有資料行中，或在該資料行編輯遮罩。  
以下範例會將遮罩函數加入 `LastName` 資料行中：  
  
```  
ALTER TABLE Membership  
ALTER COLUMN LastName ADD MASKED WITH (FUNCTION = 'partial(2,"XXX",0)');  
```  
  
 以下範例會變更 `LastName` 資料行的遮罩函數：  
  
```  
ALTER TABLE Membership  
ALTER COLUMN LastName varchar(100) MASKED WITH (FUNCTION = 'default()');  
```  
  
### <a name="granting-permissions-to-view-unmasked-data"></a>授與權限以檢視未遮罩的資料  
 授與 **UNMASK** 權限可讓 `TestUser` 看見未遮罩的資料。  
  
```  
GRANT UNMASK TO TestUser;  
EXECUTE AS USER = 'TestUser';  
SELECT * FROM Membership;  
REVERT;   
  
-- Removing the UNMASK permission  
REVOKE UNMASK TO TestUser;  
```  
  
### <a name="dropping-a-dynamic-data-mask"></a>卸除動態資料遮罩  
 以下陳述式會卸除先前範例中在 `LastName` 資料行建立的遮罩：  
  
```  
ALTER TABLE Membership   
ALTER COLUMN LastName DROP MASKED;  
```  
  
## <a name="see-also"></a>另請參閱  
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [column_definition &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-column-definition-transact-sql.md)   
 [sys.masked_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-masked-columns-transact-sql.md)   
 [開始使用 SQL 資料庫動態資料遮罩 (Azure Preview 入口網站)](http://azure.microsoft.com/documentation/articles/sql-database-dynamic-data-masking-get-started/)  
  
  

