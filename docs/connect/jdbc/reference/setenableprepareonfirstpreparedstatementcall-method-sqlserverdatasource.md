---
title: setEnablePrepareOnFirstPreparedStatementCall 方法 (SQLServerDataSource) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 26ac2cac075d08b8029ac0e85dacffd1674fb0da
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67974307"
---
# <a name="setenableprepareonfirstpreparedstatementcall-method-sqlserverdatasource"></a>setEnablePrepareOnFirstPreparedStatementCall 方法 (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定特定連接實例的行為。 如果此設定為 false, 則第一次執行備妥的語句將會呼叫 sp_executesql, 而不是準備語句, 一旦第二次執行時, 就會呼叫 sp_prepexec, 並實際設定備妥的語句控制碼。 下列執行會呼叫 sp_execute。 如此一來, 如果語句只執行一次, 就能減輕備妥的語句關閉 sp_unprepare 的需求。  
## <a name="syntax"></a>語法  
  
```
public void setEnablePrepareOnFirstPreparedStatementCall(boolean enablePrepareOnFirstPreparedStatementCall);  
```  
  
#### <a name="parameters"></a>參數  
 *enablePrepareOnFirstPreparedStatementCall*  
  
 **EnablePrepareOnFirstPreparedStatementCall**連接屬性的新值。  

## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 這個方法可從 JDBC 驅動程式6.4 版和之後版本取得。
 
## <a name="see-also"></a>另請參閱  
 [SQLServerDataSource 成員](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 類別](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
