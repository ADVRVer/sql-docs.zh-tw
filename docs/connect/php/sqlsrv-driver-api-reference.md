---
title: SQLSRV 驅動程式 API 參考 |Microsoft Docs
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 0b55da26-ddeb-4e89-872a-91e0aba57103
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b1b1b94952006e338b324e7ca1da1d3bcbf8c2a0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47756586"
---
# <a name="sqlsrv-driver-api-reference"></a>SQLSRV 驅動程式 API 參考
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

在 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 中，SQLSRV 驅動程式的 API 名稱是 **sqlsrv**。 所有 **sqlsrv** 函式皆以 **sqlsrv_** 開頭，後面再加上動詞或名詞。 後面接著動詞的會執行某些動作，後面接著名詞的則會傳回某種形式的中繼資料。  
  
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
[PHP 手冊](http://php.net/manual)  
  
## <a name="see-also"></a>另請參閱  
[Microsoft Drivers for PHP for SQL Server 概觀](../../connect/php/overview-of-the-php-sql-driver.md)

[常數 &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)

[適用於 SQL Server 程式設計適用於 PHP 的 Microsoft 驅動程式的指南](../../connect/php/programming-guide-for-php-sql-driver.md)

[開始使用 Microsoft Drivers for PHP for SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md)
  
