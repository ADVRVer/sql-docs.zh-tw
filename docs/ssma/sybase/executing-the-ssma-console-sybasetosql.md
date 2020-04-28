---
title: 執行 SSMA 主控台（SybaseToSQL） |Microsoft Docs
ms.custom: ''
ms.date: 09/27/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Sybase Console,Database Connection Commands
- Sybase Console,Manageability Commands
- Sybase Console,Migration Commands
- Sybase Console,Migration Preparation Command
- Sybase Console,Project Commands
- Sybase Console,Report Commands
- Sybase Console,Script File Commands
- Sybase Console,Script Generation Commands
ms.assetid: ea8950b7-fabc-4aa4-89f8-9573a2617d70
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 602bc0ac1584f9ff369efa8a2484a16a97a92285
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "68029150"
---
# <a name="executing-the-ssma-console-sybasetosql"></a>執行 SSMA 主控台 (SybaseToSQL)
Microsoft 為您提供了一組健全的腳本檔案命令，以執行和控制 SSMA 活動。 後續章節會詳細說明相同的情況。  
  
## <a name="script-file-commands"></a>指令檔命令  
主控台應用程式會使用本節中所列舉的特定標準腳本檔案命令。  
  
## <a name="project-commands"></a>專案命令  
專案命令會處理建立專案、開啟、儲存和結束專案。  
  
### <a name="create-new-project"></a>create-new-project  
此命令會建立新的 SSMA 專案。  
  
-   `project-folder`表示要建立之專案的資料夾。  
  
-   `project-name`表示專案的名稱。 {string}  
  
-   `overwrite-if-exists`選擇性屬性指出是否應該覆寫現有的專案。 true  
  
-   `project-type:`選擇性屬性。 表示專案類型，也就是 "sql-server-2005" 專案或 "sql-伺服器-2008" 專案或 "sql-伺服器-2012" 專案或 "sql----2014" 專案或 "sql-azure" 專案。 預設值為 "sql-server-2008"。  
  
**語法範例：**  
  
```xml  
<create-new-project  
  
  project-folder="<project-folder>"  
  
  project-name="<project-name>"  
  
  overwrite-if-exists="<true/false>" (optional)  
  
   project-type="<sql-server-2008/sql-server-2005/sql-server-2012/sql-server-2014/sql-azure>"  
/>  
```  
屬性「覆寫-如果-exists」預設為**false** 。  
  
屬性 ' 專案類型 ' 預設為**sql-伺服器-2008** 。  
  
### <a name="open-project"></a>開啟-專案  
此命令會開啟專案。

-   `project-folder`表示要建立之專案的資料夾。 如果指定的資料夾不存在，則此命令會失敗。  {string}  
  
-   `project-name`表示專案的名稱。 如果指定的專案不存在，則此命令會失敗。  {string}  
  
**語法範例：**  
  
```xml  
<open-project  
  
  project-folder="<project-folder>"  
  
  project-name="<project-name>"  
  
/>  
```  
> [!NOTE]  
> SSMA for SAP ASE 主控台應用程式支援回溯相容性。 您可以使用它來開啟先前版本 SSMA 所建立的專案。  
  
### <a name="save-project"></a>save-project  
此命令會儲存遷移專案。  
  
**語法範例：**  
  
```xml  
<save-project/>  
```  
  
### <a name="close-project"></a>關閉-專案  
此命令會關閉 [遷移] 專案。  
  
**語法範例：**  
  
```xml  
<close-project   
  if-modified="<save/error/ignore>"   (optional)  
/>  
```  
屬性 ' if-modified ' 是選擇性的，預設為**忽略**。  
  
## <a name="database-connection-commands"></a>資料庫連接命令  
資料庫連接命令有助於連接到資料庫。  
  
