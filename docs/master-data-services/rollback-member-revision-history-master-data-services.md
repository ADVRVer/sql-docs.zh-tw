---
title: 回復成員修訂歷程記錄
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: d39d3474-20e7-429f-9c8d-fcc4eb0854fc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0a37881bd22c73ea86316f3883382e3319e36b66
ms.sourcegitcommit: 6be9a0ff0717f412ece7f8ede07ef01f66ea2061
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85811435"
---
# <a name="rollback-member-revision-history-master-data-services"></a>回復成員修訂歷程記錄 (Master Data Services)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  每次變更成員時會記錄成員修訂歷程記錄。 您可以將成員修訂歷程記錄回復至舊版。  
  
## <a name="prerequisites"></a>必要條件  
  
-   您必須具有更新至少一個選取的成員之屬性的權限。 當您復原修訂歷程記錄時，可更新的所有屬性值將會都回復為先前的版本值。  
  
-   修訂歷程記錄只有在實體的交易記錄類型為成員時可用。  
  
 **若要回復成員修訂歷程記錄**  
  
1.  在 [主資料管理員] 中，按一下 [總管]。  
  
2.  選擇要復原的實體和成員。  
  
3.  按一下 [檢視歷程記錄]****。  
  
4.  選擇要回復的修訂，然後按一下 [回復]****。  
  
## <a name="see-also"></a>另請參閱  
 [成員修訂歷程記錄 &#40;Master Data Services&#41;](../master-data-services/member-revision-history-master-data-services.md)   
 [變更實體交易記錄類型 &#40;Master Data Services&#41;](../master-data-services/change-the-entity-transaction-log-type-master-data-services.md)  
  
  
