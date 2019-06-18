---
title: 將程式碼新增至報表 (SSRS) | Microsoft Docs
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
helpviewer_keywords:
- code [Reporting Services]
- custom code [Reporting Services]
- expressions [Reporting Services], code
- adding code
- reports [Reporting Services], code
ms.assetid: 00ef8fc6-99fe-49b2-8a22-7eb475881dc4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: d66cb9fa3fdb3bdee5eb0f4fefbc282a9841f9a7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "65582028"
---
# <a name="add-code-to-a-report-ssrs"></a>將程式碼加入至報表 (SSRS)
  在任何運算式中，您可以呼叫自己的自訂程式碼。 您可以透過下列兩個方法來提供程式碼：  
  
-   將以 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 撰寫的程式碼直接內嵌在報表中。 如果程式碼參考的是非 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 或 <xref:System.Math> 的 <xref:System.Convert>，您即必須在報表中加入參考。 如需詳細資訊，請參閱 [將組件參考加入至報表 &#40;SSRS&#41;](../../reporting-services/report-design/add-an-assembly-reference-to-a-report-ssrs.md)。 如需可從程式碼建立之其他參考的詳細資訊，請參閱[報表設計師中運算式的自訂程式碼及組件參考 &#40;SSRS&#41;](../../reporting-services/report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)。  
  
-   藉由使用 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]來提供自訂程式碼組件。 如果您提供自訂組件，您必須同時將它安裝在您撰寫報表的電腦上及檢視報表的報表伺服器上。 如需詳細資訊，請參閱 [Using Custom Assemblies with Reports](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)。  
  
### <a name="to-add-embedded-code-to-a-report"></a>將內嵌程式碼加入報表中  
  
1.  在 [設計]  檢視中，以滑鼠右鍵按一下報表框線外面的設計介面，然後按一下 [報表屬性]  。  
  
2.  按一下 **[程式碼]** 。  
  
3.  在 **[自訂程式碼]** 中，輸入程式碼。 當報表執行時，程式碼中的錯誤會產生警告。 下列範例會建立名為 `ChangeWord` 的自訂函數，以 "`Bike`" 取代 "`Bicycle`" 一字。  
  
    ```  
    Public Function ChangeWord(ByVal s As String) As String  
       Dim strBuilder As New System.Text.StringBuilder(s)  
       If s.Contains("Bike") Then  
          strBuilder.Replace("Bike", "Bicycle")  
          Return strBuilder.ToString()  
          Else : Return s  
       End If  
    End Function  
    ```  
  
4.  下列範例示範如何在運算式中將名為 Category 的資料集欄位傳遞給這個函數：  
  
    ```  
    =Code.ChangeWord(Fields!Category.Value)  
    ```  
  
     如果您將此運算式加入至顯示類別目錄值的資料表資料格，則每當 "Bike" 一字位於該資料列的資料集欄位中時，此資料表資料格值就會改為顯示 "Bicycle" 一字。  
  
## <a name="see-also"></a>另請參閱  
 [報表屬性對話方塊、程式碼](https://msdn.microsoft.com/library/955d4b11-17b4-4f1c-9690-6e7af54caea7)   
 [運算式範例 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [參數集合參考 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/built-in-collections-parameters-collection-references-report-builder.md)  
  
  
