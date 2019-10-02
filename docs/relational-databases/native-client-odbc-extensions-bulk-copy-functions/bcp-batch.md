---
title: bcp_batch |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- bcp_batch
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_batch function
ms.assetid: 0bda489e-86bc-4a7e-80f6-96047e03f281
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d1dd7b42ba6fcf4ea5b45fb779d4e6c67cd3074a
ms.sourcegitcommit: 8732161f26a93de3aa1fb13495e8a6a71519c155
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71707727"
---
# <a name="bcp_batch"></a>bcp_batch
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  認可先前從程式變數大量複製，並透過[bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)傳送至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的所有資料列。  
  
## <a name="syntax"></a>語法  
  
```  
  
DBINT bcp_batch (HDBC  
        hdbc);  
```  
  
## <a name="arguments"></a>引數  
 *hdbc*  
 這是已啟用大量複製的 ODBC 連接控制代碼。  
  
## <a name="returns"></a>傳回值  
 在最後一次呼叫**bcp_batch**之後所儲存的資料列數，如果發生錯誤，則為-1。  
  
## <a name="remarks"></a>備註  
 大量複製批次會定義交易。 當應用程式使用[bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)和**bcp_sendrow** ，將資料列從程式變數大量複製到 SQL Server 資料表時，只有在程式呼叫**bcp_batch**或[bcp_done](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-done.md)時，才會認可這些資料列。  
  
 您可以每隔*n*個數據列或在傳入的資料中有牢靠時（如同在遙測應用程式中），呼叫**bcp_batch**一次。 如果應用程式沒有呼叫**bcp_batch** ，只有在呼叫**bcp_done**時，才會認可大量複製的資料列。  
  
## <a name="see-also"></a>另請參閱  
 [大量複製函數](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
