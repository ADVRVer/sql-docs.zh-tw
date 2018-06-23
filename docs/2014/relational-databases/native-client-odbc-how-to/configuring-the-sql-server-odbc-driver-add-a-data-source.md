---
title: 加入資料來源 (ODBC) |Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data sources [ODBC]
ms.assetid: b4ac6f0e-8e6a-4b1a-9a7e-60e0a69b2180
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 822ac0f5d2e228a982368849ed1c409ef63765ee
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36134161"
---
# <a name="add-a-data-source-odbc"></a>加入資料來源 (ODBC)
  您可以加入資料來源使用 ODBC 管理員，以程式設計方式 (使用[SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md))，或藉由建立檔案。  
  
### <a name="to-add-a-data-source-by-using-odbc-administrator"></a>使用 ODBC 管理員加入資料來源  
  
1.  從**控制台**，存取**系統管理工具**然後**資料來源 (ODBC)**。 或者，您可以叫用 odbcad32.exe。  
  
2.  按一下**使用者 DSN**，**系統 DSN**，或**檔案 DSN**索引標籤，然後再按一下**新增**。  
  
3.  按一下**SQL Server**，然後按一下 **完成**。  
  
4.  完成「建立新的資料來源至 SQL Server」精靈中的步驟。  
  
### <a name="to-add-a-data-source-programmatically"></a>以程式設計方式加入資料來源  
  
1.  呼叫[SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)與第二個參數設定為 ODBC_ADD_DSN 或 ODBC_ADD_SYS_DSN。  
  
### <a name="to-add-a-file-data-source"></a>加入檔案資料來源  
  
1.  呼叫[SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md)的 savefile = file_name 參數的連接字串中。 如果連接成功，ODBC 驅動程式會利用 SAVEFILE 參數所指向位置中的連接參數建立檔案資料來源。  
  
## <a name="see-also"></a>另請參閱  
 [設定 SQL Server ODBC 驅動程式如何主題](../../database-engine/dev-guide/configuring-the-sql-server-odbc-driver-how-to-topics.md)  
  
  