---
title: 建立網域系統管理員-Analytics Platform System |Microsoft 文件
description: 某些作業需要 Analytics Platform System 網域系統管理員權限。 本節將說明如何建立其他的應用裝置的網域系統管理員。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 73eff52cb6e583383f13334e78012721a20a3e25
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="create-an-aps-domain-administrator"></a>建立 AP 網域系統管理員
某些作業需要 Analytics Platform System 網域系統管理員權限。 本節將說明如何建立其他的應用裝置的網域系統管理員。  
  
## <a name="create-a-domain-administrator"></a>建立網域系統管理員  
若要有足夠的權限來設定所有的 APS 節點中，執行使用者**AP Configuration Manager** (`dwconfig.exe`) 必須是成員**Domain Admins**群組。 若要啟動及停止 AP 服務，使用者必須是成員**PdwControlNodeAccess**群組。  
  
#### <a name="to-add-a-user-to-the-domain-admins-group"></a>將使用者新增至 Domain Admins 群組  
  
1.  登入作用中的 AD 節點 **(*appliance_domain*-AD01**或 ***appliance_domain *-ad02 移**) 使用現有的應用裝置網域系統管理員帳戶。  
  
2.  在 [開始] 功能表上，按一下 [執行]。 在**開啟**方塊中，輸入**dsa.msc**。 按一下 **[確定]**。  
  
3.  在**Active Directory 使用者和電腦**程式中，以滑鼠右鍵按一下**使用者**，指向 **新增**，然後按一下 **使用者**。  
  
4.  在**新增物件-使用者**對話方塊中，完成新使用者的描述，然後按一下 **下一步**。  
  
    完成 [密碼] 對話方塊，然後按一下**下一步**。  
  
    > [!WARNING]  
    > SQL Server PDW 不支援在網域系統管理員或本機系統管理員密碼貨幣符號字元 （$）。 包含貨幣符號的密碼仍會有效，並加以使用，但可能會封鎖升級與維護的活動  
  
    確認新的使用者描述，然後按一下**完成**。  
  
5.  在使用者清單中，按兩下新的使用者開啟使用者的 [內容] 對話方塊。  
  
6.  在**隸屬**索引標籤上，按一下 **新增**。  
  
    型別**Domain Admins。PdwControlNodeAccess** ，然後按一下 **檢查名稱**。 按一下 **[確定]**。  
  
    這會將新使用者**Domain Admins**群組和**PdwControlNodeAccess**群組。 按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
[啟動 Configuration Manager &#40;Analytics Platform System&#41;](launch-the-configuration-manager.md)  
  
