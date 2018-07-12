---
title: bcp_columns |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- bcp_columns
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_columns function
ms.assetid: 5376f6fe-9508-439a-8c66-778d77f19ac3
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c1107919200b3546274a3a78a89562c9ed715216
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37427447"
---
# <a name="bcpcolumns"></a>bcp_columns
  設定在使用者檔案中可搭配大量複製在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中進出作業的資料行總數。 [bcp_setbulkmode](bcp-setbulkmode.md)可用來代替 bcp_columns 並[bcp_colfmt](bcp-colfmt.md)。  
  
## <a name="syntax"></a>語法  
  
```  
  
RETCODE bcp_columns (  
HDBC   
hdbc  
,  
INT   
nColumns  
);  
  
```  
  
## <a name="arguments"></a>引數  
 *hdbc*  
 這是已啟用大量複製的 ODBC 連接控制代碼。  
  
 *nColumns*  
 這是使用者檔案中的資料行總數。 即使您準備要從使用者檔案大量複製資料[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資料表，並不想要複製使用者檔案中的所有資料行，您仍然必須設定*nColumns*使用者檔案資料行的總數。  
  
## <a name="returns"></a>傳回值  
 SUCCEED 或 FAIL。  
  
## <a name="remarks"></a>備註  
 後，才可以呼叫此函式[bcp_init](bcp-init.md)已使用有效的檔案名稱呼叫。  
  
 只有打算使用與預設值不同的使用者檔案格式時，才可以呼叫此函數。 如需有關預設使用者檔案格式的描述的詳細資訊，請參閱**bcp_init**。  
  
 之後呼叫`bcp_columns`，您必須呼叫[bcp_colfmt](bcp-colfmt.md)以完整定義自訂檔案格式的使用者檔案中的每一個資料行。  
  
## <a name="see-also"></a>另請參閱  
 [大量複製函數](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
