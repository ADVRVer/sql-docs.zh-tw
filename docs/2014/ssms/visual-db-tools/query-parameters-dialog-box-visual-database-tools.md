---
title: 查詢參數對話方塊 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:69645
- vdt.dlgbox.definequeryparameters
ms.assetid: 31cdaee2-d7cd-4d64-a45f-924b27e8b1f0
caps.latest.revision: 12
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 84651cc4094be20dc91f0239215c3e9024566fc2
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43810214"
---
# <a name="query-parameters-dialog-box-visual-database-tools"></a>查詢參數對話方塊 (Visual Database Tools)
  這對話方塊可以讓您輸入查詢中定義的參數值。 執行查詢時，如果查詢中包含在執行階段期間需要使用者輸入的參數，此對話方塊就會出現。  
  
## <a name="options"></a>選項。  
 **名稱**  
 列出針對正在執行之查詢所定義的參數。 如果查詢包含具名參數，名稱會出現在清單中。 如果查詢包含未命名的參數，則查詢中會針對每個參數列出系統定義的參數名稱。  
  
 **值**  
 請輸入 [Name] 下方列出的每個參數值。 最近使用的值將顯示為預設參數值。  
  
## <a name="example"></a>範例  
 在 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫中執行下列 [SQL 窗格] 中的查詢時，會開啟 [查詢參數] 對話方塊。  
  
```  
SELECT   FirstName, LastName  
FROM    Person.Person AS Lastname  
WHERE   (LastName = @Param1);  
```  
  
## <a name="see-also"></a>另請參閱  
 [使用參數查詢 &#40;Visual Database Tools&#41;](visual-database-tools.md)  
  
  
