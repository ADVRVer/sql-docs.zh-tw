---
title: 專案設定 （轉換） (SybaseToSQL) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: eeb80fa5-f530-4f21-beee-25f5a4b8ace6
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 4d7f290459e1da736605acad941602399ec3ea53
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "62664660"
---
# <a name="project-settings-conversion-sybasetosql"></a>專案設定 (轉換) (SybaseToSQL)
[轉換] 頁面**專案設定** 對話方塊中包含自訂 SSMA 如何轉換 Sybase Adaptive Server Enterprise (ASE) 語法來設定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]或 SQL Azure 的語法。  
  
[轉換] 窗格位於**專案設定**並**預設專案設定**對話方塊：  
  
-   如果您想要在指定所有的 SSMA 專案設定**工具**功能表上，選取**預設專案設定**，按一下 **一般**在底部的左的窗格中，然後按一下**轉換**。  
  
-   若要指定目前的專案中，設定**工具**功能表上，選取**專案設定**，按一下 **一般**底部的左窗格中，然後按一下  **轉換**。  
  
## <a name="miscellaneous-options"></a>其他選項  
**@@ERROR**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure 和 ASE 會使用不同的錯誤碼。  
  
使用此設定可指定類型的訊息 （「 警告 」 或 「 錯誤 」），在 [輸出] 或 [錯誤清單] 窗格中遇到的參考時顯示的 SSMA **@@ERROR**  ASE 程式碼中。  
  
-   如果您選取**轉換，並以警告標記**，SSMA 會轉換這些陳述式，並將它們標示的警告註解。  
  
-   如果您選取**含有錯誤標示**，SSMA 會跳過轉換和標記陳述式與錯誤註解。  
  
當您選取的轉換模式**模式** 方塊中，SSMA 會套用下列設定：  
  
**預設/開放式模式：** 轉換，並以警告標記  
  
**完整模式：** 以錯誤標記  
  
**LIKE 運算子的轉換**  
指定是否要轉換運算元，以符合 Sybase ASE 的行為類似。 重點是 Sybase 會修剪尾端空格的 like 模式。 因應措施是運算式的對最大有效位數的固定的長度資料類型進行轉換的右邊。  
  
-   選取 **簡單的轉換**来轉換的運算式，而不需要任何更正。  
  
-   若要使用 ASE 行為選取**轉換成固定長度。**  
  
當您在 [模式] 方塊中選取轉換模式時，SSMA 會套用下列設定：  
  
**預設/開放式模式**:簡單的轉換  
  
**完整模式**:轉換成固定長度  
  
**轉換或轉型為數字類型的空字串**  
指定如何處理空的或空白字串做為資料型別引數的數值類型的 CONVERT 或 CAST 運算式內。 此設定有下列選項：  
  
-   選取 **簡單的轉換**来轉換的運算式，而不需要任何更正。  
  
-   如果**空字串為零的數字**已選取，則字串參數 {s} 將取代案例 ltrim(rtrim({s})) 時 「 」 然後 0 else {s} 結束運算式  
  
當您在 [模式] 方塊中選取轉換模式時，SSMA 會套用下列設定：  
  
**預設/開放式模式**:簡單的轉換  
  
**完整模式**:以零數值的空字串  
  
**NULL 串連**  
此設定會指定如何將轉換與 NULL 串連的字串。 針對此特定的設定，就可以設定下列選項：  
  
-   **換行 ISNULL 函數：** 如果設定此選項時，每個非常 'string_expression' 中串連會包裝與 ISNULL(string_expression) 和 Null 將會取代為空字串。  
  
-   **保留目前的語法**  
  
當您選取的轉換模式**模式** 方塊中，SSMA 會套用下列設定：  
  
**預設/開放式模式：** 保留目前的語法  
  
**完整模式：** 換行 ISNULL 函數  
  
**空字串轉換**  
此設定會指定如何將空字串轉換。 針對此特定的設定，就可以設定下列選項：  
  
-   **以空格取代所有字串運算式**  
  
-   **以空格取代空的字串常數**  
  
