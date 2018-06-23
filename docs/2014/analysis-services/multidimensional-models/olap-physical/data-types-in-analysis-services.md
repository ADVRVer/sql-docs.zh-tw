---
title: Analysis Services 中的資料類型 |Microsoft 文件
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 910be4f4-3010-41cd-9fdc-f0a79a0ce823
caps.latest.revision: 9
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 7f5c4b371bfedda50a59fe9c0fa945739a320837
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36035992"
---
# <a name="data-types-in-analysis-services"></a>Analysis Services 中的資料類型
  所有<xref:Microsoft.AnalysisServices.DataItem>物件[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]支援下列子集`System.Data.OleDb.OleDbType`。 若要設定或讀取的資料類型，請使用[DataItem 資料類型&#40;ASSL&#41;](../../scripting/data-type/dataitem-data-type-assl.md)。  
  
## <a name="supported-data-types"></a>支援的資料類型  
  
|||  
|-|-|  
|BigInt|64 位元帶正負號的整數。 *BigInt*實值類型代表值範圍從負數 9223372036854775808 到正數 9,223,372,036,854,775,807 的整數。|  
|二進位|二進位資料的資料流**位元組**型別。 **位元組**實值型別，表示不帶正負號的整數，且範圍從 0 到 255 的值。|  
|布林|這個類型的執行個體具有 `true` 或 `false` 值。|  
|CURRENCY|A*貨幣*值範圍從-922,337,203,685,477.5808 到 + 922337203685，477.5807 精確度為貨幣單位 （四個小數位數） 的千分之十。|  
|date|日期和時間資料，儲存為雙精確度浮點數。 整數部分為自 1899 年 12 月 30 日起的天數，而分數部分則為一天的分數部分或當天的時間。|  
|Double|浮點數，範圍在 -1.79769313486232E +308 到 1.79769313486232E +308 之間。 Double 值儲存最多有效位數為 15 個小數位數的數字資訊。|  
|Integer|32 位元帶正負號的整數，代表範圍從複數 2,147,483,648 到正數 2,147,483,647 的帶正負號的整數值。|  
|Single|浮點數，範圍在 - 3.4028235E +38 到 3.4028235E +38 之間。 Single 值儲存最多有效位數為 7 個小數位數的數字資訊。|  
|Smallint|16 位元帶正負號的整數。 *Smallint*實值類型代表帶正負號的整數值範圍從負數 32768 到正數 32767。|  
|Tinyint|8 位元帶正負號的整數。 Tinyint 值類型代表範圍從負數 128 到正數 127 的整數值。|  
|UnsignedBigInt|64 位元不帶正負號的整數。 *UnsignedBigInt*實值類型代表不帶正負號的整數值範圍從 0 到 18446744073709551615。|  
|UnsignedInt|32 位元不帶正負號的整數。 *UnsignedInt*實值類型代表範圍從 0 到 4,294,967,295 的值不帶正負號的整數。|  
|UnsignedSmallInt|16 位元不帶正負號的整數。 *UnsignedSmallInt*實值類型代表不帶正負號的整數值範圍從 0 到 65535 之間。|  
|UnsignedTinyInt|8 位元不帶正負號的整數。 *UnsignedTinyInt*值類型代表不帶正負號的整數，且範圍從 0 到 255 的值|  
|WChar|Unicode 字元的以 Null 結束資料流。 A *WChar*是用來代表文字的 Unicode 字元的循序集合。|  
  
## <a name="amo-validations-on-data-types"></a>資料類型的 AMO 驗證  
 下表列出分析管理物件 (AMO) 對某些繫結所做的額外驗證：  
  
|Object|繫結|允許的資料類型|  
|------------|-------------|------------------------|  
|DimensionAttribute|KeyColumns|二進位以外的所有資料類型|  
||NameColumn|僅 WChar|  
||SkippedLevelsColumn|僅限整數類型：BigInt、整數、SmallInt、TinyInt、UnsignedBigInt、UnsignedInt、UnsignedSmallInt、UnsignedTinyInt|  
||CustomRollupColumn|僅 WChar|  
||CustomRollupPropertiesColumn|僅 WChar|  
||UnaryOperatorColumn|僅 WChar|  
||ValueColumn|All|  
|AttributeTranslation|CaptionColumn|僅 WChar|  
|ScalarMiningStructureColumn|KeyColumns|二進位以外的所有資料類型|  
||NameColumn|僅 WChar|  
|TableMiningStructureColumn|ForeignKeyColumns|二進位以外的所有資料類型|  
|MeasureGroupAttribute|KeyColumns|二進位以外的所有資料類型|  
|相異計數量值|來源|BigInt、貨幣、Double、整數、Single、SmallInt、TinyInt、UnsignedBigInt、UnsignedInt、UnsignedSmallInt、UnsignedTinyInt|  
  
  