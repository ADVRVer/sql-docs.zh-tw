---
title: "產生報表 (MySQLToSQL) |Microsoft 文件"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Generating reports
ms.assetid: 1c0202e8-546d-4cb3-a37f-1d2e35d53839
caps.latest.revision: 6
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 180b3176563baa70d05aa93f2530fd486601fbb5
ms.contentlocale: zh-tw
ms.lasthandoff: 08/02/2017

---
# <a name="generating-reports-mysqltosql"></a>產生報表 (MySQLToSQL)
使用命令來執行特定活動的報表會在物件樹狀目錄層級的 SSMA 主控台產生。  
  
使用下列程序來產生報表：  
  
1.  指定**寫入摘要的報表-對**參數。 （如果有指定），將會儲存為檔案名稱的相關的報表，或在您指定的資料夾中。 檔案名稱是系統預先定義的位置下, 表中所述 **&lt; n &gt;** 是唯一的檔案數目與每個執行的相同命令的數字遞增。  
  
    報表 vis-à-vis 命令如下：  
  
    ||||  
    |-|-|-|  
    |**Sl。[否]。**|**Command**|**報表標題**|  
    |1|產生評估報告|AssessmentReport&lt;n&gt;。XML|  
    |2|轉換結構描述|SchemaConversionReport&lt;n&gt;。XML|  
    |3|移轉資料|DataMigrationReport&lt;n&gt;。XML|  
    |4|轉換 sql 陳述式|ConvertSQLReport&lt;n&gt;。XML|  
    |5|同步處理目標|TargetSynchronizationReport&lt;n&gt;。XML|  
    |6|從資料庫重新整理|SourceDBRefreshReport&lt;n&gt;。XML|  
  
    > [!IMPORTANT]  
    > 輸出報表與不同評估報表項目。 前者是一種報表執行的命令時的效能，後者是以程式設計方式使用的 XML 報表。  
  
    命令選項的輸出報告 （從 Sl。 資料分割 2-4 上面)，請參閱[執行 SSMA 主控台 &#40;MySQLToSQL &#41;](../../ssma/mysql/executing-the-ssma-console-mysqltosql.md) > 一節。  
  
2.  表示您想要輸出報表使用報表詳細等級設定的詳細程度：  
  
    ||||  
    |-|-|-|  
    |**Sl。[否]。**|**命令和參數**|**輸出說明**|  
    |1|verbose ="false"|產生之活動的摘要的報告。|  
    |2|verbose ="true"|產生每個活動的摘要和詳細狀態報告。|  
  
    > [!NOTE]  
    > 使用上述指定的報表詳細等級設定也適用於產生評估報告、 轉換結構描述、 移轉資料，轉換 sql 陳述式命令。  
  
3.  表示您想要使用錯誤報告設定的錯誤報表中的詳細程度：  
  
    ||||  
    |-|-|-|  
    |**Sl。[否]。**|**命令和參數**|**輸出說明**|  
    |1|報告錯誤 ="false"|沒有詳細資料發生錯誤 / 警告 / 資訊訊息。|  
    |2|報告錯誤 ="true"|詳細的錯誤 / 警告 / 資訊訊息。|  
  
    > [!NOTE]  
    > 錯誤報告設定上述指定也適用於產生評估報告、 轉換結構描述、 移轉資料，轉換 sql 陳述式命令。  
  
```xml  
<generate-assessment-report  
  
   object-name="<object-name>"  
  
   object-type="<object-type>"  
  
   verbose="<true/false>"  
  
   report-erors="<true/false>"  
  
   write-summary-report-to="<file-name/folder-name>"  
  
   assessment-report-folder="<folder-name>"  
  
   assessment-report-overwrite="<true/false>"  
  
/>  
```  
  
### <a name="synchronize-target"></a>同步處理目標：  
命令**同步處理目標**具有**報告錯誤至**參數，指定同步處理作業的錯誤報表的位置。 然後，名稱的檔案**TargetSynchronizationReport&lt;n&gt;。XML**會建立在指定的位置，其中 **&lt; n &gt;** 是唯一的檔案數目與每個執行的相同命令的數字遞增。  
  
**注意：**如果指定的資料夾路徑，則 '報告錯誤-對' 參數就會變成命令 '同步處理目標' 的選用屬性。  
  
```xml  
<!-- Example: Synchronize target entire Database with all attributes-->  
  
<synchronize-target  
  
   object-name="<object-name>"  
  
   on-error="<report-total-as-warning/report-each-as-warning/fail-script>"  
  
   report-errors-to="<file-name/folder-name>"  
  
/>  
```  
**物件名稱：**指定同步處理 （它也可以有 indivdual 物件名稱或群組的物件名稱） 被視為物件。  
  
**-錯誤：**指定是否要指定同步處理錯誤視為警告或錯誤。 在錯誤的可用選項：  
  
-   報表-總計-為-警告  
  
-   報表-每個-為-警告  
  
-   失敗指令碼  
  
### <a name="refresh-from-database"></a>重新整理從-資料庫：  
命令**從資料庫重新整理**具有**報告錯誤至**參數，指定重新整理作業的錯誤報表的位置。 然後，名稱的檔案**SourceDBRefreshReport&lt;n&gt;。XML**會建立在指定的位置，其中 **&lt; n &gt;** 是唯一的檔案數目與每個執行的相同命令的數字遞增。  
  
**注意：**如果指定的資料夾路徑，則 '報告錯誤-對' 參數就會變成命令 '同步處理目標' 的選用屬性。  
  
```xml  
<!-- Example: Refresh entire Schema (with all attributes)-->  
  
<refresh-from-database  
  
   object-name="<object-name>"  
  
   object-type ="<object-type>"  
  
   on-error="<report-total-as-warning/report-each-as-warning/fail-script>"  
  
   report-errors-to="<file-name/folder-name>"  
  
/>  
```  
**物件名稱：**指定重新整理 （它也可以有 indivdual 物件名稱或群組的物件名稱） 被視為物件。  
  
**-錯誤：**指定是否要指定重新整理錯誤視為警告或錯誤。 在錯誤的可用選項：  
  
-   報表-總計-為-警告  
  
-   報表-每個-為-警告  
  
-   失敗指令碼  
  
## <a name="see-also"></a>另請參閱  
[執行 SSMA 主控台 (MySQL)](http://msdn.microsoft.com/en-us/e3e9f7e4-0619-4861-a202-3d5d39953b26)  
  

