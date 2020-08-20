---
description: 管理備份 (OracleToSQL)
title: 管理 (OracleToSQL) 的備份 |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Oracle Backup Management
- SQL Server Backup Management
ms.assetid: a1a03ef9-b6e8-4127-bad0-eae261251472
author: nahk-ivanov
ms.author: alexiva
manager: alexiva
ms.openlocfilehash: c0505913f29e473f4687454b8622becb01389519
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88480460"
---
# <a name="managing-backups-oracletosql"></a>管理備份 (OracleToSQL)
Oracle 備份管理可讓您在執行測試之前或之後備份及還原資料表資料。 您也可以使用 [管理備份內容] 對話方塊來管理 [備份內容]。  
  
## <a name="oracle-backup-management"></a>Oracle 備份管理  
  
### <a name="backup"></a>Backup  
若要開啟 [備份] 對話方塊，請在 [測試器] 功能表上指向 [Oracle 備份管理]，然後按一下 [備份]。在 [備份] 對話方塊中，您會發現 Oracle 中繼資料樹狀結構會顯示已載入之 Oracle 架構的所有資料表。 選取一或多個資料表來執行備份。  
  
對話方塊提供下列按鈕：  
  
-   按一下 [ **檢查狀態** ] 按鈕來檢查資料表的備份狀態。  
  
-   按一下 [ **備份** ] 按鈕以備份資料表的資料。  
  
-   按一下 [ **取消** ] 按鈕以關閉對話方塊。  
  
### <a name="restore"></a>還原  
若要開啟 [還原] 對話方塊，請在 [測試人員] 功能表上指向 [Oracle 備份管理]，然後按一下 [還原]。在那裡，您會找到一個樹狀結構，其中包含備份中可用的資料表。 選取一或多個資料表來還原其資料。  
  
對話方塊提供下列按鈕：  
  
-   按一下 [ **檢查狀態** ] 按鈕來檢查資料表的備份狀態。  
  
-   按一下 [ **還原** ] 按鈕，將備份資料還原到資料表中。  
  
-   按一下 [ **取消** ] 按鈕以關閉對話方塊。  
  
### <a name="managing-backup-contents"></a>管理備份內容  
若要開啟 [管理備份內容]，請在 [測試器] 功能表上指向 [Oracle 備份管理]，然後按一下 [備份內容]。在那裡，您會找到包含備份中資料表的樹狀結構。  
  
對話方塊提供下列按鈕：  
  
-   按一下 [ **檢查狀態** ] 按鈕來檢查資料表的備份狀態。  
  
-   按一下 [ **移除** ] 按鈕，從備份中移除資料表。  
  
-   按一下 [ **關閉** ] 按鈕以關閉對話方塊。  
  
## <a name="sql-server-backup-management"></a>SQL Server 備份管理  
SQL Server 備份管理可讓您在執行測試之前或之後備份和還原資料表資料。 您也可以使用 [管理備份內容] 對話方塊來管理 [備份內容]。  
  
### <a name="backup"></a>Backup  
若要開啟 [備份] 對話方塊，請在 [測試器] 功能表上，指向 SQL Server 備份管理]，然後按一下 [備份]。 在 [備份] 對話方塊中，您會找到 SQL Server 的中繼資料樹狀結構，其中顯示已載入 SQL Server 資料庫的所有資料表。 選取一或多個資料表來執行備份。  
  
對話方塊提供下列按鈕：  
  
-   按一下 [ **檢查狀態** ] 按鈕來檢查資料表的備份狀態。  
  
-   按一下 [ **備份** ] 按鈕以備份資料表的資料。  
  
-   按一下 [ **取消** ] 按鈕以關閉對話方塊。  
  
### <a name="restore"></a>還原  
若要開啟 [還原] 對話方塊，請在 [測試器] 功能表上，按一下 [還原 ...] SQL Server 備份管理。在那裡，您會找到一個樹狀結構，其中包含備份中可用的資料表。 選取一或多個資料表來還原其資料。  
  
對話方塊提供下列按鈕：  
  
-   按一下 [ **檢查狀態** ] 按鈕來檢查資料表的備份狀態。  
  
-   按一下 [ **還原** ] 按鈕，將備份資料還原到資料表中。  
  
-   按一下 [ **取消** ] 按鈕以關閉對話方塊。  
  
### <a name="managing-backup-contents"></a>管理備份內容  
若要開啟 [管理備份內容]，請在 [測試器] 功能表上，指向 SQL Server 備份管理]，然後按一下 [備份內容]。在那裡，您會找到包含備份中資料表的樹狀結構。  
  
對話方塊提供下列按鈕：  
  
-   按一下 [ **檢查狀態** ] 按鈕來檢查資料表的備份狀態。  
  
-   按一下 [ **移除** ] 按鈕，從備份中移除資料表。  
  
-   按一下 [ **關閉** ] 按鈕以關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
[測試遷移的資料庫物件 &#40;OracleToSQL&#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
