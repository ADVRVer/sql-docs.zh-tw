---
description: 選取 [從 &lt; 結構] &gt; 。例
title: 選取 [從 &lt; 結構] &gt; 。案例 |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: cf8afcdf84c5d33e91971c58dff5c1f93c68fd08
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/05/2020
ms.locfileid: "91726125"
---
# <a name="select-from-ltstructuregtcases"></a>選取 [從 &lt; 結構] &gt; 。例
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  傳回用於建立採礦結構的案例。  
  
 如果結構上未啟用鑽研，則陳述式會失敗。 同時，如果使用者沒有採礦結構的鑽研權限，陳述式將會失敗。  
  
 在中 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，根據預設會啟用新的採礦結構的「鑽取」。 若要確認是否已針對特定結構啟用「鑽取」，請檢查 **CacheMode** 屬性的值是否設定為 **KeepTrainingCases**。  
  
 如果 **CacheMode** 的值變更為 **>clearafterprocessing**，則會從快取中清除結構案例，而且您無法使用「鑽取」。  
  
> [!NOTE]  
>  您無法使用資料採礦延伸模組 (DMX)，在採礦結構上啟用或停用鑽研。  
  
## <a name="syntax"></a>語法  
  
```  
  
SELECT [TOP n] <expression list> FROM <structure>.CASES  
[WHERE <condition expression>][ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>引數  
 *n*  
 選擇性。 指定要傳回多少資料列的整數。  
  
 *運算式清單*  
 逗號分隔的運算式清單。  
  
 運算式可以包含資料行識別碼、使用者定義函數，以及 VBA 函數。  
  
 *結構*  
 結構的名稱。  
  
 *條件運算式*  
 限制從資料行清單傳回之值的條件。  
  
 *expression*  
 選擇性。 傳回純量值的運算式。  
  
## <a name="remarks"></a>備註  
 如果同時在模型和結構上都啟用鑽研，具有採礦結構和模型之鑽研權限的任何角色成員都可以使用下列語法，傳回不包含在模型中的結構資料行：  
  
```  
SELECT StructureColumn('<column name>') FROM <model>.CASES  
```  
  
 因此，若要保護敏感性資料或個人資訊，您應該將資料來源 view 視為遮罩個人資訊，並只在必要時授與 **AllowDrillthrough** 許可權給採礦結構或採礦模型。  
  
## <a name="examples"></a>範例  
 下列範例是根據以資料庫為基礎的採礦結構、目標郵寄以及 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 相關聯的採礦模型。 如需詳細資訊，請參閱 [基本資料採礦教學](/previous-versions/sql/sql-server-2016/ms167167(v=sql.130))課程。  
  
### <a name="example-1-drill-through-to-structure-cases"></a>範例 1：鑽研結構案例  
 下列範例會傳回採礦結構「目標郵寄」中，最舊的 500 位客戶的清單。 此查詢會傳回採礦模型中的所有資料行，但會將資料列限制為購買自行車的客戶，並以年齡加以排序。 您也可以編輯運算式清單，僅傳回您需要的資料行。  
  
```  
SELECT TOP 500 *  
FROM [Targeted Mailing].Cases  
WHERE [Bike Buyer] = 1  
ORDER BY Age DESC;  
```  
  
### <a name="example-2-drillthrough-to-test-or-training-cases-only"></a>範例 2：僅鑽研測試或培訓案例  
 下列範例會針對為測試而保留的「目標郵寄」，傳回結構案例的清單。 如果採礦結構不包含鑑效組測試集，系統預設會將所有案例視為培訓案例，因此，此查詢會傳回 0 個案例。  
  
```  
SELECT [Customer Key], Gender, Age  
FROM [Targeted Mailing].Cases  
WHERE IsTestCase();  
```  
  
 若要傳回培訓案例，取代函數 `IsTrainingCase()`。  
  
## <a name="see-also"></a>另請參閱  
 [選取 &#40;DMX&#41;](../dmx/select-dmx.md)   
 [資料採礦延伸模組 &#40;DMX&#41; 資料定義語句](../dmx/dmx-statements-data-definition.md)   
 [資料採礦延伸模組 &#40;DMX&#41; 資料動作陳述式](../dmx/dmx-statements-data-manipulation.md)   
 [資料採礦延伸模組 &#40;DMX&#41; 陳述式參考](../dmx/data-mining-extensions-dmx-statements.md)  
  
