---
title: 建立變數值檔案 (DB2ToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 122f3fbe-46a0-40df-ac3b-d43bf33d96ba
caps.latest.revision: 5
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 73afb63d53be87baaaf1e969ae06c803100aa4f7
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2018
ms.locfileid: "40395923"
---
# <a name="creating-variable-value-files-db2tosql"></a>建立變數值檔案 (DB2ToSQL)
變數值檔案是 XML 檔案包含一些來源或目的地伺服器名稱經常變更從一部伺服器移轉到另一個的命令的參數值。 大量的資料庫移轉發生時，會建立並使用主要的指令碼檔案中參考多個變數的檔案，以儲存每個來源伺服器的值 **– v**在命令列切換。 這有助於維護幾個指令碼檔案中的靜態值，與多個變數的檔案中的變數值。  
  
> [!NOTE]  
> 1.  變數名稱會做為前置詞和後置字元為 $ （美元） 符號。 如果變數未指派的變數值檔案中的值，您就會導致懸置在主控台執行程序的指令碼檔案剖析期間發生錯誤。  
> 2.  逸出字元**$** 是**$$**。 如果變數或靜態值的參數值包含**$** （貨幣） 符號，然後**$$** 必須指定將它視為一個字元，而不是變數。  
> 3.  基於可維護性，變數可以宣告內`‘variable-group’`邏輯區隔使用者的項目定義的變數。  這個元素的使用方式不是必要的。  
  
**範例：**  
  
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
操作主控台的下一個步驟是[建立伺服器連線檔案&#40;DB2ToSQL&#41;](../../ssma/db2/creating-the-server-connection-files-db2tosql.md)  
  
## <a name="see-also"></a>另請參閱  
[建立伺服器連線檔案](../oracle/creating-the-server-connection-files-oracletosql.md)  
  
