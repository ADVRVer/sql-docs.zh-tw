---
title: 異動複寫的發行項選項 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- articles [SQL Server replication], transactional replication options
- transactional replication, article options
ms.assetid: 3469b185-0ea5-4690-a71c-717230d886b6
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7e003ab7a1928c98e2e4e004d53d71fc001227d7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48190718"
---
# <a name="article-options-for-transactional-replication"></a>異動複寫的發行項選項
  針對交易式發行集中的發行項提供了一些選項。 使用異動複寫，您可以執行下列項目：  
  
-   指定變更從「發行者」傳播到「訂閱者」的方式。 如需詳細資訊，請參閱[指定交易式發行項變更的傳播方式](transactional-articles-specify-how-changes-are-propagated.md)。  
  
-   指定複寫預存程序的執行。 針對會影響大量資料的維護導向預存程序複寫結果時很有用。 如需詳細資訊，請參閱 [Publishing Stored Procedure Execution in Transactional Replication](publishing-stored-procedure-execution-in-transactional-replication.md)。  
  
-   指定結構描述選項，如條件約束和觸發程序是否複製到訂閱者。 如需詳細資訊，請參閱 [指定結構描述選項](../publish/specify-schema-options.md)。  
  
-   使用資料列篩選與資料行篩選。 篩選資料表發行項可讓您建立即將發行的資料分割。 如需詳細資訊，請參閱[篩選發行的資料](../publish/filter-published-data.md)。  
  
## <a name="see-also"></a>另請參閱  
 [發行資料和資料庫物件](../publish/publish-data-and-database-objects.md)  
  
  
