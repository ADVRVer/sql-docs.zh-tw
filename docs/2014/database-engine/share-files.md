---
title: 共用檔案 |Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- sharing files
- file sharing [SQL Server]
- version control services [SQL Server], file sharing
ms.assetid: 645f5c0a-e949-4e87-8988-85e4d6128464
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 528e0ac6eb185089fc7e5e38f654dd1acf2fb64e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36135221"
---
# <a name="share-files"></a>共用檔案
  您可以利用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 來跨越不同的原始檔控制專案共用項目。 當您共用某個項目時，這個項目的任何變更都會反映在共用這個項目的每個專案中。  
  
 「項目共用」為原始檔控制的使用者帶來下列好處：  
  
-   不需要每個使用共用項目的專案都儲存一份個別的項目副本，可以節省原始檔控制用戶端和伺服器的磁碟空間。 原始檔控制提供者將共用項目儲存在單一中央位置，每個共用它的專案都會儲存一個指向這個位置的指標。  
  
-   避免版本不相容。 由於共用項目的每個專案都使用相同的項目版本，因此，當各個項目副本在多個專案內個別變更時，不會發生衝突。  
  
### <a name="to-share-an-item"></a>共用項目  
  
1.  在 [方案總管] 中，選取共用檔案要放在其中的資料夾或專案。  
  
2.  在**檔案**功能表上，指向**原始檔控制**，然後按一下 **共用**。  
  
3.  在**分享**對話方塊中，瀏覽目錄清單中，您想要共用的項目，然後按一下該項目。  
  
4.  按一下**共用**。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制基本概念](../../2014/database-engine/source-control-basics.md)  
  
  