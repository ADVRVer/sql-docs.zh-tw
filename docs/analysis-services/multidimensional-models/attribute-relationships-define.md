---
title: 定義屬性關聯性 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e49207e99887e13cdd5321821e7325b4a2dac7dc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "62717815"
---
# <a name="attribute-relationships---define"></a>屬性關聯性 - 定義
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中，屬性是維度的基礎建置組塊。 維度包含一組根據屬性關聯性所組織的屬性。  
  
 針對包含在維度中的每個資料表，有一種屬性關聯性可以建立資料表之重要屬性與該資料表中之其他屬性的關聯性。 建立維度時，您可以建立這種關聯性。  
  
 屬性關聯性提供下列優點：  
  
-   減少維度處理所需的記憶體量。 這會加快維度、磁碟分割和查詢的處理速度。  
  
-   由於儲存體存取速度更快，而且執行計劃的最佳化程度更好，因此可以增加查詢效能。  
  
-   假設已沿著關聯性路徑定義使用者自訂階層，則按照彙總設計演算法選取彙總時更有效率。  
  
  
## <a name="attribute-relationship-considerations"></a>屬性關聯性考量  
 當基礎資料支援屬性關聯性時，您也應該定義屬性之間的唯一屬性關聯性。 若要定義唯一屬性關聯性，使用 [維度設計師] 的 [屬性關聯性]  索引標籤。  
  
 具有輸出關聯性的屬性必須具備相對於其相關聯屬性的唯一索引鍵。 換句話說，來源屬性中的成員在相關聯的屬性中，必須識別一個 (而且只能識別一個) 成員。 例如，請考量 City -> State 的關聯性。 在此關聯性中，來源屬性為 [City]，而相關聯的屬性為 [State]。 來源屬性是在 「 多 」 端和相關聯的部分是多對一關聯性的 「 一 」 端。 來源屬性的索引鍵將是 City + State。 如需詳細資訊，請參閱 [建立、修改或刪除屬性關聯性](../../analysis-services/multidimensional-models/attribute-relationships-create-modify-or-delete-relationship.md)。  
  
 如需屬性 (Attribute) 關聯性之屬性 (Property) 的詳細資訊，請參閱 [設定屬性 (Attribute) 關聯性屬性 (Property)](../../analysis-services/multidimensional-models/attribute-relationships-configure-attribute-properties.md)。  
  
> [!NOTE]  
>  如果定義的屬性關聯性錯誤，可能導致查詢結果無效。  
  
## <a name="see-also"></a>另請參閱  
 [中，使用 [維度設計師] 的](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)  
  
  
