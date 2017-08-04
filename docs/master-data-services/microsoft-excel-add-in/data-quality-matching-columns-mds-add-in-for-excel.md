---
title: "資料品質比對資料行 （MDS 增益集的 Excel） |Microsoft 文件"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f683fdc6-0d4c-4793-8143-567616cb2094
caps.latest.revision: 9
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 4ce8ddcdbf8c29663640025ad40b4e01e44d99c1
ms.contentlocale: zh-tw
ms.lasthandoff: 08/02/2017

---
# <a name="data-quality-matching-columns-mds-add-in-for-excel"></a>資料品質比對資料行 (適用於 Excel 的 MDS 增益集)
  在[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]，當您在比對資料之後**資料品質**群組在功能區中，您可以按一下**顯示詳細資料**即可顯示提供比對詳細的資料行。  
  
 下表顯示比對資料時所顯示的資料行。  
  
|名稱|說明|  
|----------|-----------------|  
|**CLUSTER_ID**|用於將相似記錄分組的唯一識別碼。 所有相似的資料列都有相同的 **CLUSTER_ID**。 如果沒有顯示資料列的 **CLUSTER_ID** ，表示找不到相似的記錄。|  
|**RECORD_ID**|用於識別記錄的唯一識別碼。 類似於 MDS 儲存機制中儲存的代碼值，它是用來識別記錄的值。 每次進行比對時，都會自動產生它。|  
|**PIVOT_MARK**|與其他記錄比較的任意記錄；它沒有分數值。|  
|**SCORE**|表示群組中的記錄與樞紐記錄的相似度。 此分數由 DQS 決定。 如果沒有顯示分數，表示記錄是其他記錄的樞紐，或是找不到相符結果。|  
  
## <a name="see-also"></a>另請參閱  
 [資料品質比對中的 MDS 增益集的 Excel](../../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)   
 [比對相似資料 &#40;MDS 增益集的 Excel &#41;](../../master-data-services/microsoft-excel-add-in/match-similar-data-mds-add-in-for-excel.md)   
 [資料比對](../../data-quality-services/data-matching.md)  
  
  
