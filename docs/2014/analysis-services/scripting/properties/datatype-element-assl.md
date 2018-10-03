---
title: DataType 元素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DataType Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DataType
helpviewer_keywords:
- DataType element
ms.assetid: efe6f717-8288-4ca2-85ed-9b63d27c02d8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 92c3981344d0425c46ef283fa8792de942d6193b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48191038"
---
# <a name="datatype-element-assl"></a>DataType 元素 (ASSL)
  定義相關聯元素的資料類型。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<DataItem> <!-- or Measure -->  
   ...  
   <DataType>...</DataType>  
   ...  
</DataItem>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|字串 (列舉)|  
|預設值|None|  
|基數|0-1：只能出現一次的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[DataItem](../data-type/dataitem-data-type-assl.md)，[量值](../objects/measure-element-assl.md)|  
|子元素|None|  
  
## <a name="remarks"></a>備註  
 `DataType` 的值定義於 `System.Data.OleDb.OleDbType` 列舉中。 不過，只有下表中的列舉值才適用於 `DataType` 元素。  
  
|值|描述|  
|-----------|-----------------|  
|*BigInt*|64 位元帶正負號的整數。 此資料類型會對應至`Int64`中的資料類型[!INCLUDE[msCoName](../../../includes/msconame-md.md)]OLE DB 中的.NET Framework 和的 DBTYPE_I8 資料類型。|  
|*bool*|布林值 (Boolean)。 這個資料類型會對應至 .NET Framework 中的 `Boolean` 資料類型和 OLE DB 中的 DBTYPE_BOOL 資料類型。|  
|*貨幣*|貨幣值，範圍從-2<sup>63</sup> （或-922,337,203,685,477.5808） 到 2<sup>63</sup>-1 （或 + 922337203685，477.5807），正確率為貨幣單位的千分之十。 這個資料類型會對應至 .NET Framework 中的 `Decimal` 資料類型和 OLE DB 中的 DBTYPE_CY 資料類型。|  
|*日期*|儲存成雙精確度浮點數的日期資料。 整數部分為自 1899 年 12 月 30 日起的天數，而分數部分則為一天的分數部分。 這個資料類型會對應至 .NET Framework 中的 `DateTime` 資料類型和 OLE DB 中的 DBTYPE_DATE 資料類型。|  
|*雙精度浮點數*|在 -1.79E +308 到 1.79E +308 範圍中的雙精確度浮點數。 這個資料類型會對應至 .NET Framework 中的 `Double` 資料類型和 OLE DB 中的 DBTYPE_R8 資料類型。|  
|*Integer*|32 位元帶正負號的整數。 這個資料類型會對應至 .NET Framework 中的 `Int32` 資料類型和 OLE DB 中的 DBTYPE_I4 資料類型。|  
|*Single*|在 -3.40E +38 到 3.40E +38 範圍中的單精確度浮點數。 這個資料類型會對應至 .NET Framework 中的 `Single` 資料類型和 OLE DB 中的 DBTYPE_R4 資料類型。|  
|*SmallInt*|16 位元帶正負號的整數。 這個資料類型會對應至 .NET Framework 中的 `Int16` 資料類型和 OLE DB 中的 DBTYPE_I2 資料類型。|  
|*TinyInt*|8 位元帶正負號的整數。 這個資料類型會對應至 .NET Framework 中的 `SByte` 資料類型和 OLE DB 中的 DBTYPE_I1 資料類型。|  
|*UnsignedBigInt*|64 位元不帶正負號的整數。 這個資料類型會對應至 .NET Framework 中的 `UInt64` 資料類型和 OLE DB 中的 DBTYPE_UI8 資料類型。|  
|*unsignedInt*|32 位元不帶正負號的整數。 這個資料類型會對應至 .NET Framework 中的 `UInt32` 資料類型和 OLE DB 中的 DBTYPE_UI4 資料類型。|  
|*UnsignedSmallInt*|16 位元不帶正負號的整數。 這個資料類型會對應至 .NET Framework 中的 `UInt16` 資料類型和 OLE DB 中的 DBTYPE_UI2 資料類型。|  
|*WChar*|Unicode 字元的以 Null 結束資料流。 這個資料類型會對應至 .NET Framework 中的 `String` 資料類型和 OLE DB 中的 DBTYPE_WSTR 資料類型。|  
|*繼承*|資料類型`DataItem`中包含[來源](source-element-measure-assl.md)項目`Measure`項目。 **注意︰** 適用只`Measure`項目。|  
  
## <a name="see-also"></a>另請參閱  
 [屬性&#40;ASSL&#41;](properties-assl.md)  
  
  
