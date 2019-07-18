---
title: 資料指標類型 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC applications, cursors
- cursors [ODBC], types
- ODBC cursors, types
ms.assetid: 3a916cc7-f352-42cb-8b83-f78e06cef991
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 437b2d21e6441c3c6f6d94291d3f25d8546ddec4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68134076"
---
# <a name="cursor-types"></a>資料指標類型
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  ODBC 定義四種由 Microsoft 所支援的資料指標類型[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]而[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client ODBC 驅動程式。 這些資料指標不同能力偵測結果集的變更，並在資源中取用，例如記憶體及中的空間**tempdb**。 資料指標只有在嘗試重新提取變更過的資料列時，才能偵測到這些資料列的變更；沒有方法可讓資料來源通知資料指標目前所提取的資料列已變更。 交易隔離等級也會影響資料指標偵測到並非透過該資料指標所進行之變更的能力。  
  
 以下是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所支援的四種 ODBC 資料指標類型：  
  
-   順向資料指標：此種資料指標不支援捲動，而僅支援從資料指標開頭到結尾循序提取資料列。  
  
-   內建的靜態資料指標**tempdb**資料指標開啟時。 這種資料指標一定會顯示結果集在資料指標開啟時的原貌， 而不會反映出資料的變更。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 靜態資料指標永遠是唯讀的。 因為靜態伺服器資料指標建置為的工作資料表**tempdb**，資料指標結果集的大小不能超過所允許的最大資料列大小[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。  
  
-   索引鍵集驅動的資料指標：這種資料指標開啟時，會將結果集中資料列的成員資格和順序設為固定。 您可透過此資料指標看到非索引鍵資料行的變更。  
  
-   動態資料指標是靜態資料指標的相反。 動態資料指標會反映其結果集之中變更的資料列。 每回擷取時結果集之中資料列的資料值、順序和成員均會變動。  
  
## <a name="see-also"></a>另請參閱  
 [使用資料指標&#40;ODBC&#41;](../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
  
