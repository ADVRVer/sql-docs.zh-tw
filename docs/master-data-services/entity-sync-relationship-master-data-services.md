---
title: 實體同步關聯性 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.component: non-specific
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: bd627a2d-dc64-47e9-9a71-2d0ad04b4962
caps.latest.revision: 6
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: d54b4f3b9211f7ab79483a76c82ec5db14abff72
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="entity-sync-relationship-master-data-services"></a>實體同步關聯性 (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  實體同步是實體版本間單向且可重複的同步處理。 它可讓您在不同模型間共用實體資料。 您可以將事實的單一來源保留在一個模型，並且在其他模型中重複使用此主要資料。 例如，您可以將美國的狀態資料儲存在一個模型實體，並且在其他模型中重複使用該資料。  
  
 實體同步時，您也可以進行資料的一次性複製。  
  
 來源實體中具有任意格式和檔案屬性的所有分葉成員，都會在同步執行期間同步處理至目標實體。 這會建立、刪除和修改實體結構描述和成員。  
  
 一旦建立同步關聯性，目標實體只能由同步處理程序修改。 隨時可以移除同步關聯性，讓目標實體可供編輯。  
  
## <a name="see-also"></a>另請參閱  
 [建立及執行實體同步關係 &#40;Master Data Services&#41;](../master-data-services/create-and-execute-an-entity-sync-relationship-master-data-services.md)   
 [編輯和刪除實體同步關係 &#40;Master Data Services&#41;](../master-data-services/edit-and-delete-an-entity-sync-relationship-master-data-services.md)  
  
  
