---
title: "維度 (Analysis Services-多維度資料) 的簡介 |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- dimensions [Analysis Services], about dimensions
- storage [Analysis Services], dimensions
- dimensions [Analysis Services], examples
- storing data [Analysis Services], dimensions
- storage [Analysis Services]
ms.assetid: ab170fdd-4144-42db-9497-690b9189fc25
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9320eebfc25964e5e751e2d93ffc8cb7503861e5
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="dimensions---introduction"></a>維度-簡介
  所有的 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]維度都是根據資料表或檢視中的資料來源檢視中的資料行的屬性群組。 維度的存在與 Cube 無關，也可以用於多個 Cube 中、在單一 Cube 中使用多次，也可以在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體之間連結。 存在與 Cube 無關的維度稱為資料庫維度，而 Cube 中的資料庫維度執行個體則稱為 Cube 維度。  
  
## <a name="dimension-based-on-a-star-schema-design"></a>根據星狀結構描述設計的維度  
 維度的結構主要是由基礎維度資料表或資料表的結構來驅動。 最簡單的結構稱為星狀結構描述，其中的每個維度都會根據單一維度資料表，而該資料表又會透過「主索引鍵 - 外部索引鍵」關聯性直接連結至事實資料表。  
  
 下圖說明的子區段[!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)]範例資料庫中的，在其中**FactResellerSales**事實資料表與兩個維度資料表， **DimReseller**和**DimPromotion**。 **ResellerKey**中的資料行**FactResellerSales**事實資料表定義外部索引鍵關聯性**ResellerKey**主索引鍵資料行**DimReseller**維度資料表。 同樣地， **Dimpromotion**中的資料行**FactResellerSales**事實資料表定義外部索引鍵關聯性**Dimpromotion** 主索引鍵資料行**DimPromotion**維度資料表。  
  
 ![事實維度關聯性的邏輯結構描述](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/media/dimfactrelationship.gif "事實維度關聯性的邏輯結構描述")  
  
## <a name="dimension-based-on-a-snowflake-schema-design"></a>根據雪花式結構描述設計的維度  
 一般而言，會需要較複雜的結構，因為定義維度時需要有來自多個資料表的資訊。 在這個結構 (稱為雪花式結構描述) 中，每一個維度會以多個互相連結之資料表中資料行內的屬性為基礎，而最後會依「主索引鍵 - 外部索引鍵」關聯性連結至事實資料表。 例如下, 圖說明完整地描述中的 [產品] 維度所需的資料表**AdventureWorksDW**範例專案：  
  
 ![AdventureWorksAS 產品維度資料表](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/media/dimproduct.gif "AdventureWorksAS 產品維度的資料表")  
  
 若要完整地描述產品，產品的類別目錄與子類別目錄必須包含在產品維度中。 不過，該資訊不是存放直接的主資料表**DimProduct**維度。 從外部索引鍵關聯性**DimProduct**至**DimProductSubcategory**，因而具有外部索引鍵關聯性**DimProductCategory**資料表可以在 [產品] 維度中包含產品類別目錄和子類別目錄的資訊。  
  
## <a name="snowflake-schema-versus-reference-relationship"></a>雪花式結構描述與參考關聯性的比較  
 有時您可以選擇使用雪花式結構描述，從多份資料表中定義維度中的屬性，或選擇定義兩個不同的維度，然後定義它們之間的參考維度關聯性。 下列圖表說明如此的狀況。  
  
 ![範例參考維度的邏輯結構描述](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/media/dimindirect.gif "範例參考維度的邏輯結構描述")  
  
 在上圖中， **FactResellerSales**事實資料表中沒有的外部索引鍵關聯性**DimGeography**維度資料表。 不過， **FactResellerSales**事實資料表沒有的外部索引鍵關聯性**DimReseller**維度資料表，接著擁有的外部索引鍵關聯性**DimGeography**維度資料表。 若要定義轉售商 維度，其中包含有關每個轉售商地理位置資訊，您必須擷取這些屬性從**DimGeography**和**DimReseller**維度資料表。 然而，在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中，您可以建立兩個個別的維度，然後在這兩個維度之間定義參考維度關聯性，以在量值群組中連結它們，因而獲得相同的結果。 如需有關參考維度關聯性的詳細資訊，請參閱[維度關聯性](../../analysis-services/multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)。  
  
 在這個狀況下使用參考維度關聯性的其中一個好處是您可以建立單一地理位置維度，然後根據地理位置維度建立多個 Cube 維度，而完全不需要任何額外的儲存空間。 例如，您可以將一個地理位置 Cube 維度連結至轉售商維度，而將另一個地理位置 Cube 維度連結至客戶維度。 **相關主題：**[維度關聯性](../../analysis-services/multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)，[定義 Referenced Relationship and Referenced Relationship](../../analysis-services/multidimensional-models/define-a-referenced-relationship-and-referenced-relationship-properties.md)  
  
## <a name="processing-a-dimension"></a>處理維度  
 建立維度之後，您必須先處理維度，才能檢視屬性的成員與維度中的階層。 變更維度的結構或更新其基礎資料表中的資訊之後，必須再次處理此維度，然後才可以檢視這些變更。 在結構性變更之後處理維度時，也必須處理包含此維度的任何 Cube，否則將無法檢視此 Cube。  
  
## <a name="security"></a>安全性  
 維度的所有從屬物件，包括階層、層級和成員，都是使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中的角色來保護。 維度安全性可套用至資料庫中使用該維度的所有 Cube，或只套用至特定 Cube。 如需有關維度安全性的詳細資訊，請參閱[授與權限維度 &#40;Analysis Services &#41;](../../analysis-services/multidimensional-models/grant-permissions-on-a-dimension-analysis-services.md).  
  
## <a name="see-also"></a>另請參閱  
 [維度儲存](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-storage.md)   
 [維度翻譯](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimension-translations.md)   
 [可寫入維度](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  

