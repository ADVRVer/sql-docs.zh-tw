---
title: bcp_batch |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_batch
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_batch function
ms.assetid: 0bda489e-86bc-4a7e-80f6-96047e03f281
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c41e8d90adc8ff6eb2058feebe3f33c10edbfa92
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48049558"
---
# <a name="bcpbatch"></a>bcp_batch
  認可所有資料列先前大量複製從程式變數，並且傳送至[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]所[bcp_sendrow](bcp-sendrow.md)。  
  
## <a name="syntax"></a>語法  
  
```  
  
DBINT bcp_batch (HDBC  
hdbc  
);  
  
```  
  
## <a name="arguments"></a>引數  
 *hdbc*  
 這是已啟用大量複製的 ODBC 連接控制代碼。  
  
## <a name="returns"></a>傳回值  
 在上次呼叫之後儲存的資料列數目**bcp_batch**，則為-1，如果發生錯誤。  
  
## <a name="remarks"></a>備註  
 大量複製批次會定義交易。 當應用程式時，使用[bcp_bind](bcp-bind.md)並**bcp_sendrow**若要大量複製資料列從程式變數到 SQL Server 資料表，會認可資料列只有在程式呼叫時，才**bcp_batch**或是[bcp_done](bcp-done.md)。  
  
 您可以呼叫**bcp_batch**一旦每*n*資料列或是當您有暫停情況發生 （如同遙測的應用程式） 的內送資料中。 如果應用程式不會呼叫**bcp_batch**大量複製資料列的認可時，才**bcp_done**呼叫。  
  
## <a name="see-also"></a>另請參閱  
 [大量複製函數](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
