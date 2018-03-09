---
title: "管理連接與工作階段 (XMLA) |Microsoft 文件"
ms.custom: 
ms.date: 02/14/2018
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- statefulness [XML for Analysis]
- statelessness [XML for Analysis]
- XML for Analysis, sessions
- states [XML for Analysis]
- XMLA, sessions
- sessions [XML for Analysis]
ms.assetid: b83bb3ff-09be-4fda-9d1d-6248e04ffb21
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 761618d7a0d651fb24257e03c5fcb261fde051c6
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2018
---
# <a name="managing-connections-and-sessions-xmla"></a>管理連接與工作階段 (XMLA)
  *Statefulness*是在伺服器保留之身分識別與內容的用戶端方法呼叫之間的條件。 *Statelessness*是在伺服器不會記住之身分識別與內容的用戶端方法呼叫完成之後的條件。  
  
 若要提供 statefulness，XML for Analysis (XMLA) 支援*工作階段*，允許一系列陳述式一起執行。 這樣一系列的陳述式範例，將會建立用於後續查詢的導出成員。  
  
 一般而言，在 XMLA 中的工作階段會遵循 OLE DB 2.6 規格所述的下列行為：  
  
-   工作階段定義交易和命令內容範圍。  
  
-   在單一工作階段的內容中可以執行多個命令。  
  
-   支援 XMLA 內容中的交易是透過提供者特有的命令，以傳送[Execute](../../analysis-services/xmla/xml-elements-methods-execute.md)方法。  
  
 XMLA 定義了一個方法，可支援在 Web 環境中的工作階段，其所使用的模式類似於分散式撰寫及版本處理 (DAV) 通訊協定所使用的方法，可在鬆散偶合的環境中實作鎖定。 這個實作與 DAV 相似，因為其允許提供者基於各種理由 (例如，逾時或是連接錯誤) 使工作階段過期。 當再度支援工作階段時，Web 服務必須知道並準備處理必須重新啟動之中斷的命令集。  
  
 World Wide Web Consortium (W3C) 簡易物件存取通訊協定 (SOAP) 規格建議使用 SOAP 標頭，在 SOAP 訊息上面建立新的通訊協定。 下表列出 XMLA 為起始、維護和關閉工作階段，所定義的 SOAP 標頭元素與屬性。  
  
|SOAP 標頭|Description|  
|-----------------|-----------------|  
|BeginSession|此標頭要求提供者建立新的工作階段。 提供者應該建構新的工作階段，並在 SOAP 回應中，將工作階段識別碼與 Session 標頭一起傳回。|  
|SessionId|值區域包含的工作階段識別碼，必須用於工作階段其餘部分的每個方法呼叫。 在 SOAP 回應中的提供者會傳送這個標記，而用戶端也必須將這個屬性與每個 Session 標頭元素一起傳送。|  
|Session|對於每個發生在工作階段的方法呼叫，都必須使用這個標頭，而且在標頭的值區域中必須包括工作階段識別碼。|  
|EndSession|若要結束工作階段，請使用這個標頭。 值區域必須包括工作階段識別碼。|  
  
> [!NOTE]  
>  工作階段識別碼並不保證工作階段會維持有效狀態。 如果工作階段過期 (例如，如果逾時或是連接中斷)，提供者可以選擇結束和回復該工作階段的動作。 因此，所有後續從用戶端對工作階段識別碼發出的方法呼叫都會失敗，並產生指出工作階段無效的錯誤。 用戶端應該要處理這個狀況，並準備從頭開始，重新傳送工作階段方法呼叫。  
  
## <a name="legacy-code-example"></a>舊版程式碼範例  
 以下範例將示範如何支援工作階段。  
  
1.  若要開始工作階段，請將 SOAP 中的 BeginSession 標頭從用戶端加入輸出 XMLA 方法。 值區域一開始是空白的，因為還不知道工作階段識別碼。  
  
    ```  
    <SOAP-ENV:Envelope  
       xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"  
       SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">  
       <SOAP-ENV:Header>  
          <XA:BeginSession  
             xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
             xsi:type="xsd:int"  
             mustUnderstand="1"/>  
       </SOAP-ENV:Header>  
       <SOAP-ENV:Body>  
          ...<!-- Discover or Execute call goes here.-->  
       </SOAP-ENV:Body>  
    </SOAP-ENV:Envelope>  
    ```  
  
2.  從提供者的 SOAP 回應訊息包含的工作階段識別碼傳回標頭區域中，使用 XMLA 標頭標記\<SessionId >。  
  
    ```  
    <SOAP-ENV:Header>  
       <XA:Session  
          xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
          SessionId="581"/>  
    </SOAP-ENV:Header>  
    ```  
  
3.  工作階段中的每個方法呼叫都必須加入 Session 標頭，以包含從提供者傳回的工作階段識別碼。  
  
    ```  
    <SOAP-ENV:Header>  
       <XA:Session  
          xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
          mustUnderstand="1"  
          SessionId="581"/>  
    </SOAP-ENV:Header>  
    ```  
  
4.  工作階段完成時， \<EndSession > 標記會使用包含相關的工作階段識別碼值。  
  
    ```  
    <SOAP-ENV:Header>  
       <XA:EndSession  
          xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
          xsi:type="xsd:int"  
          mustUnderstand="1"  
          SessionId="581"/>  
    </SOAP-ENV:Header>  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [使用 Analysis Services 中的 XMLA 進行開發](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
