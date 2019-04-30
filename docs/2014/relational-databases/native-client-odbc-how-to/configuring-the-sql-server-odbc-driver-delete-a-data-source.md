---
title: 刪除資料來源 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data sources [ODBC]
ms.assetid: 910e3e16-7b91-49d8-80bb-b4243926afaa
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ff882caf0ce5d9ef7d2e9f059daed89ed4b50d82
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63126101"
---
# <a name="delete-a-data-source-odbc"></a>刪除資料來源 (ODBC)
  您可以使用 ODBC 管理員，以程式設計方式刪除資料來源 (利用[SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md))，或藉由刪除檔案 （如果檔案資料來源名稱）。  
  
### <a name="to-delete-a-data-source-by-using-odbc-administrator"></a>使用 ODBC 管理員刪除資料來源  
  
1.  在**控制台中**，開啟**系統管理工具**，然後按兩下**資料來源 (ODBC)**。 或者，您也可以從命令提示字元執行 odbcad32.exe。  
  
2.  按一下 [**使用者 DSN**，**系統 DSN**，或**檔案 DSN** ] 索引標籤。  
  
3.  按一下要刪除的資料來源。  
  
4.  按一下 **移除**，然後確認刪除。  
  
## <a name="example"></a>範例  
 若要以程式設計方式刪除資料來源，請呼叫[SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)使用 ODBC_REMOVE_DSN 或 ODBC_REMOVE_SYS_DSN 做為第二個參數。  
  
 下列範例會示範如何以程式設計的方式刪除資料來源。  
  
```  
// remove_odbc_data_source.cpp  
// compile with: ODBCCP32.lib user32.lib  
#include <iostream>  
#include <windows.h>  
#include <odbcinst.h>  
  
int main() {   
   LPCSTR provider = "SQL Server";   // Windows SQL Server Driver  
   LPCSTR provider = "SQL Server";   // Windows SQL Server driver  
   LPCSTR provider2 = "SQL Server Native Client 11.0";   // SQL Server 2012 Native Client driver  
   LPCSTR dsnname = "DSN=data2";  
   BOOL retval = SQLConfigDataSource(NULL, ODBC_REMOVE_DSN, provider, dsnname);  
   std::cout << retval;   // 1 if successful  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [設定 SQL Server ODBC 驅動程式的使用說明主題](../../database-engine/dev-guide/configuring-the-sql-server-odbc-driver-how-to-topics.md)  
  
  
