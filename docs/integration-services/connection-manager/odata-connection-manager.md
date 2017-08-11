---
title: "OData 連接管理員 |Microsoft 文件"
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3caa4372-aff3-4c0f-9ecd-97870948b8d0
caps.latest.revision: 9
f1_keywords:
- sql13.dts.designer.odatasource.connectionmanager.f1
- sql13.dts.designer.odataconnectionmanager.f1
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 8397673c7ed9dfe8ae02871f9077ed7286e49863
ms.openlocfilehash: b23a158bff546fd6ffb4208638c039d690379ce1
ms.contentlocale: zh-tw
ms.lasthandoff: 08/09/2017

---
# <a name="odata-connection-manager"></a>OData 連接管理員
  使用 OData 連接管理員連接到 OData 來源。 OData 來源元件會使用 OData 連接線理員連接到 OData 來源，並取用此服務中的資料。 如需詳細資訊，請參閱＜ [OData Source](../../integration-services/data-flow/odata-source.md)＞。  
  
## <a name="adding-an-odata-connection-manager-to-an-ssis-package"></a>將 OData 連接管理員加入 SSIS 封裝中  
 您可以使用三種方式，將新的 OData 連接管理員加入至 SSIS 封裝：  
  
-   按一下 [新增…]  按鈕 (位於 [OData 來源編輯器]   
  
-   在 **方案總管** 中，以滑鼠右鍵按一下 [連線管理員] 資料夾，然後按一下 [新增連線管理員] 。 針對 [連線管理員類型]  選取 [ODATA] 。  
  
-   以滑鼠右鍵按一下封裝設計師底部的 [連線管理員]  窗格，然後選取 [新增連接…] 。 針對 [連線管理員類型]  選取 [ODATA] 。  
  
## <a name="connection-manager-authentication"></a>連接管理員驗證  
 OData 連接管理員支援五種模式的驗證。  
  
-   Windows 驗證  
  
-   基本驗證 (使用使用者名稱和密碼)  

-   Microsoft Dynamics AX Online (使用使用者名稱和密碼)
  
-   Microsoft Dynamics CRM Online (使用使用者名稱和密碼)
  
-   Microsoft Online Services (使用使用者名稱和密碼)  
  
 如果是匿名存取，請選取 [Windows 驗證] 選項。  
  
### <a name="specifying-and-securing-credentials"></a>指定認證及維護認證安全  
 如果 OData 服務需要基本驗證，您可以在 [OData 連線管理員編輯器](../../integration-services/connection-manager/odata-connection-manager-editor.md)中指定使用者名稱和密碼。 您在編輯器中輸入的值會保存在封裝中。 密碼值會根據封裝保護等級進行加密。  
  
 有多個方式可將使用者名稱和密碼值參數化，或儲存到封裝外部。 例如，您可以使用參數，或是在使用 SQL Server Management Studio 執行封裝時直接設定連接管理員屬性，來執行這項操作。  
  
## <a name="odata-connection-manager-properties"></a>OData 連接管理員屬性  
 下列清單描述 OData 連接管理員的屬性。  
  
|||  
|-|-|  
|屬性|說明|  
|Url|服務文件的 URL。|  
|UserName|基本驗證所使用的使用者名稱。|  
|密碼|基本驗證所使用的密碼。|  
|ConnectionString|反映連接管理員的其他屬性。|  
  
## <a name="odata-connection-manager-editor"></a>OData 連線管理員編輯器
  使用 [OData 連線管理員編輯器] 對話方塊加入連線，或編輯現有的 OData 來源連線。  
  
### <a name="options"></a>選項。  
 **連線管理員名稱**  
 連接管理員的名稱。  
  
 **服務文件位置**  
 OData 服務的 URL。 例如：http://services.odata.org/V3/Northwind/Northwind.svc/。  
  
 **驗證**  
 請選取 [Windows 驗證]  或在 [基本驗證]  使用 **此使用者名稱和密碼**。 如果您選取第二個選項，請輸入 [使用者名稱]  和 [密碼] 。 
 
 現在還多了三個選項。 選取 [Microsoft Dynamics AX Online]  使用 Dynamics AX Online，選取 [Microsoft Dynamics CRM Online]  使用 Dynamics CRM Online，以及選取 [Microsoft Online Services]  使用 Microsoft Online Services。 如果選取三個選項其中之一，請輸入 **使用者名稱** 及 **密碼**。
  
 **測試連接**  
 按一下此按鈕，測試 OData 來源的連接。  
  
## <a name="see-also"></a>另請參閱  
 [OData 連線管理員編輯器](../../integration-services/connection-manager/odata-connection-manager-editor.md)  
  
  
