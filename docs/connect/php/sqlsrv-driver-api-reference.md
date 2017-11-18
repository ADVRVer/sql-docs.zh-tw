---
title: "SQLSRV 驅動程式 API 參考 |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b55da26-ddeb-4e89-872a-91e0aba57103
caps.latest.revision: 42
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2bd1cf731f49119e54fb9e5a548a8988af1ef9fc
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsrv-driver-api-reference"></a>SQLSRV 驅動程式 API 參考
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

在 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 中，SQLSRV 驅動程式的 API 名稱是 **sqlsrv**。 所有**sqlsrv**函式開頭**sqlsrv_** ，後面接著動詞或名詞。 後面接著動詞的會執行某些動作，後面接著名詞的則會傳回某種形式的中繼資料。  
  
## <a name="in-this-section"></a>本節內容  
SQLSRV 驅動程式包含下列函數：  
  
|函數|Description|  
|------------|---------------|  
|[sqlsrv_begin_transaction](../../connect/php/sqlsrv-begin-transaction.md)|開始交易。|  
|[sqlsrv_cancel](../../connect/php/sqlsrv-cancel.md)|取消陳述式；會捨棄陳述式任何擱置的結果。|  
|[sqlsrv_client_info](../../connect/php/sqlsrv-client-info.md)|提供用戶端的相關資訊。|  
|[sqlsrv_close](../../connect/php/sqlsrv-close.md)|關閉連接。 釋出所有與連接相關聯的資源。|  
|[sqlsrv_commit](../../connect/php/sqlsrv-commit.md)|認可交易。|  
|[sqlsrv_configure](../../connect/php/sqlsrv-configure.md)|變更錯誤處理和記錄組態。|  
|[sqlsrv_connect](../../connect/php/sqlsrv-connect.md)|建立及開啟連接。|  
|[sqlsrv_errors](../../connect/php/sqlsrv-errors.md)|傳回與前次作業有關的錯誤和 (或) 警告資訊。|  
|[sqlsrv_execute](../../connect/php/sqlsrv-execute.md)|執行已備妥的陳述式。|  
|[sqlsrv_fetch](../../connect/php/sqlsrv-fetch.md)|讓下一個資料列可供讀取。|  
|[sqlsrv_fetch_array](../../connect/php/sqlsrv-fetch-array.md)|將下一個資料列擷取為數值索引陣列和 (或) 關聯陣列。|  
|[sqlsrv_fetch_object](../../connect/php/sqlsrv-fetch-object.md)|將下一個資料列擷取為物件。|  
|[sqlsrv_field_metadata](../../connect/php/sqlsrv-field-metadata.md)|傳回欄位中繼資料。|  
|[sqlsrv_free_stmt](../../connect/php/sqlsrv-free-stmt.md)|關閉陳述式。 釋出所有與陳述式相關聯的資源。|  
|[sqlsrv_get_config](../../connect/php/sqlsrv-get-config.md)|傳回指定組態設定的值。|  
|[sqlsrv_get_field](../../connect/php/sqlsrv-get-field.md)|依索引擷取目前資料列中的欄位。 可以指定 PHP 傳回類型。|  
|[sqlsrv_has_rows](../../connect/php/sqlsrv-has-rows.md)|偵測結果集是否有一或多個資料列。|  
|[sqlsrv_next_result](../../connect/php/sqlsrv-next-result.md)|讓下一個結果可供處理。|  
|[sqlsrv_num_rows](../../connect/php/sqlsrv-num-rows.md)|報告結果集內的資料列數目。|  
|[sqlsrv_num_fields](../../connect/php/sqlsrv-num-fields.md)|擷取作用中結果集內的欄位數目。|  
|[sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md)|準備 Transact-SQL 查詢而不加以執行。 隱含地繫結參數。|  
|[sqlsrv_query](../../connect/php/sqlsrv-query.md)|準備及執行 Transact-SQL 查詢。|  
|[sqlsrv_rollback](../../connect/php/sqlsrv-rollback.md)|復原交易。|  
|[sqlsrv_rows_affected](../../connect/php/sqlsrv-rows-affected.md)|傳回已修改的資料列數目。|  
|[sqlsrv_send_stream_data](../../connect/php/sqlsrv-send-stream-data.md)|透過每個對函數的呼叫，將最多 8 KB 的資料傳送到伺服器。|  
|[sqlsrv_server_info](../../connect/php/sqlsrv-server-info.md)|提供伺服器的相關資訊。|  
  
## <a name="reference"></a>參考  
[PHP 手冊](http://go.microsoft.com/fwlink/?LinkId=105500)  
  
## <a name="see-also"></a>另請參閱  
[PHP SQL 驅動程式概觀](../../connect/php/overview-of-the-php-sql-driver.md)
[常數 &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)  
[PHP SQL 驅動程式程式設計指南](../../connect/php/programming-guide-for-php-sql-driver.md)
[PHP SQL 驅動程式快速入門](../../connect/php/getting-started-with-the-php-sql-driver.md)
  

