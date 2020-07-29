---
title: 設定資料庫圖表設計工具
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.diagnostic.InstallSqlDiagramSupport
helpviewer_keywords:
- Database Diagram Designer
- database diagrams [SQL Server], Database Diagram Designer
- diagrams [SQL Server], Database Diagram Designer
ms.assetid: 927321ee-b459-4f5b-9719-4a7a95639143
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: 811905581cf0bb8f7bbd73f71a751e3c3da028c3
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2020
ms.locfileid: "85999335"
---
# <a name="set-up-database-diagram-designer-visual-database-tools"></a>設定資料庫圖表設計工具 (Visual Database Tools)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
若要使用資料庫圖表設計工具，必須先由 **db_owner** 角色的成員進行設定，才能控制圖表的存取權。  
  
### <a name="to-set-up-database-diagramming"></a>設定資料庫圖表化  
  
1.  從 [物件總管] 中，展開資料庫節點。  
  
2.  在資料庫連接中展開 [資料庫圖表] 節點。  
  
3.  如果您要設定資料庫圖表化，可在提示出現時選取 [是]  。  
  
    > [!NOTE]  
    > 這會在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫中建立資料庫圖表資料表、系統預存程序和系統函數。  
  
4.  Visual Studio 會在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體上建立下列物件：  
  
    1.  sysdiagrams 資料表  
  
    2.  sp_alterdiagram 預存程序  
  
    3.  sp_creatediagram 預存程序  
  
    4.  sp_dropdiagram 預存程序  
  
    5.  sp_renamediagram 預存程序  
  
    6.  fn_diagramobjects 函數  
  
    7.  sp_helpdiagrams 預存程序  
  
    8.  sp_helpdiagramsdefinition 預存程序  
  
    9. sp_upgraddiagrams 預存程序  
  
## <a name="see-also"></a>另請參閱  
[了解資料庫圖表擁有權 &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/understand-database-diagram-ownership-visual-database-tools.md)  
[升級舊版的資料庫圖表 &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/upgrade-database-diagrams-from-previous-editions-visual-database-tools.md)  
[ALTER AUTHORIZATION (Transact-SQL)](https://msdn.microsoft.com/8c805ae2-91ed-4133-96f6-9835c908f373)  
  
