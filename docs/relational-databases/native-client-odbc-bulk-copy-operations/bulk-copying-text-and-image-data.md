---
title: 大量複製 Text 與 Image 資料 |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], text data
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], image data
- ODBC, bulk copy operations
ms.assetid: 87155bfa-3a73-4158-9d4d-cb7435dac201
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5032f6d038130fc78405949a171a39a6f0ec1842
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47607176"
---
# <a name="bulk-copying-text-and-image-data"></a>大量複製 Text 與 Image 資料
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  大型**文字**， **ntext**，並**映像**的值是使用複製的大量[bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md)函式。 您撰寫程式碼[bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) for**文字**， **ntext**，或**映像**資料行*pData*指標設定NULL 表示資料將會得到**bcp_moretext**。 請務必指定確切的每個所提供的資料長度**文字**， **ntext**，或**映像**中每個大量複製資料列的資料行。 如果資料行資料的長度不同於指定的資料行長度[bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)，使用[bcp_collen](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md)將長度設定為適當的值。 A [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)傳送所有非**文字**、 非-**ntext**，和非-**映像**資料; 您再呼叫**bcp_moretext**傳送**文字**， **ntext**，或**映像**個別單位中的資料。 大量複製函數決定，所有資料都傳送給目前**文字**， **ntext**，或**映像**資料行之資料的長度總和都傳送透過時**bcp_moretext**等於最新版本中指定的長度**bcp_collen**或是**bcp_bind**。  
  
 **bcp_moretext**沒有參數識別的資料行。 如果有多個**文字**， **ntext**，或**映像**中的資料列的資料行**bcp_moretext**作**文字**， **ntext**，或**映像**從具有最低的序號，並繼續進行，最高的序數數字的資料行的資料行的資料行。 **bcp_moretext**傳送的資料長度總和等於最新版本中指定的長度時，從一個資料行移至下一步**bcp_collen**或是**bcp_bind**目前的資料行。  
  
## <a name="see-also"></a>另請參閱  
 [執行大量複製作業&#40;ODBC&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
  
