---
title: Connection （ADO-WFC 語法） |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Connection collection [ADO], ADO/WFC syntax
ms.assetid: 8cfc35bb-91e2-47da-ad4c-982e9162cd51
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 64647d577170a79b1f600b7162a0338ea19c572e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "67919530"
---
# <a name="connection-ado---wfc-syntax"></a>Connection (ADO - WFC 語法)
## <a name="package-commswfcdata"></a>封裝 .com. wfc. 資料  
  
### <a name="constructor"></a>建構函式  
  
```  
public Connection()  
public Connection(String connectionstring)  
```  
  
### <a name="methods"></a>方法  
  
```  
public int beginTrans()  
public void commitTrans()  
public void rollbackTrans()  
public void cancel()  
public void close()  
public com.ms.wfc.data.Recordset execute(String commandText)  
public com.ms.wfc.data.Recordset execute(String commandText, int options)  
public int executeUpdate(String commandText)  
public int executeUpdate(String commandText, int options)  
```  
  
 **ExecuteUpdate**方法是特殊的案例方法，會使用特定參數來呼叫基礎 ADO **execute**方法。 **ExecuteUpdate**方法不支援傳回**記錄集**物件，因此**execute**方法的*options*參數會使用**AdoEnums. ExecuteOptions. NORECORDS**進行修改。 在**execute**方法完成之後，其更新的*RecordsAffected*參數會傳回到**executeUpdate**方法，最後會以**int**的形式傳回。  
  
```  
public void open()   
public void open(String connectionString)  
public void open(String connectionString, String userID)  
public void open(String connectionString, String userID, String password)  
public void open(String connectionString, String userID, String password, int options)  
public Recordset openSchema(int schema, Object[]  
    restrictions, String schemaID)  
public Recordset openSchema(int schema)  
public Recordset openSchema(int schema, Object[] restrictions)  
```  
  
### <a name="properties"></a>屬性  
  
```  
public int getAttributes()  
public void setAttributes(int attr)  
public int getCommandTimeout()  
public void setCommandTimeout(int timeout)  
public String getConnectionString()  
public void setConnectionString(String con)  
public int getConnectionTimeout()  
public void setConnectionTimeout(int timeout)  
public int getCursorLocation()  
public void setCursorLocation(int cursorLoc)  
public String getDefaultDatabase()  
public void setDefaultDatabase(String db)  
public int getIsolationLevel()  
public void setIsolationLevel(int level)  
public int getMode()  
public void setMode(int mode)  
public String getProvider()  
public void setProvider(String provider)  
public int getState()  
public String getVersion()  
public AdoProperties getProperties()  
public com.ms.wfc.data.Errors getErrors()  
```  
  
### <a name="events"></a>事件  
 如需 ADO/WFC 事件的詳細資訊，請參閱[依語言的 Ado 事件](../../../ado/guide/data/ado-event-instantiation-by-language.md)具現化。  
  
```  
public void addOnBeginTransComplete(ConnectionEventHandler handler)  
public void removeOnBeginTransComplete(ConnectionEventHandler handler)  
public void addOnCommitTransComplete(ConnectionEventHandler handler)  
public void removeOnCommitTransComplete(ConnectionEventHandler handler)  
public void addOnConnectComplete(ConnectionEventHandler handler)  
public void removeOnConnectComplete(ConnectionEventHandler handler)  
public void addOnDisconnect(ConnectionEventHandler handler)  
public void removeOnDisconnect(ConnectionEventHandler handler)  
public void addOnExecuteComplete(ConnectionEventHandler handler)  
public void removeOnExecuteComplete(ConnectionEventHandler handler)  
public void addOnInfoMessage(ConnectionEventHandler handler)  
public void removeOnInfoMessage(ConnectionEventHandler handler)  
public void addOnRollbackTransComplete(ConnectionEventHandler handler)  
public void removeOnRollbackTransComplete(ConnectionEventHandler handler)  
public void addOnWillConnect(ConnectionEventHandler handler)  
public void removeOnWillConnect(ConnectionEventHandler handler)  
public void addOnWillExecute(ConnectionEventHandler handler)  
public void removeOnWillExecute(ConnectionEventHandler handler)  
```  
  
## <a name="see-also"></a>另請參閱  
 [Connection 物件 (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