> [!NOTE]  
> - 主控台不支援 UI 的**流覽**功能。  
> - 如需「建立腳本檔」的詳細資訊，請參閱[&#40;SybaseToSQL&#41;建立腳本](../../ssma/sybase/creating-script-files-sybasetosql.md)檔。  
  
### <a name="connect-source-database"></a>連接-來源-資料庫  
此命令會執行源資料庫的連接，並載入源資料庫的高階中繼資料，但不是所有中繼資料。
  
如果無法建立與來源的連接，則會產生錯誤，而且主控台應用程式會停止執行。
  
伺服器定義是從伺服器連接檔案或腳本檔案之伺服器區段中的每個連接所定義的名稱屬性中取得。  
  
**語法範例：**  
  
```xml  
<connect-source-database  server="<server-unique-name>"/>  
```  
  
### <a name="force-load-sourcetarget-database"></a>強制載入-來源/目標-資料庫  
此命令會載入來源中繼資料，並且適用于離線處理遷移專案。  
  
如果無法建立與來源/目標的連接，則會產生錯誤，而且主控台應用程式會停止執行。  
  
此命令需要一個或數個資料庫節點做為命令列參數。  
  
**語法範例：**  
  
```xml  
<force-load metabase="<source/target>" >  
  
  <metabase-object object-name="<object-name>"/>  
  
</force-load>  
```  
  
### <a name="reconnect-source-database"></a>重新連接-來源-資料庫  
此命令會重新連接至源資料庫，但不會載入任何中繼資料，就像 [連接-來源-資料庫] 命令一樣。  
  
如果無法建立與來源的（re）連線，就會產生錯誤，而且主控台應用程式會停止執行。  
  
**語法範例：**  
  
```xml  
<reconnect-source-database  server="<server-unique-name>"/>  
```  
  
### <a name="connect-target-database"></a>連接-目標-資料庫  
此命令會連接到目標 SQL Server 資料庫，並載入目標資料庫的高階中繼資料，而不是整個中繼資料。  
  
如果無法建立與目標的連接，則會產生錯誤，而且主控台應用程式會停止執行。  
  
伺服器定義是從伺服器連接檔案或腳本檔案之伺服器區段中的每個連接所定義的名稱屬性中取得。  
  
**語法範例：**  
  
```xml  
<connect-target-database  server="<server-unique-name>"/>  
```  
  
### <a name="reconnect-target-database"></a>重新連接-目標-資料庫  
  
此命令會重新連接至目標資料庫，但不會載入任何中繼資料，不同于連接目標資料庫命令。  
  
如果無法建立（re）與目標的連接，則會產生錯誤，而且主控台應用程式會停止執行。  
  
**語法範例：**  
  
```xml  
<reconnect-target-database  server="<server-unique-name>"/>  
```  
  
## <a name="report-commands"></a>報表命令  
報告命令會針對各種 SSMA 主控台活動的效能產生報告。  
  
### <a name="generate-assessment-report"></a>產生-評量-報告  
  
此命令會在源資料庫上產生評量報告。  
  
如果在執行此命令之前未執行源資料庫連接，則會產生錯誤並結束主控台應用程式。  
  
在命令執行期間無法連接到源資料庫伺服器，也會導致終止主控台應用程式。  
  
-   `conversion-report-folder:`指定可儲存評量報告的資料夾。 （選擇性屬性）  
  
-   `object-name:`指定針對評估報告產生所考慮的物件（支援個別物件名稱或群組物件名稱）。  
  
-   `object-type:`指定物件名稱屬性中所呼叫物件的類型（如果指定了物件類別，則物件類型將會是 "category"）。  
  
-   `conversion-report-overwrite:`指定是否要覆寫評估報告資料夾（如果已經存在）。  
  
    **預設值：** false。 （選擇性屬性）  
  
-   `write-summary-report-to:`指定將產生報表的路徑。  
  
    如果只提及資料夾路徑，則依名稱**&lt;AssessmentReport n&gt;。** 已建立 XML。 （選擇性屬性）  
  
    報表建立有兩個進一步的子類別：  
  
    -   `report-errors`（= "true/false"，預設值為 "false" （選擇性屬性））  
  
    -   `verbose`（= "true/false"，預設值為 "false" （選擇性屬性））  
  
**語法範例：**  
  
```xml  
<generate-assessment-report  
  
  object-name="<object-name>"  
  
  object-type="<object-category>"  
  
  write-summary-report-to="<file-name/folder-name>"             (optional)  
  
  verbose="<true/false>"                       (optional)  
  
  report-errors="<true/false>"                 (optional)  
  
  assessment-report-folder="<folder-name>"          (optional)  
  
  conversion-report-overwrite="<true/false>"   (optional)  
  
/>  
```  
或  
  
```xml  
<generate-assessment-report  
  
  assessment-report-folder="<folder-name>"            (optional)  
  
  conversion-report-overwrite="<true/false>"     (optional)  
  
>  
<metabase-object object-name="<object-name>"  
  
        object-type="<object-category>"/>  
  
</generate-assessment-report>  
```  
  
## <a name="migration-commands"></a>遷移命令  
遷移命令會將目標資料庫架構轉換成來源架構，並將資料移轉至目標伺服器。  
  
### <a name="convert-schema"></a>轉換-架構  
此命令會執行從來源到目標架構的架構轉換。  
  
如果在執行此命令之前未執行來源或目標資料庫連接，或來源或目標資料庫伺服器的連接在命令執行期間失敗，則會產生錯誤並結束主控台應用程式。  
  
-   `conversion-report-folder:`指定可儲存評量報告的資料夾。 （選擇性屬性）  
  
-   `object-name:`指定轉換架構時所考慮的來源物件（支援個別物件名稱或群組物件名稱）。  
  
-   `object-type:`指定物件名稱屬性中所呼叫物件的類型（如果指定了物件類別，則物件類型將會是 "category"）。  
  
-   `conversion-report-overwrite:`指定是否要覆寫評估報告資料夾（如果已經存在）。  
  
    **預設值：** false。 （選擇性屬性）  
  
-   `write-summary-report-to:`指定將產生摘要報告的路徑。  
  
    如果只提及資料夾路徑，則依名稱**&lt;SchemaConversionReport n&gt;。** 已建立 XML。 （選擇性屬性）  
  
    報表建立有兩個進一步的子類別：  
  
    -   `report-errors`（= "true/false"，預設值為 "false" （選擇性屬性））  
  
    -   `verbose`（= "true/false"，預設值為 "false" （選擇性屬性））  
  
**語法範例：**  
  
```xml  
<convert-schema  
  
  object-name="<object-name>"  
  
  object-type="<object-category>"  
  write-summary-report-to="<file-name/folder-name>"     (optional)  
  
  verbose="<true/false>"                          (optional)  
  
  report-errors="<true/false>"                    (optional)  
  
  conversion-report-folder="<folder-name>"             (optional)  
  
  conversion-report-overwrite="<true/false>"      (optional)  
  
/>  
```  
或  
  
```xml  
<convert-schema  
  
  conversion-report-folder="<folder-name>"         (optional)  
  
  conversion-report-overwrite="<true/false>"> (optional)  
  
  <metabase-object object-name="<object-name>"  
  
    object-type="<object-category>"/>  
  
</convert-schema>  
```  
  
### <a name="migrate-data"></a>遷移-資料  
此命令會將源資料移轉至目標。  
  
-   `object-name:`指定針對遷移資料所考慮的來源物件（支援個別物件名稱或群組物件名稱）。  
  
-   `object-type:`指定物件名稱屬性中所呼叫物件的類型（如果指定了物件類別，則物件類型將會是 "category"）。  
  
-   `write-summary-report-to:`指定將產生報表的路徑。  
  
    如果只提及資料夾路徑，則依名稱**&lt;DataMigrationReport n&gt;。** 已建立 XML。 （選擇性屬性）  
  
    報表建立有兩個進一步的子類別：  
  
    -   `report-errors`（= "true/false"，預設值為 "false" （選擇性屬性））  
  
    -   `verbose`（= "true/false"，預設值為 "false" （選擇性屬性））  
  
**語法範例：**  
  
```xml  
<migrate-data  
  
  write-summary-report-to="<file-name/folder-name>"  
  
  report-errors="<true/false>" verbose="<true/false>">  
  
    <metabase-object object-name="<object-name>"/>  
  
    <metabase-object object-name="<object-name>"/>  
  
    <metabase-object object-name="<object-name>"/>  
  
    <data-migration-connection  
  
      source-use-last-used="true"/source-server="<server-unique-name>"  
  
      target-use-last-used="true"/target-server="<server-unique-name>"/>  
  
</migrate-data>  
```  
或  
  
```xml  
<migrate-data  
  
  object-name="<object-name>"  
  
  object-type="<object-category>"  
  
  write-summary-report-to="<file-name/folder-name>"  
  
  report-errors="<true/false>" verbose="<true/false>"/>  
```  
  
## <a name="migration-preparation-command"></a>遷移準備命令  
[遷移準備] 命令會起始來源與目標資料庫之間的架構對應。  
  
> [!NOTE]  
> 遷移命令的預設主控台輸出設定是「完整」輸出報告，沒有詳細的錯誤報表： [僅限來源物件樹狀結構根節點的摘要]。  
  
### <a name="map-schema"></a>對應架構  
此命令提供源資料庫與目標架構的架構對應。  
  
-   `source-schema`指定要遷移的來源架構。  
  
-   `sql-server-schema`指定要將來源架構遷移至其中的目標架構。  
  
**語法範例：**  
  
```xml  
<map-schema source-schema="<source-schema>"  
  
sql-server-schema="<target-schema>"/>  
```  
  
## <a name="manageability-commands"></a>管理性命令  
管理性命令有助於同步處理目標資料庫物件與源資料庫。  
  
> [!NOTE]  
> 遷移命令的預設主控台輸出設定是「完整」輸出報告，沒有詳細的錯誤報表： [僅限來源物件樹狀結構根節點的摘要]。  
  
### <a name="synchronize-target"></a>同步處理-目標  
此命令會將目標物件與目標資料庫同步處理。  
 
如果此命令是針對源資料庫執行，就會發生錯誤。  
  
如果在執行此命令之前未執行目標資料庫連接，或與目標資料庫伺服器的連接在命令執行期間失敗，則會產生錯誤並結束主控台應用程式。  
  
-   `object-name:`指定與目標資料庫進行同步處理時所考慮的目標物件（支援個別物件名稱或群組物件名稱）。  
  
-   `object-type:`指定物件名稱屬性中所呼叫物件的類型（如果指定了物件類別，則物件類型將會是 "category"）。  
  
-   `on-error:`指定是否要將同步處理錯誤指定為警告或錯誤。 發生錯誤的可用選項：  
  
    -   報告--as 警告  
  
    -   報告-每個警告  
  
    -   fail-腳本  
  
-   `report-errors-to:`指定同步處理作業的錯誤報表位置（選擇性屬性）。 如果只指定資料夾路徑，則會建立依名稱**TargetSynchronizationReport**的檔案。  
  
**語法範例：**  
  
```xml  
<synchronize-target  
  
object-name="<object-name>"  
  
on-error="<report-total-as-warning/  
  
report-each-as-warning/  
  
fail-script>" (optional)  
  
  report-errors-to="<file-name/folder-name>"        (optional)  
  
/>  
```  
或  
  
```xml  
<synchronize-target  
  
  object-name="<object-name>"  
  
  object-type="<object-category>"/>  
```  
或  
  
```xml  
<synchronize-target>  
  
  <metabase-object object-name="<object-name>"/>  
  
  <metabase-object object-name="<object-name>"/>  
  
  <metabase-object object-name="<object-name>"/>  
  
</synchronize-target>  
```  
  
### <a name="refresh-from-database"></a>從資料庫重新整理  
此命令會從資料庫重新整理來源物件。  
  
如果此命令是針對目標資料庫執行，則會產生錯誤。  
  
此命令需要一個或數個資料庫節點做為命令列參數。  
  
-   `object-name:`指定從源資料庫重新整理所考慮的來源物件（支援個別物件名稱或群組物件名稱）。  
  
-   `object-type:`指定物件名稱屬性中指定之物件的類型（如果指定了物件類別，則物件類型將會是 "category"）。  
  
-   `on-error:`指定是否要將重新整理錯誤當做警告或錯誤來呼叫。 發生錯誤的可用選項：  
  
    -   報告--as 警告  
  
    -   報告-每個警告  
  
    -   fail-腳本  
  
-   `report-errors-to:`指定重新整理作業的錯誤報表位置（選擇性屬性）。 如果只指定資料夾路徑，則會建立依名稱**SourceDBRefreshReport**的檔案。  
  
**語法範例：**  
  
```xml  
<refresh-from-database  
  
  object-name="<object-name>"  
  
  on-error="<report-total-as-warning/  
  
             report-each-as-warning/  
  
             fail-script>"              (optional)  
  
  report-errors-to="<file-name/folder-name>"        (optional)  
  
/>  
```  
或  
  
```xml  
<refresh-from-database  
  
  object-name="<object-name>"  
  
  object-type="<object-category>" />  
```  
或  
  
```xml  
<refresh-from-database>  
  
  <metabase-object object-name="<object-name>"/>  
  
</refresh-from-database>  
```  
  
## <a name="script-generation-commands"></a>腳本產生命令  
腳本產生命令會執行雙重工作：它們可協助您將主控台輸出儲存在腳本檔案中，並根據您指定的參數，將 T-sql 輸出記錄到主控台或檔案。  
  
### <a name="save-as-script"></a>另存新檔-腳本  
此命令是用來將物件的腳本儲存到當 [中繼檔 = 目標] 時所提到的檔案。 這是 [同步處理] 命令的替代方法，我們會取得腳本，並在目標資料庫上執行相同的作業。  
  
此命令需要一個或數個資料庫節點做為命令列參數。  
  
-   `object-name:`指定要儲存其腳本的物件（支援個別物件名稱或群組物件名稱）。  
  
-   `object-type:`指定物件名稱屬性中所呼叫物件的類型（如果指定了物件類別，則物件類型將會是 "category"）。  
  
-   `metabase:`指定它是否為來源或目標元資料庫。  
  
-   `destination:`指定必須儲存腳本的路徑或資料夾。 如果未提供檔案名，則會提供格式（object_name 屬性值）的檔案名。將會提供 out。
  
-   `overwrite:`若為 true，則會覆寫相同的檔案名（如果存在的話）。 它可以有值（true/false）。  
  
**語法範例：**  
  
```xml  
<save-as-script  
  
  metabase="<source/target>"  
  
  object-name="<object-name>"  
  
  object-type="<object-category>"  
  
  destination="<file-name/folder-name>"  
  
  overwrite="<true/false>"   (optional)  
  
/>  
```  
或  
  
```xml  
<save-as-script  
  
  metabase="<source/target>"  
  
  destination="<file-name/folder-name>"  
  
    <metabase-object object-name="<object-name>"  
  
                     object-type="<object-category>"/>  
  
</save-as-script>  
```  
  
### <a name="convert-sql-statement"></a>convert-sql 語句
此命令會轉換 SQL 語句。  
  
-   `context`指定架構名稱。  
  
-   `destination`指定是否應該將輸出儲存在檔案中。  
  
    如果未指定這個屬性，則會在主控台上顯示轉換的 T-sql 語句。 （選擇性屬性）  
  
-   `conversion-report-folder`指定可儲存評量報告的資料夾。 （選擇性屬性）  
  
-   `conversion-report-overwrite`指定是否要覆寫評估報告資料夾（如果已經存在）。  
  
    **預設值：** false。 （選擇性屬性）  
  
-   `write-converted-sql-to`指定要儲存已轉換之 T-sql 的檔案（或）資料夾路徑。 當資料夾路徑與`sql-files`屬性一起指定時，每個原始程式檔都會在指定的資料夾下建立對應的目標 t-sql 檔案。 當資料夾路徑與`sql`屬性一併指定時，已轉換的 t-sql 會寫入名為 Result 的檔案中指定的資料夾底下。  
  
-   `sql`指定要轉換的 Sybase sql 語句，可以使用 ";" 分隔一或多個語句  
  
-   `sql-files`指定必須轉換成 T-sql 程式碼之 sql 檔案的路徑。  
  
-   `write-summary-report-to`指定將產生摘要報告的路徑。 如果只提及資料夾路徑，則會建立依名稱**ConvertSQLReport**的檔案。 （選擇性屬性）  
  
    建立摘要報表有兩個進一步的子類別，亦即：  
  
    -   報告-錯誤（= "true/false"，預設值為 "false" （選擇性屬性））。  
  
    -   verbose （= "true/false"，預設值為 "false" （選擇性屬性））。  
  
此命令需要一個或數個資料庫節點做為命令列參數。  
  
**語法範例：**  
  
```  
<convert-sql-statement  
  
       context="<database-name>.<schema-name>"  
  
        conversion-report-folder="<folder-name>"  
  
        conversion-report-overwrite="<true/false>"  
  
        write-summary-report-to="<file-name/folder-name>"   (optional)  
  
        verbose="<true/false>"   (optional)  
  
        report-errors="<true/false>"   (optional)  
  
        destination="<stdout/file>"   (optional)  
  
        write-converted-sql-to ="<file-name/folder-name>"  
  
        sql="SELECT 1 FROM DUAL;">  
  
    <output-window suppress-messages="<true/false>" />  
  
</convert-sql-statement>  
```  
或  
  
```  
<convert-sql-statement  
  
         context="<database-name>.<schema-name>"  
  
         conversion-report-folder="<folder-name>"  
  
         conversion-report-overwrite="<true/false>"  
  
         write-summary-report-to="<file-name/folder-name>"   (optional)  
  
         verbose="<true/false>"   (optional)  
  
         report-errors="<true/false>"   (optional)  
  
         destination="<stdout/file>"   (optional)  
  
         write-converted-sql-to ="<file-name/folder-name>"  
  
         sql-files="<folder-name>\*.sql"  
  
/>  
```  
或  
  
```  
<convert-sql-statement  
  
         context="<database-name>.<schema-name>"  
  
         conversion-report-folder="<folder-name>"  
  
         conversion-report-overwrite="<true/false>"  
  
         sql-files="<folder-name>\*.sql"  
  
/>  
```  
  
## <a name="next-steps"></a>後續步驟  
如需命令列選項的詳細資訊，請參閱[SSMA 主控台中的命令列選項（AccessToSQL）](../access/command-line-options-in-ssma-console-accesstosql.md)。  
  
如需範例主控台腳本檔案的詳細資訊，請參閱[使用範例主控台腳本檔案 &#40;SybaseToSQL&#41;](../../ssma/sybase/working-with-the-sample-console-script-files-sybasetosql.md)  
  
下一步取決於您的專案需求：  
  
-   如需指定密碼或匯出/匯入密碼，請參閱[&#40;SybaseToSQL&#41;管理密碼](../../ssma/sybase/managing-passwords-sybasetosql.md)。  
  
-   如需產生報表，請參閱[&#40;SybaseToSQL&#41;產生報表](../../ssma/sybase/generating-reports-sybasetosql.md)。  
  
-   如需主控台的疑難排解問題，請參閱[&#40;SybaseToSQL&#41;的疑難排解](../../ssma/sybase/troubleshooting-sybasetosql.md)。  
  