-   若要使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure 的行為，選取**保留目前的語法**。  
  
當您選取的轉換模式**模式** 方塊中，SSMA 會套用下列設定：  
  
**預設/開放式模式：** 保留目前的語法  
  
**完整模式：** 以空格取代所有字串運算式  
  
**轉換和轉換的二進位字串轉換**  
數字的二進位值轉換可以在不同的平台上傳回不同的值。 例如，在 x86 處理器，CONVERT (integer，0x00000100) 會傳回在 ASE 中的 65536，以及使用中的 256 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 此外，ASE 也會傳回位元組順序而異。  
  
使用此設定，來控制如何 SSMA 會將轉換的轉換和包含二進位值的 CASE 運算式：  
  
-   選取 **簡單的轉換**轉換沒有任何警告或修正的運算式。 如果您知道 ASE 伺服器已不需要任何變更的二進位值的位元組順序，請使用此設定。  
  
-   選取 **轉換，並更正**能夠轉換，並更正用於運算式上的 SSMA [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 常值常數的位元組順序會反轉。 將標示 （例如二進位變數和資料行） 的其他所有二進位值，但發生錯誤。 如果您知道 ASE 伺服器有需要變更為二進位值的位元組順序，請使用此值。  
  
-   選取 **轉換，並以警告標記**有 SSMA 轉換並更正運算式，並標示所有轉換的警告註解的運算式。  
  
當您選取的轉換模式**模式** 方塊中，SSMA 會套用下列設定：  
  
**預設模式：** 轉換，並以警告標記  
  
**開放式的模式：** 簡單的轉換  
  
**完整模式：** 轉換並更正  
  
**動態 SQL**  
您可以使用此設定來指定 SSMA 在遇到 ASE 程式碼中的動態 SQL 時，要顯示在 [輸出] 或 [錯誤清單] 窗格中的訊息 （「 警告 」 或 「 錯誤 」） 的類型。  
  
-   如果您選取**轉換，並以警告標記**，SSMA 會轉換動態 SQL，並將標示的警告註解的陳述式。  
  
-   如果您選取**含有錯誤標示**，SSMA 會跳過轉換和標記陳述式與錯誤註解。  
  
當您選取的轉換模式**模式** 方塊中，SSMA 會套用下列設定：  
  
**預設/開放式模式：** 轉換，並以警告標記  
  
**完整模式：** 以錯誤標記  
  
**等號比較檢查轉換**  
在  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure，如果的 ANSI_NULLS 設定為 on， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ 任何相等比較包含 null 值時，SQL Azure 會傳回 UNKNOWN。 如果 ANSI_NULLS 是 off 時，包含 null 值的相等比較，則為 true 時傳回相比較的資料行和運算式或兩個運算式都是 null。 預設值 （ANSINULL 關閉） Sybase ASE 等號比較行為類似[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure 以 ANSI_NULLS OFF。  
  
-   如果您選取**簡單的轉換**，SSMA 會將轉換的 ASE 程式碼[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure 的語法，而不需額外的檢查 null 值。 如果 ANSI_NULLS 是 off，在使用這個設定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure，或如果您想要修改每個案例為基礎的相等比較。  
  
-   如果您選取**考慮 NULL 值**，SSMA 會藉由使用 IS NULL 和 IS NOT NULL 子句新增檢查 null 值。  
  
當您選取的轉換模式**模式** 方塊中，SSMA 會套用下列設定：  
  
**預設/開放式模式：** 簡單的轉換  
  
**完整模式：** 請考慮 NULL 值  
  
**格式字串**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure 不會再支援*format_string* PRINT 和 RAISERROR 陳述式中的引數。 *Format_string*變數支援直接在字串中，將可置換的參數，並且將在執行階段參數。 相反地，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用字串常值或建置使用變數的字串中需要完整的字串。 如需詳細資訊，請參閱 「 列印 ( [!INCLUDE[tsql](../../includes/tsql-md.md)]) 」 中的主題[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]線上叢書 》。  
  
當遇到 SSMA *format_string*引數，它可以建置字串常值使用的變數或建立新的變數並建立使用該變數的字串。  
  
-   若要使用 PRINT 和 RAISERROR 函式的字串常值，請選取**建立新的字串**。  
  
    在此模式中，如果 PRINT 或 RAISERROR 陳述式不會使用預留位置和本機變數、 陳述式不變。 雙百分比字元 （%）會變更為單一的百分比字元 %列印字串常值中。  
  
    如果 PRINT 或 RAISERROR 陳述式會使用預留位置和一個或多個本機變數，如下列範例所示：  
  
    ```  
    PRINT 'Total: %1!%%', @percent  
    ```  
    SSMA 會將它轉換成下列語法：  
  
    ```  
    PRINT 'Total: '+ CAST(@percent AS varchar(max)) + '%'  
    ```  
    如果*format_string*是變數，例如，下列陳述式中：  
  
    ```  
    PRINT @fmt, @arg1, @arg2  
    ```  
    SSMA 會無法執行簡單的字串轉換，並必須建立新的變數：  
  
    ```  
    DECLARE @print_format_1 varchar(max)  
    SET @print_format_1  =   
        REPLACE (@fmt, '%%', '%')  
    SET @print_format_1  =   
        REPLACE (@print_format_1, '%1!',   
        CAST (@arg1 AS varchar(max)))  
    SET @print_format_1  =   
        REPLACE (@print_format_1, '%2!',   
        CAST (@arg2 AS varchar(max)))  
    PRINT @print_format_1  
    ```  
    當使用**建立新的字串**模式中，SSMA 假設[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]選項 CONCAT_NULL_YIELDS_NULL 為 OFF。 因此，SSMA 不會檢查 null 引數。  
  
-   若要建置新的變數，每個 PRINT 和 RAISERROR 陳述式，並再將該變數用於字串值的 SSMA，請選取**建立新的變數**。  
  
    在此模式中，如果 PRINT 或 RAISERROR 陳述式不會使用預留位置和區域變數，SSMA 會取代所有雙百分比字元 （%）使用單一的百分比字元來遵守[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure 的語法。  
  
    如果 PRINT 或 RAISERROR 陳述式會使用預留位置和一個或多個本機變數，如下列範例所示：  
  
    ```  
    PRINT 'Total: %1!%%', @percent  
    ```  
    SSMA 會將它轉換成下列語法：  
  
    ```  
    DECLARE @print_format_1 varchar(max)  
    SET @print_format_1 = 'Total: %1!%'  
    SET @print_format_1  =   
        REPLACE (@print_format_1, '%1!',   
        ISNULL(CAST (@percent AS VARCHAR(max)), ''))  
    PRINT @print_format_1  
    ```  
    如果*format_string*是變數，例如，下列陳述式中：  
  
    ```  
    PRINT @fmt, @arg1, @arg2  
    ```  
    SSMA 會建立新的變數，如下所示，檢查每個引數中的 null 值：  
  
    ```  
    DECLARE @print_format_1 varchar(max)  
    SET @print_format_1  =   
        REPLACE (@fmt, '%%', '%')  
    SET @print_format_1  =   
        REPLACE (@print_format_1, '%1!',   
        ISNULL(CAST (@arg1 AS varchar(max)),''))  
    SET @print_format_1  =   
        REPLACE (@print_format_1, '%2!',   
        ISNULL(CAST (@arg2 AS varchar(max)),''))  
    PRINT @print_format_1  
    ```  
  
當您選取的轉換模式**模式** 方塊中，SSMA 會套用下列設定：  
  
**預設/開放式模式：** 建立新的字串  
  
**完整模式：** 建立新的變數  
  
**明確值插入 timestamp 資料行**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure 不支援外顯值插入 timestamp 資料行。  
  
-   若要排除的 INSERT 陳述式中的時間戳記資料行，請選取**排除資料行**。  
  
-   在 INSERT 陳述式中的時間戳記資料行是每次列印一則錯誤訊息，請選取**含有錯誤標示**。 在此模式中，INSERT 陳述式不會被轉換，系統會以錯誤的註解標示。  
  
當您選取的轉換模式**模式** 方塊中，SSMA 會套用下列設定：  
  
**預設/開放式模式：** 排除資料行  
  
**完整模式：** 以錯誤標記  
  
**儲存程序中所定義的暫存物件**  
此設定指定是否出現在程序的暫存物件定義應該儲存在來源中繼資料轉換期間。  
  
-   選取 **是**儲存至中繼資料。  
  
-   選取  **No**如果不需要存放物件。  
  
**預設/開放式模式：** 是  
  
**完整模式：** 否  
  
**Proxy 資料表轉換**  
指定是否 ASE proxy 資料表轉換成[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure 資料表或未轉換和程式碼會以錯誤的註解標記。  
  
-   選取 **轉換**來將 proxy 資料表轉換成一般的資料表。  
  
-   選取 **含有錯誤標示**只是將 proxy 資料表程式碼使用錯誤註解。  
  
當您選取的轉換模式**模式** 方塊中，SSMA 會套用下列設定：  
  
**預設/開放式/Full 模式：** 以錯誤標記  
  
**RAISERROR 基底的訊息數目**  
ASE 使用者訊息會儲存在每個資料庫。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用者的郵件會集中儲存並可透過**sys.messages**目錄檢視。 除了 ASE 使用者訊息開始 20000，但[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]開始 50001 的錯誤訊息。  
  
此設定會指定要新增要將它轉換成的 ASE 使用者訊息數目的數字[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用者訊息。 如果您[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]具有使用者訊息**sys.messages**目錄檢視中，您可能必須變更此數字較高的值。 這是讓轉換後的訊息數字未與現有的訊息編號衝突。  
  
請注意下列事項：  
  
-   ASE 中的訊息 17000 19999 的範圍是從 sysmessages 系統資料表並不會轉換。  
  
-   如果 RAISERROR 陳述式中參考的訊息編號為常數，SSMA 會將常數，以判斷新的使用者訊息數目的基底的訊息數目。  
  
-   如果變數或運算式所參考的訊息編號，SSMA 會建立中繼的本機變數。  
  
-   在開放式模式中，SSMA 假設[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]選項 CONCAT_NULL_YIELDS_NULL 已關閉，而且可為 null 的引數不會檢查。  
  
-   在完整模式中，SSMA 會檢查 null 引數。  
  
-   RAISERROR 與 ERRORDATA*清單*不會被轉換。  
  
當您選取的轉換模式**模式** 方塊中，SSMA 會套用下列設定：  
  
**預設/開放式/Full 模式：** 30001  
  
**系統物件**  
您可以使用此設定來指定 SSMA 在遇到使用 ASE 系統物件時，要顯示在 [輸出] 或 [錯誤清單] 窗格中的訊息 （「 警告 」 或 「 錯誤 」） 的類型。  
  
-   如果您選取**轉換，並以警告標記**，SSMA 會將轉換的系統物件的參考，並會標示警告註解的陳述式。  
  
-   如果您選取**含有錯誤標示**，SSMA 不會將轉換的系統物件的參考，並會將標示為使用錯誤註解的陳述式。  
  
當您選取的轉換模式**模式** 方塊中，SSMA 會套用下列設定：  
  
**預設/開放式模式：** 轉換，並以警告標記  
  
**完整模式：** 以錯誤標記  
  
**無法解析識別項**  
您可以使用此設定來指定 SSMA 會顯示在 [輸出] 或 [錯誤清單] 窗格中，當無法解析識別項的訊息 （「 警告 」 或 「 錯誤 」） 的類型。  
  
-   如果您選取**轉換，並以警告標記**，SSMA 會嘗試轉換無法解析識別項參考，並會標示警告註解的陳述式。  
  
-   如果您選取**含有錯誤標示**，SSMA 不會轉換無法解析識別項參考，並會將標示為使用錯誤註解的陳述式。  
  
當您選取的轉換模式**模式** 方塊中，SSMA 會套用下列設定：  
  
**預設/開放式模式：** 轉換，並以警告標記  
  
**完整模式：** 以錯誤標記  
  
## <a name="system-function-options"></a>系統函式選項  
**CHARINDEX 函式**  
在 ASE 中，則 CHARINDEX 會傳回 NULL，只有當輸入的所有運算式都是 NULL。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ 如果任何輸入的運算式為 NULL，SQL Azure 會傳回 NULL。  
  
-   若要使用 ASE 行為，請選取**Replace 函式**。 CHARINDEX 函式所有呼叫會使用 CHARINDEX_VARCHAR 或 CHARINDEX_NVARCHAR 根據傳遞的參數型別 （在中建立結構描述名稱 's2ss' 的使用者資料庫） 來模擬 Sybase ASE 行為的使用者定義函式的呼叫都取代。  
  
-   若要使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure 的行為，選取**保留目前的語法**。  
  
當您選取的轉換模式**模式** 方塊中，SSMA 會套用下列設定：  
  
**預設/開放式模式：** 保留目前的語法  
  
**完整模式：** 取代函式  
  
**DATALENGTH 函數**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] / SQL Azure 和 ASE 的單一空格的值時，DATALENGTH 函數所傳回的值不同。 在此情況下， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure 會傳回 0，ASE 會傳回 1。  
  
-   若要使用 ASE 行為，請選取**Replace 函式**。 若要模擬 Sybase ASE 行為的 CASE 運算式會替換 DATALENGTH 函式所有呼叫。  
  
-   若要使用預設值[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure 的行為，選取**保留目前的語法**。  
  
當您選取的轉換模式**模式** 方塊中，SSMA 會套用下列設定：  
  
**預設/開放式模式：** 保留目前的語法  
  
**完整模式：** 取代函式  
  
**INDEX_COL 函數**  
ASE 支援選擇性*user_id*引數，INDEX_COL 函式; 不過， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure 不支援這個引數。 如果您使用*user_id*引數，此函式不能轉換成[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure 的語法。  
  
-   若要使用 ASE 行為，請選取**Convert 函數**。 如果包含的程式碼*user_id*引數，SSMA 會顯示錯誤。  
  
-   若要顯示的錯誤訊息，每次在遇到該 INDEX_COL，請選取**含有錯誤標示**。 SSMA 會將轉換的函式的參考，並會將標示為錯誤的註解的陳述式。  
  
**預設/開放式/Full 模式：** 以錯誤標記  
  
**INDEX_COLORDER 函式**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure 並沒有 INDEX_COLORDER 系統函式。  
  
-   若要使用 ASE 行為，請選取**Convert 函數**。 INDEX_COLORDER 函式所有呼叫會使用相同的名稱 （結構描述名稱 's2ss' 下的使用者資料庫中建立） 的 INDEX_COLORDER 可模擬 Sybase ASE 行為的使用者定義函式的呼叫都取代。  
  
-   若要列印一則錯誤訊息，每次在遇到該 INDEX_COLORDER，請選取**含有錯誤標示**。 SSMA 會將轉換的函式的參考，並會將標示為錯誤的註解的陳述式。  
  
當您選取的轉換模式**模式** 方塊中，SSMA 會套用下列設定：  
  
**預設/開放式/Full 模式：** 以錯誤標記  
  
**LEFT 和 RIGHT 函式**  
左邊和右邊的函式在 Sybase 中行為不同負數長度參數。  
  
-   若要使用 ASE 行為，請選取**取代的函式**。 長度參數取代使用 CASE 運算式會傳回負數的值為 null。  
  
-   若要使用 SQL Server 行為，請選取**保留目前的語法**  
  
當您選取的轉換模式**模式** 方塊中，SSMA 會套用下列設定：  
  
**預設/開放式模式：** 保留目前的語法  
  
**完整模式：** 取代函式  
  
> [!NOTE]  
> 如果常值，而不是複雜運算式的長度參數，長度值會一律會取代 null，不論專案設定。  
  
**NEXT_IDENTITY 函式**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure 並沒有 NEXT_IDENTITY 系統函式。  
  
-   若要使用 ASE 行為，請選取**轉換的函式**。 NEXT_IDENTITY 函式所有呼叫都取代運算式 （IDENT_CURRENT(parameter Value) + IDENT_INCR(parameter Value) 可模擬 Sybase ASE 行為。  
  
-   若要列印一則錯誤訊息，每次在遇到該 NEXT_IDENTITY，請選取**含有錯誤標示**。 SSMA 會將轉換的函式的參考，並會將標示為錯誤的註解的陳述式。  
  
當您選取的轉換模式**模式** 方塊中，SSMA 會套用下列設定：  
  
**預設/開放式/Full 模式：** 以錯誤標記  
  
**PATINDEX 函式**  
指定是否要將轉換 PATINDEX 函式，以符合 Sybase ASE 的行為。 重點是 Sybase 會修剪尾端空格的搜尋模式。 因應措施是對型別轉換為固定長度資料類型最大有效位數，並套用 rtrim 函式可搜尋模式的值運算式。  
  
-   若要使用 ASE 行為 select**使用**。  
  
-   若要使用預設值[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure 的行為，選取**請勿使用**。  
  
當您選取的轉換模式**模式** 方塊中，SSMA 會套用下列設定：  
  
**預設/開放式模式：** 請勿使用  
  
**完整模式：** 使用  
  
**REPLICATE 函式**  
REPLICATE 函式會重複指定次數的字串。 在 ASE 中，如果您指定要重複字串多次，則結果為 null。 在  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure，結果為空字串。  
  
-   若要使用 ASE 行為，請選取**Replace 函式**。 複寫函式所有呼叫會使用 REPLICATE_VARCHAR 或 REPLICATE_NVARCHAR 根據傳遞的參數型別 （在中建立結構描述名稱 's2ss' 的使用者資料庫） 來模擬 Sybase ASE 行為的使用者定義函式的呼叫都取代。  
  
-   若要使用預設值[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure 的行為，選取**取代函式**。  
  
當您選取的轉換模式**模式** 方塊中，SSMA 會套用下列設定：  
  
**預設/開放式模式/Full 模式：** 取代函式  
  
**TRIM （LTRIM、 RTRIM） 函式**  
此設定指定是否將 Trim （LTRIM、 RTRIM） 函式的呼叫取代 Sybase ASE-對等項目語法函式，或保留目前的語法。 針對此特定的設定有下列選項：  
  
-   **取代函式**  
  
-   **保留目前的語法**  
  
當您選取的轉換模式**模式** 方塊中，SSMA 會套用下列設定：  
  
**預設/開放式模式/Full 模式：** 取代函式  
  
**SUBSTRING 函式**  
在 ASE 中，此函式`SUBSTRING(expression, start, length)`指定開始值大於運算式中的字元數，則長度會等於零，則傳回 NULL。 在  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure 對等的運算式會傳回空字串。  
  
-   若要使用 ASE 行為，請選取**Replace 函式**。 SUBSTRING 函式所有呼叫會使用 SUBSTRING_VARCHAR SUBSTRING_NVARCHAR 或 SUBSTRING_VARBINARY 傳遞 （結構描述名稱 's2ss' 的使用者資料庫中建立），來模擬的參數類型為基礎的使用者定義函式的呼叫都取代Sybase ASE 行為。  
  
-   若要使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure 的行為，選取**保留目前的語法**。  
  
當您選取的轉換模式**模式** 方塊中，SSMA 會套用下列設定：  
  
**預設/開放式模式：** 保留目前的語法  
  
**完整模式：** 取代函式  
  
## <a name="tables"></a>TABLES  
**加入主索引鍵**  
建立新的主索引鍵中[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]或 SQL Azure 資料表，如果 Access 資料表沒有主索引鍵或唯一索引。  
  
-   **預設模式**:False  
  
-   **開放式模式**:False  
  
-   **完整模式**:True  
  
> [!NOTE]  
> 當連接到 SQL Azure，這是預設為 True。  
  
## <a name="see-also"></a>另請參閱  
[使用者介面參考&#40;SybaseToSQL&#41;](../../ssma/sybase/user-interface-reference-sybasetosql.md)  
  
