---
title: 安裝 ADO.NET Data Services 以支援資料摘要的 SharePoint 清單匯出 |Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f32527ae-f623-4e08-adfb-6d3262f5c2ac
caps.latest.revision: 6
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: d4241d56aa3257bd0ec2cddf4b439a4939f8ab9f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36032200"
---
# <a name="install-adonet-data-services-to-support-data-feed-exports-of-sharepoint-lists"></a>如何：安裝 ADO.NET Data Services 以支援 SharePoint 清單的資料摘要匯出  
  從 SharePoint 清單匯出資料摘要需要 ADO.NET Data Services。 SharePoint 2010 不會在 SharePoint 必要安裝程式中包含這個元件，所以您必須手動安裝它。  
  
 如果沒有此程序，當您嘗試使用匯出為資料摘要的 SharePoint 清單時，會出現下列錯誤：「基於安全理由，這份 XML 文件禁止使用 DTD。 若要啟用 DTD 處理，請將 XmlReaderSettings 上的 ProhibitDtd 屬性設定為 false，並且將這項設定傳入 XmlReader.Create 方法。」  
  
 使用下列程序，在您想要讓清單當做資料摘要匯出的每一部 SharePoint 伺服器上安裝 ADO.NET Data Services。  
  
### <a name="download-and-install-adonet-data-services"></a>下載及安裝 ADO.NET Data Services  
  
1.  移至適用於 SharePoint 2010 的硬體和軟體需求文件[硬體和軟體需求 (SharePoint 2010)](http://go.microsoft.com/fwlink/?LinkId=169734)  
  
2.  在**適用的軟體存取**，尋找連結的 ADO.NET Data Services 3.5 會對應到作業系統 （Windows Server 2008 SP2 或 Windows Server 2008 R2） 使用。  
  
3.  按一下該連結，並執行安裝程式來安裝服務。  
  
## <a name="see-also"></a>另請參閱  
 [PowerPivot for SharePoint 2010 安裝](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  