---
title: 測試使用者的權限 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 83a03b85-ea7f-4b4a-b19b-f7eca534ffae
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 0160628621049db7c9498ca931c675c080e78b8d
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2018
ms.locfileid: "52798300"
---
# <a name="test-a-user39s-permissions-master-data-services"></a>測試使用者的權限 (Master Data Services)
  在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，您可以建立測試使用者並登入 Web 應用程式來測試權限。當使用者嘗試存取 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] URL 時，就會驗證使用者的認證。 在 Internet Explorer 中，安全性設定會控制這項驗證是自動發生，還是使用者必須輸入使用者名稱和密碼。 若要變更這些設定，請完成下列步驟：  
  
### <a name="to-test-a-users-security"></a>測試使用者的安全性  
  
1.  在 Internet Explorer 7 及更新版本中，依序按一下 **[工具]**、 **[網際網路選項]** 和 **[安全性]** 索引標籤。  
  
2.  依序按一下 **[近端內部網路]** 和 **[自訂等級]** 按鈕。  
  
3.  在 **[使用者驗證]** 區段中，選擇 **[提示輸入使用者名稱及密碼]**。  
  
4.  下次您開啟瀏覽器視窗時，將提示您輸入使用者名和密碼。  
  
## <a name="see-also"></a>另請參閱  
 [安全性 &#40;Master Data Services&#41;](security-master-data-services.md)  
  
  
