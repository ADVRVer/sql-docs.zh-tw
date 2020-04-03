---
title: 使用 Try 和 Catch 區塊 | Microsoft Docs
description: 了解如何透過使用 try/catch 區塊來套用適當的例外狀況處理，以針對無效要求提供另一層保護。
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service-net-framework-exception-handling
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], try/catch blocks
- try/catch blocks [Reporting Services]
ms.assetid: a7a9ef53-e3b6-4bf7-81f3-d85615954e6f
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 51f6c4d3cbc7751df8e7685835057c4c5e58daa9
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2020
ms.locfileid: "80216354"
---
# <a name="using-try-and-catch-blocks"></a>使用 Try 和 Catch 區塊
  在您將條件陳述式加入程式碼，以限制對報表伺服器的無效要求之後，應該透過使用 Try/Catch 區塊，來提供適當的例外狀況處理。 這個技術可以針對無效的要求提供另一層的保護。 如果對報表伺服器的要求是包含在 Try 區塊中，而且該要求造成報表伺服器擲回例外狀況，則在 Catch 區塊中會抓住例外狀況，因此可防止應用程式非預期地結束。 一旦捕捉到例外狀況，您可以使用例外狀況來指示使用者執行不一樣的動作，或只是以適當的方式讓使用者知道已發生錯誤。 接著您可以使用 Finally 區塊來清除任何資源。 理想上，您應該產生一般的例外狀況處理計劃，來避免 Try/Catch 區塊不必要的複製。  
  
 下列範例使用 Try/Catch 區塊來增強例外狀況處理程式碼的可靠性。  
  
```  
// C#  
private void PublishReport()  
{  
   int index;  
   string reservedChar;  
   string message;  
  
   // Check the text value of the name text box for "/",  
   // a reserved character  
   index = nameTextBox.Text.IndexOf(@"/");  
  
   if ( index != -1) // The text contains the character  
   {  
      reservedChar = nameTextBox.Text.Substring(index, 1);  
      // Build a user-friendly error message  
      message = "The name of the report cannot contain the reserved character " +  
         "\"" + reservedChar + "\". " +  
         "Please enter a valid name for the report. " +  
         "For more information about reserved characters, " +  
         "consult the online documentation";  
  
      MessageBox.Show(message, "Invalid Input Error");  
   }  
   else // Publish the report  
   {  
      Byte[] definition = null;  
      Warning[] warnings = {};  
      string name = nameTextBox.Text;  
  
      try  
      {  
         FileStream stream = File.OpenRead("MyReport.rdl");  
         definition = new Byte[stream.Length];  
         stream.Read(definition, 0, (int) stream.Length);  
         stream.Close();  
         // Create report with user-defined name  
         rs.CreateCatalogItem("Report", name, "/Samples", false, definition, null, out warnings);  
         MessageBox.Show("Report: {0} created successfully", name);  
      }  
  
      // Catch expected exceptions beginning with the most specific,  
      // moving to the least specific  
      catch(IOException ex)  
      {  
         MessageBox.Show(ex.Message, "File IO Exception");  
      }  
  
      catch (SoapException ex)  
      {  
         // The exception is a SOAP exception, so use  
         // the Detail property's Message element.  
         MessageBox.Show(ex.Detail["Message"].InnerXml, "SOAP Exception");   
      }  
  
      catch (Exception ex)  
      {  
         MessageBox.Show(ex.Message, "General Exception");  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [Reporting Services 中的例外狀況處理簡介](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Reporting Services SoapException 類別](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)  
  
  
