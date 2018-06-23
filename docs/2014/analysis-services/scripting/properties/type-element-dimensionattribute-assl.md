---
title: 輸入元素 (DimensionAttribute) (ASSL) |Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Type Element (DimensionAttribute)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: 64fce1f5-39b7-4d0a-ae60-21203a03bd0d
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 450f25e039a4efbc2a6ae4175faf396bfbfa9ff7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36136507"
---
# <a name="type-element-dimensionattribute-assl"></a>Type 元素 (DimensionAttribute) (ASSL)
  包含屬性的類型。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<DimensionAttribute>  
      ...  
   <Type>...</Type>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|字串 (列舉)|  
|預設值|*規則*|  
|基數|0-1：只能出現一次的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
 這個元素的值限制為下表所列的其中一個字串。  
  
|ReplTest1|描述|  
|-----------|-----------------|  
|*帳戶*|此屬性代表帳戶的名稱。|  
|*AccountNumber*|此屬性代表帳戶的號碼。|  
|*AccountType*|此屬性代表帳戶的類型。|  
|*位址*|此屬性代表地址。|  
|*AddressBuilding*|此屬性代表地址的大樓棟別識別碼。|  
|*AddressCity*|屬性代表地址的縣 (市)。|  
|*AddressCountry*|此屬性代表地址的國家或地區。|  
|*AddressFax*|此屬性代表傳真電話號碼。|  
|*AddressFloor*|此屬性代表地址的樓層識別碼。|  
|*AddressHouse*|屬性代表地址的門牌號碼。|  
|*AddressPhone*|屬性代表電話號碼。|  
|*AddressQuarter*|屬性代表地址的區。|  
|*AddressRoom*|屬性代表地址的室識別碼。|  
|*AddressStateOrProvince*|屬性代表地址的省份。|  
|*AddressStreet*|此屬性代表地址的街道名稱。|  
|*AddressZip*|此屬性代表地址的郵遞區號。|  
|*BOMResource*|此屬性代表用料表 (BOM) 的資源。|  
|*標題*|屬性代表標題。|  
|*CaptionAbbreviation*|屬性代表縮寫。|  
|*CaptionDescription*|屬性代表描述。|  
|*通路*|屬性代表通道。|  
|*縣 （市)*|屬性代表縣 (市)。|  
|*公司*|屬性代表公司。|  
|*大陸*|屬性代表大陸。|  
|*國家/地區*|屬性代表國家或地區。|  
|*郡*|屬性代表國家 (地區)。|  
|*CurrencyDestination*|屬性代表貨幣兌換的目的地貨幣。|  
|*CurrencyISOcode*|此屬性代表貨幣的 ISO 代碼。|  
|*CurrencName*|此屬性代表貨幣的名稱。|  
|*CurrencySource*|此屬性代表貨幣兌換的來源貨幣。|  
|*CustomerGroup*|此屬性代表客戶的群組。|  
|*CustomerHousehold*|此屬性代表客戶的家庭成員。|  
|*客戶*|屬性代表客戶。|  
|*日期*|屬性代表日期。|  
|*DateCanceled*|屬性代表取消日期。|  
|*DateDuration*|屬性代表持續時間。|  
|*DateEnded*|屬性代表結束日期。|  
|*DateModified*|屬性代表修改日期。|  
|*DateStart*|屬性代表開始日期。|  
|*DayOfHalfYears*|屬性代表半年中的日序數。|  
|*DayOfMonth*|屬性代表月中的日序數。|  
|*DayOfQuarter*|屬性代表季中的日序數。|  
|*DayOfTrimester*|屬性代表每四個月中的日序數。|  
|*DayOfWeek*|屬性代表週中的日序數。|  
|*DayOfYear*|屬性代表年中的日序數。|  
|*天*|屬性代表天數。|  
|*DaysOfTenDays*|此屬性代表十天週期中的日序數。|  
|*FiscalDay*|此屬性代表會計日曆中的天數。|  
|*FiscalDayOfHalfYears*|此屬性代表會計日曆中之半年的日序數。|  
|*FiscalDayOfMonth*|屬性代表會計日曆中之月的日序數。|  
|*FiscalDayOfQuarter*|屬性代表會計日曆中之季的日序數。|  
|*FiscalDayOfTrimester*|屬性代表會計日曆中之每四個月的日序數。|  
|*FiscalDayOfWeek*|屬性代表會計日曆中之週的日序數。|  
|*FiscalDayOfYear*|屬性代表會計日曆中之年的日序數。|  
|*FiscalHalfYears*|屬性代表會計日曆中的半年度。|  
|*FiscalHalfYearsOfYear*|屬性代表會計日曆中之年的半年度序數。|  
|*會計月份*|屬性代表會計日曆中的月份。|  
|*FiscalMonthOfHalfYears*|屬性代表會計日曆中之半年度的月序數。|  
|*FiscalMonthOfQuarter*|屬性代表會計日曆中之季的月序數。|  
|*FiscalMonthOfTrimester*|屬性代表會計日曆中之每四個月的月序數。|  
|*FiscalMonthOfYear*|屬性代表會計日曆中之年的月序數。|  
|*Fiscalquarter 和*|屬性代表會計日曆中的季數。|  
|*FiscalQuarterOfHalfYear*|屬性代表會計日曆中之半年的季序數。|  
|*FiscalQuarterOfYear*|屬性代表會計日曆中之年的季序數。|  
|*FiscalTrimester*|屬性代表會計日曆中的每四個月。|  
|*FiscalTrimesterOfYear*|屬性代表會計日曆中之年的每四個月序數。|  
|*FiscalWeek*|屬性代表會計日曆中的週。|  
|*FiscalWeekOfHalfYears*|屬性代表會計日曆中之半年的週序數。|  
|*FiscalWeekOfMonth*|屬性代表會計日曆中之月的週序數。|  
|*FiscalWeekOfQuarter*|屬性代表會計日曆中之季的週序數。|  
|*FiscalWeekOfTrimester*|屬性代表會計日曆中之每四個月的週序數。|  
|*FiscalWeekOfYear*|屬性代表會計日曆中之年的週序數。|  
|*FiscalYear*|屬性代表會計日曆中的年。|  
|*FormattingColor*|屬性代表格式化使用的色彩。|  
|*FormattingFont*|屬性代表格式化使用的字型。|  
|*FormattingFontEffects*|屬性代表格式化使用的字型效果。|  
|*FormattingFontSize*|屬性代表格式化使用的字型大小。|  
|*FormattingOrder*|屬性代表格式化使用的順序。|  
|*FormattingSubtotal*|屬性代表小計。|  
|*GeoBoundaryBottom*|屬性代表地理界限的最底部值。|  
|*GeoBoundaryFront*|屬性代表地理界限的最前方值。|  
|*GeoBoundaryLeft*|屬性代表地理界限的最左方值。|  
|*GeoBoundaryPolygon*|屬性代表地理界限的多邊形定義。|  
|*GeoBoundaryRear*|屬性代表地理界限的最後方值。|  
|*GeoBoundaryRight*|屬性代表地理界限的最右方值。|  
|*GeoBoundaryTop*|屬性代表地理界限的最頂部值。|  
|*GeoCentroidX*|屬性代表地理區域的 X 軸距心。|  
|*GeoCentroidY*|屬性代表地理區域的 Y 軸距心。|  
|*GeoCentroidZ*|屬性代表地理區域的 Z 軸距心。|  
|*HalfYears*|屬性代表半年度。|  
|*HalfYearsOfYear*|屬性代表年中的半年度序數。|  
|*小時*|此屬性代表小時。|  
|*Id*|此屬性代表識別碼或索引鍵。|  
|*IsHoliday*|此屬性會指出日期是否為假日。|  
|*ISO8601DayOfWeek*|此屬性代表 ISO 8601 日曆中之週的日序數。|  
|*ISO8601DayOfYear*|屬性代表 ISO 8601 日曆中之年的日序數。|  
|*ISO8601Days*|屬性代表 ISO 8601 日曆中的天數。|  
|*ISO8601Week*|屬性代表 ISO 8601 日曆中的週。|  
|*ISO8601WeekOfYear*|屬性代表 ISO 8601 日曆中之年的週序數。|  
|*ISO8601Year*|此屬性代表 ISO 8601 日曆中的年度。|  
|*IsWeekDay*|此屬性會指出日期是否為週一至週五。|  
|*IsWorkingDay*|此屬性會指出日期是否為工作日。|  
|*ManufacturingDay*|屬性代表製造日曆中的天數。|  
|*ManufacturingDayOfHalfYears*|屬性代表製造日曆中之半年的日序數。|  
|*ManufacturingDayOfMonth*|屬性代表製造日曆中之月的日序數。|  
|*ManufacturingDayOfQuarter*|屬性代表製造日曆中之季的日序數。|  
|*ManufacturingDayOfTrimester*|屬性代表製造日曆中之每四個月的日序數。|  
|*ManufacturingDayOfWeek*|屬性代表製造日曆中之週的日序數。|  
|*ManufacturingDayOfYear*|屬性代表製造日曆中之年的日序數。|  
|*ManufacturingHalfYears*|屬性代表製造日曆中的半年度。|  
|*ManufacturingHalfYearsOfYear*|屬性代表製造日曆中之年的半年度序數。|  
|*ManufacturingMonth*|屬性代表製造日曆中的月份。|  
|*ManufacturingMonthOfHalfYears*|屬性代表製造日曆中之半年的月序數。|  
|*ManufacturingMonthOfQuarter*|屬性代表製造日曆中之季的月序數。|  
|*ManufacturingMonthOfTrimester*|屬性代表製造日曆中之每四個月的月序數。|  
|*ManufacturingMonthOfYear*|屬性代表製造日曆中之年的月序數。|  
|*ManufacturingQuarter*|屬性代表製造日曆中的季數。|  
|*ManufacturingQuarterOfHalfYear*|屬性代表製造日曆中之半年的季序數。|  
|*ManufacturingQuarterOfYear*|屬性代表製造日曆中之年的季序數。|  
|*ManufacturingTrimester*|屬性代表製造日曆中的每四個月。|  
|*ManufacturingTrimesterOfYear*|屬性代表製造日曆中之年的每四個月序數。|  
|*ManufacturingWeek*|屬性代表製造日曆中的週。|  
|*ManufacturingWeekOfHalfYears*|屬性代表製造日曆中之半年的週序數。|  
|*ManufacturingWeekOfMonth*|屬性代表製造日曆中之月的週序數。|  
|*ManufacturingWeekOfQuarter*|屬性代表製造日曆中之季的週序數。|  
|*ManufacturingWeekOfTrimester*|屬性代表製造日曆中之每四個月的週序數。|  
|*ManufacturingWeekOfYear*|屬性代表製造日曆中之年的週序數。|  
|*ManufacturingYear*|屬性代表製造日曆中的年。|  
|*Minutes*|屬性代表分鐘數。|  
|*MonthOfHalfYears*|屬性代表半年的月序數。|  
|*MonthOfQuarter*|屬性代表季的月序數。|  
|*MonthOfTrimester*|屬性代表每四個月的月序數。|  
|*MonthOfYear*|屬性代表年中的月序數。|  
|*幾個月*|此屬性代表月數。|  
|*OrganizationalUnit*|此屬性代表組織單位。|  
|*OrgTitle*|此屬性代表組織標題。|  
|*PercentOwnership*|此屬性代表擁有權的百分比。|  
|*PercentVoteRight*|此屬性代表投票權的百分比。|  
|*人員*|屬性代表個人。|  
|*PersonContact*|屬性代表個人的連絡資訊。|  
|*PersonDemographic*|此屬性代表個人的人口統計資訊。|  
|*PersonFirstName*|此屬性代表個人的名字。|  
|*PersonFullName*|此屬性代表個人的全名。|  
|*PersonLastName*|此屬性代表個人的姓氏。|  
|*PersonMiddleName*|此屬性代表個人的中間名。|  
|*PhysicalColor*|屬性代表色彩。|  
|*PhysicalDensity*|屬性代表密度。|  
|*PhysicalDepth*|屬性代表深度。|  
|*PhysicalHeight*|屬性代表高度。|  
|*PhysicalSize*|屬性代表大小。|  
|*PhysicalVolume*|屬性代表體積。|  
|*PhysicalWeight*|屬性代表重量。|  
|*PhysicalWidth*|屬性代表寬度。|  
|*點*|屬性代表點。|  
|*郵遞區號*|屬性代表郵遞區號。|  
|*產品*|屬性代表產品。|  
|*ProductBrand*|此屬性代表產品品牌。|  
|*ProductCategory*|此屬性代表產品類別目錄。|  
|*ProductGroup*|此屬性代表產品群組。|  
|*ProductSKU*|此屬性代表產品存貨保持單元 (SKU)。|  
|*ProjectCode*|此屬性代表專案代碼。|  
|*Projectcompletion*|此屬性代表專案的完成狀態。|  
|*ProjectEnddate*|此屬性代表專案結束日期。|  
|*專案名稱*|此屬性代表專案名稱。|  
|*ProjectStartDate*|此屬性代表專案開始日期。|  
|*升級*|屬性代表促銷。|  
|*QtyRangeHigh*|屬性代表數量範圍的最大值。|  
|*QtyRangeLow*|屬性代表數量範圍的最小值。|  
|*量化*|屬性代表數量的屬性。|  
|*QuarterOfHalfYear*|屬性代表半年中的季序數。|  
|*QuarterOfYear*|屬性代表年中的季序數。|  
|*數個季度*|屬性代表季數。|  
|*速率*|屬性代表比率。|  
|*RateType*|屬性代表比率類型。|  
|*區域*|屬性代表客戶自訂的區域。|  
|*規則*|屬性代表一般屬性。|  
|*RelationToParent*|屬性代表與父系的關聯性。|  
|*ReportingDay*|屬性代表報表日曆中的天數。|  
|*ReportingDayOfHalfYears*|屬性代表報表日曆中之半年的日序數。|  
|*ReportingDayOfMonth*|屬性代表報表日曆中之月的日序數。|  
|*ReportingDayOfQuarter*|屬性代表報表日曆中之季的日序數。|  
|*ReportingDayOfTrimester*|屬性代表報表日曆中之每四個月的日序數。|  
|*ReportingDayOfWeek*|屬性代表報表日曆中之週的日序數。|  
|*ReportingDayOfYear*|屬性代表報表日曆中之年的日序數。|  
|*ReportingHalfYears*|屬性代表報表日曆中的半年度。|  
|*ReportingHalfYearsOfYear*|屬性代表報表日曆中之年的半年度序數。|  
|*ReportingMonth*|屬性代表報表日曆中的月份。|  
|*ReportingMonthOfHalfYears*|屬性代表報表日曆中之半年的月序數。|  
|*ReportingMonthOfQuarter*|屬性代表報表日曆中之季的月序數。|  
|*ReportingMonthOfTrimester*|屬性代表報表日曆中之每四個月的月序數。|  
|*ReportingMonthOfYear*|屬性代表報表日曆中之年的月序數。|  
|*ReportingQuarter*|屬性代表報表日曆中的季數。|  
|*ReportingQuarterOfHalfYear*|屬性代表報表日曆中之半年的季序數。|  
|*ReportingQuarterOfYear*|屬性代表報表日曆中之年的季序數。|  
|*ReportingTrimester*|屬性代表報表日曆中的每四個月。|  
|*ReportingTrimesterOfYear*|屬性代表報表日曆中之年的每四個月序數。|  
|*ReportingWeek*|屬性代表報表日曆中的週。|  
|*ReportingWeekOfHalfYears*|屬性代表報表日曆中之半年的週序數。|  
|*ReportingWeekOfMonth*|屬性代表報表日曆中之月的週序數。|  
|*ReportingWeekOfQuarter*|屬性代表報表日曆中之季的週序數。|  
|*ReportingWeekOfTrimester*|屬性代表報表日曆中之每四個月的週序數。|  
|*ReportingWeekOfYear*|屬性代表報表日曆中之年的週序數。|  
|*ReportingYear*|屬性代表報表日曆中的年。|  
|*代表*|此屬性表示代表。|  
|*案例*|此屬性代表狀況。|  
|*秒*|此屬性代表秒數。|  
|*序列*|屬性代表順序屬性。|  
|*ShortCaption*|屬性代表簡短標題。|  
|*StateOrProvince*|屬性代表省份。|  
|*TenDayOfHalfYears*|屬性代表半年的十天週期序數。|  
|*TenDayOfQuarter*|屬性代表季的十天週期序數。|  
|*TenDayOfTrimester*|屬性代表每四個月的十天週期序數。|  
|*TenDayOfYear*|屬性代表年的十天週期序數。|  
|*TenDays*|屬性代表十天週期。|  
|*TenDaysOfMonth*|屬性代表月的十天週期序數。|  
|*每四個月*|屬性代表每四個月。|  
|*TrimesterOfYear*|屬性代表年的每四個月序數。|  
|*UndefinedTime*|此屬性代表未定義的時間週期。|  
|*公用程式*|此屬性代表公用程式。|  
|*版本*|此屬性代表版本。|  
|*WebHtml*|此屬性代表 HTML 內容。|  
|*WebMailAlias*|屬性代表電子郵件別名。|  
|*WebUrl*|屬性代表 URL 位址。|  
|*WebXmlOrXsl*|屬性代表 XML 或 XSL 內容。|  
|*WeekOfHalfYears*|屬性代表半年的週序數。|  
|*WeekOfMonth*|屬性代表月的週序數。|  
|*WeekOfQuarter*|屬性代表季的週序數。|  
|*WeekOfTrimester*|屬性代表每四個月的週序數。|  
|*WeekOfYear*|屬性代表年的週序數。|  
|*週*|此屬性代表週數。|  
|*年*|此屬性代表年度。|  
  
 在「分析管理物件」(AMO) 物件模型中對應至 `Type` 允許值的列舉是 <xref:Microsoft.AnalysisServices.AttributeType>。  
  
 對應目的父代的項目`Type`在 「 分析管理物件 (AMO) 物件模型而言， <xref:Microsoft.AnalysisServices.DimensionAttribute>。  
  
## <a name="see-also"></a>另請參閱  
 [屬性項目&#40;ASSL&#41;](../collections/attributes-element-assl.md)   
 [維度元素&#40;ASSL&#41;](../objects/dimension-element-assl.md)   
 [屬性&#40;ASSL&#41;](properties-assl.md)  
  
  