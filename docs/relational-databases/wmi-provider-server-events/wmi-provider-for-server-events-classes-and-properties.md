---
title: WMI Provider for Server Events 類別和屬性 |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- event classes [WMI]
- WMI Provider for Server Events, events listed
- classes [WMI]
ms.assetid: e2916cd7-a3ed-41e6-97b4-2ee060754cbe
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 3673ee3d837179984c4221e1aa2509f67643dfb4
ms.sourcegitcommit: 6c9d35d03c1c349bc82b9ed0878041d976b703c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2018
ms.locfileid: "51217096"
---
# <a name="wmi-provider-for-server-events-classes-and-properties"></a>伺服器事件類別和屬性的 WMI 提供者
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  下列伺服器事件會組成伺服器事件之 WMI 提供者的程式撰寫模型。 有兩個主要類別目錄的事件，可以針對提供者發出 WQL 查詢來查詢這些事件。 這些是資料定義語言 (DDL) 事件和追蹤事件。 也可以查詢 QUEUE_ACTIVATION 和 BROKER_QUEUE_DISABLED Service Broker 事件。 請注意下列樹狀圖表的內含本質。 例如，DDL_ASSEMBLY_EVENTS 事件包含任何 ALTER_ASSEMBLY、CREATE_ASSEMBLY 和 DROP_ASSEMBLY 事件。 同樣地，TRC_FULL_TEXT 事件包含任何 FT_CRAWL_ABORTED、FT_CRAWL_STARTED 和 FT_CRAWL_STOPPED 事件。 ALL_EVENTS 涵蓋所有 DDL 事件、追蹤事件、QUEUE_ACTIVATION 和 BROKER_QUEUE_DISABLED。  
  
 若要得知可以從事件或事件群組查詢哪些屬性，請參考事件結構描述。 根據預設，事件結構描述會安裝在以下目錄：[!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]Tools\Binn\schemas\sqlserver\2006\11\events\events.xsd。  
  
 或者，您可以參考在發行的事件結構描述[ http://schemas.microsoft.com/sqlserver ](http://go.microsoft.com/fwlink/?linkid=43100)。  
  
 例如，藉由參考 ALTER_DATABASE 事件，您將了解它的父事件為 DDL_SERVER_LEVEL_EVENTS，而其屬性可以**TSQLCommand**並**DatabaseName**。 事件也會繼承的屬性**SQLInstance**， **PostTime**， **ComputerName**， **SPID**，和**LoginName**. 此事件沒有任何子事件。  
  
> [!NOTE]  
>  執行類似 DDL 作業的系統預存程序也可以引發事件通知。 請測試事件通知以判斷它們對執行之系統預存程序的回應。 例如，CREATE TYPE 陳述式及**sp_addtype**預存程序都會引發在 CREATE_TYPE 事件建立的事件通知。 如需詳細資訊，請參閱 <<c0> [ DDL 事件](../../relational-databases/triggers/ddl-events.md)。  
  
 **資料定義語言事件和事件群組**  
  
 ![WMI Provider for Server Events 事件樹](../../relational-databases/wmi-provider-server-events/media/sql-wmi-ddl-events-ktm.gif "WMI Provider for Server Events 事件樹")  
  
 **追蹤事件和事件群組**  
  
 ![追蹤事件和事件群組](../../relational-databases/wmi-provider-server-events/media/sql-wmi-trc-all-events.gif "追蹤事件和事件群組")  
  
## <a name="see-also"></a>另請參閱  
 [WMI 事件提供者伺服器概念](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md)   
 [搭配伺服器事件的 WMI 提供者使用 WQL](../../relational-databases/wmi-provider-server-events/using-wql-with-the-wmi-provider-for-server-events.md)  
  
  
