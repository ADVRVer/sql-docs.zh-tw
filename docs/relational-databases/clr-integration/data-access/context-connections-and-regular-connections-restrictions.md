---
title: 一般和內容連接的限制 |Microsoft 文件
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: clr
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- context connections [CLR integration]
- regular connections [CLR integration]
ms.assetid: 0c6fe4cb-d846-40b5-8884-35a9c770f5e8
caps.latest.revision: 24
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 93a08bc27c73db40f1ee388455ce7ffbc7c38557
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32920983"
---
# <a name="context-connections-and-regular-connections---restrictions"></a>內容連接和正常連接的限制
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  本主題討論中執行程式碼的相關限制[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]透過內容和一般連接處理序。  
  
## <a name="restrictions-on-context-connections"></a>內容連接的限制  
 開發應用程式時，請考慮下列適用於內容連接的限制：  
  
-   在給定連接的給定時間內，您只能開啟一個內容連接。 如果您同時在不同的連接中執行多個陳述式，其中每個陳述式可能會取得自己的內容連接。 這項限制不會影響來自不同連接的並行要求，只會影響給定連接的給定要求。  
  
-   內容連接不支援 Multiple Active Result Sets (MARS)。  
  
-   **SqlBulkCopy**類別內容連接中無法運作。  
  
-   不支援在內容連接中更新批次。  
  
-   **SqlNotificationRequest**無法搭配針對內容連接執行的命令。  
  
-   不支援取消針對內容連接執行的命令。 **SqlCommand.Cancel**方法會以無訊息模式忽略要求。  
  
-   當您使用 "context connection=true" 時，無法使用其他連接字串關鍵字。  
  
-   **SqlConnection.DataSource**屬性會傳回 null 的連接字串如果**SqlConnection**是 「 內容連接 = true"，而不是執行個體名稱[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]。  
  
-   設定**SqlCommand.CommandTimeout**屬性針對內容連接執行命令時，就沒有作用。  
  
## <a name="restrictions-on-regular-connections"></a>一般連接的限制  
 開發應用程式時，請考慮下列適用於一般連接的限制：  
  
-   不支援針對內部伺服器執行非同步命令。 包括"async = true"連接字串中的命令，然後執行命令，會導致**System.NotSupportedException**擲回。 此訊息會顯示：「在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 處理序內部執行時，不支援非同步處理」。  
  
-   **SqlDependency**不支援物件。  
  
## <a name="see-also"></a>另請參閱  
 [內容連接](../../../relational-databases/clr-integration/data-access/context-connection.md)  
  
  
