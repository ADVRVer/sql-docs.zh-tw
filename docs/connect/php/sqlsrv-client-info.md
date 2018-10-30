---
title: sqlsrv_client_info |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_client_info
apitype: NA
helpviewer_keywords:
- API Reference, sqlsrv_client_info
- sqlsrv_client_info
ms.assetid: 3e2d3679-436a-45d8-8bdc-7c633b65a720
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9feacf047b9c949bae25958a3030fce4661c1583
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47710442"
---
# <a name="sqlsrvclientinfo"></a>sqlsrv_client_info
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

傳回連接和用戶端堆疊的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```  
  
sqlsrv_client_info( resource $conn)  
```  
  
#### <a name="parameters"></a>參數  
*$conn*：用以連接用戶端的連接資源。  
  
## <a name="return-value"></a>傳回值  
下表中說明、具有索引鍵的關聯陣列；如果連接資源為 Null，則為 **false** 。  
  
**若是 SQL Server 3.2 和 3.1 版的 PHP**：  
  
|索引鍵|Description|  
|-------|---------------|  
|DriverDllName|MSODBCSQL11.DLL (ODBC Driver 11 for SQL Server)|  
|DriverODBCVer|ODBC 版本 (xx.yy)|  
|DriverVer|ODBC Driver 11 for SQL Server DLL 版本：<br /><br />xx.yy.zzzz ([!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 3.2 或 3.1 版)|  
|ExtensionVer|php_sqlsrv.dll 版本：<br /><br />3.2.xxxx.x (適用於 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 3.2 版)<br /><br />3.1.xxxx.x (適用於 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 3.1 版)|  
  
**若是 SQL Server 3.0 和 2.0 版的 PHP**：  
  
|索引鍵|Description|  
|-------|---------------|  
|DriverDllName|SQLNCLI10.DLL ([!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 2.0 版)|  
|DriverODBCVer|ODBC 版本 (xx.yy)|  
|DriverVer|SQL Server Native Client DLL 版本：<br /><br />10.50.xxx ([!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 2.0 版)|  
|ExtensionVer|php_sqlsrv.dll 版本：<br /><br />2.0.xxxx.x ([!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 2.0 版)|  
  
## <a name="example"></a>範例  
從命令列執行下列範例時，該範例會將用戶端資訊寫入至主控台。 此範例假設 SQL Server 安裝在本機電腦上。 從命令列執行範例時，所有輸出都會寫入至主控台。  
  
```  
<?php  
/*Connect to the local server using Windows Authentication and   
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$conn = sqlsrv_connect( $serverName);  
  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
if( $client_info = sqlsrv_client_info( $conn))  
{  
       foreach( $client_info as $key => $value)  
      {  
              echo $key.": ".$value."\n";  
      }  
}  
else  
{  
       echo "Client info error.\n";  
}  
  
/* Close connection resources. */  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>另請參閱  
[SQLSRV 驅動程式 API 參考](../../connect/php/sqlsrv-driver-api-reference.md)

[關於文件中的程式碼範例](../../connect/php/about-code-examples-in-the-documentation.md)  
  
