---
title: "建立變數值檔案 (OracleToSQL) |Microsoft 文件"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Variable Value File Creation
- Variable Value File, Variable Value File Validation
ms.assetid: f583d81a-8e34-41b1-8100-ee3a6a82213b
caps.latest.revision: 26
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 3ba4def7c054b0d5a65a8ac93698cf6cb432845a
ms.contentlocale: zh-tw
ms.lasthandoff: 08/02/2017

---
# <a name="creating-variable-value-files-oracletosql"></a>建立變數值檔案 (OracleToSQL)
變數值的檔案是 XML 檔案中所包含的參數值經常變更從一部伺服器移轉到另一個來源或目的地伺服器名稱類似命令。 大量的資料庫移轉發生時，多個變數的檔案，以儲存每個來源伺服器的值時會建立及參考的主版的指令碼檔案中**– v**在命令列參數。 這有助於維護幾個指令碼檔案中的多個變數的檔案中的變數值的靜態值。  
  
> [!NOTE]  
> 1.  變數名稱會做為前置詞和後置字元為 $ （美元） 符號。 如果變數不會指派變數值檔案中的值，您會導致一主控台執行程序的指令碼檔剖析期間發生錯誤。  
> 2.  The escape character for **$** is **$$**. 如果變數或靜態值的參數值包含 **$**  （美元） 符號，然後 **$$** 必須指定以將其視為一個字元，而不是變數。  
> 3.  為了可維護性，變數可以宣告內`‘variable-group’`元素的邏輯隔離的使用者定義變數。  使用這個項目不是強制性。  
  
**範例:**  
  
**範例 1:**  
  
```  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="ProjectSpecs">  
  
    <variable name="$project_folder$" value="<project-folder>"/>  
  
    <variable name="$project_name$" value="<project-name>"/>  
  
    <variable name="$project_overwrite$" value="<true/false>"/>  
  
    <variable name="$project_type$" value="<project-type>"/>  
  
  </variable-group>  
  
</variables>  
```  
**範例 2:**  
  
```  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="SQLServerParams">  
  
    <variable-group name="SqlServerConnectionParams">  
  
      <variable name="$TargetServerName$" value="<server-name>"/>  
  
      <variable name="$TargetDB$" value="<database-name>"/>  
  
      <variable name="$TargetUserName$" value="<user-name>"/>  
  
      <variable name="$TargetPassword$" value="<password>"/>  
  
      <variable name="$TrustedConnection$" value="<true/false>"/>  
  
    </variable-group>  
  
    <variable-group name="SqlServerObjectParams">  
  
      <variable name="$ObjectName1$" value="<object-name>"/>  
  
      <variable name="$ObjectName2$" value="<object-name>"/>  
  
    </variable-group>  
  
  </variable-group>  
  
</variables>  
```  
  
## <a name="next-step"></a>下一個步驟  
在操作主控台的下一個步驟是[建立伺服器連接檔案 &#40; OracleToSQL &#41;](../../ssma/oracle/creating-the-server-connection-files-oracletosql.md)  
  
## <a name="see-also"></a>另請參閱  
[建立伺服器檔案 (Oracle)](http://msdn.microsoft.com/en-us/002f129e-0868-48ad-a4b4-c68b5007e12e)  
  

