---
title: 工作 7： 建立複合定義域 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ae778647-1df0-4952-9a69-0ef6177eea9c
caps.latest.revision: 7
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e6f1ee787a51b8417ad3de37b74075df8782c722
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37153289"
---
# <a name="task-7-creating-a-composite-domain"></a>工作 7：建立複合定義域
  在這個工作中，您建立複合定義域**地址驗證**，其中包括**地址行**，**縣 （市)**，**狀態**，以及**Zip**網域。 複合定義域可讓您定義在規則中涉及多個定義域的跨定義域規則。 複合定義域還有其他優點，例如能夠將欄位值剖析成多個定義域。  例如，[完整名稱] 欄位的值可以剖析成個別的名字、中間名和姓氏等定義域。 在本教學課程中，您只會定義跨定義域規則。 請參閱[管理複合定義域](http://msdn.microsoft.com/library/hh510399.aspx)如需詳細資訊。  
  
1.  在左窗格中，按一下**建立複合定義域**工具列上的按鈕。  
  
     ![建立複合定義域 工具列按鈕](../../2014/tutorials/media/et-creatingacompositedomain-01.jpg "建立複合定義域 工具列按鈕")  
  
2.  請輸入**地址驗證**for**複合定義域名稱**。  
  
     ![地址驗證 」 複合定義域](../../2014/tutorials/media/et-creatingacompositedomain-02.jpg "位址驗證 」 複合定義域")  
  
3.  從網域清單中選取**地址行**，**縣 （市)**，**狀態**，以及**Zip**然後按一下**向右箭號**將其新增至**複合定義域中**清單。  
  
4.  按一下 **[確定]** ，關閉對話方塊。  
  
## <a name="next-step"></a>下一個步驟  
 [工作 8：建立複合定義域規則](../../2014/tutorials/task-8-creating-a-composite-domain-rule.md)  
  
  
