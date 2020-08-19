---
description: RDS 物件
title: RDS 物件 |Microsoft Docs
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
helpviewer_keywords:
- objects [ADO], RDS
- RDS objects [ADO]
ms.assetid: f2ac8b3b-f968-41c4-a504-7aee3538b7c7
author: rothja
ms.author: jroth
ms.openlocfilehash: 477db26b27b0b6222da55585661db1dc37d64b82
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88438780"
---
# <a name="rds-objects"></a>RDS 物件
> [!IMPORTANT]
>  從 Windows 8 和 Windows Server 2012 開始，Windows 作業系統中不再包含 RDS 伺服器元件 (如需詳細) 資訊，請參閱 Windows 8 和 [Windows server 2012 相容性操作手冊](https://www.microsoft.com/download/details.aspx?id=27416) 。 未來的 Windows 版本將移除 RDS 用戶端元件。 請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。 使用 RDS 的應用程式應該遷移至 [WCF 資料服務](https://go.microsoft.com/fwlink/?LinkId=199565)。  
  
|Object|描述|  
|-|-|  
|[DataControl (RDS) ](../../../ado/reference/rds-api/datacontrol-object-rds.md)|將資料查詢 **記錄集** 系結至一或多個控制項 (例如，文字方塊、方格控制項或下拉式方塊) ，以在網頁上顯示 **記錄集** 資料。<br /><br /> **DataControl**物件對腳本是安全的。|  
|[DataFactory (RDSServer) ](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)|會針對用戶端應用程式的指定資料來源，執行提供讀取/寫入資料存取的方法。<br /><br /> **DataFactory**物件對腳本而言並不安全。|  
|[ (RDS) 的空間 ](../../../ado/reference/rds-api/dataspace-object-rds.md)|建立位於仲介層的自訂商務物件之用戶端 proxy。<br /><br /> 您可以安全地執行腳本處理的 **空間** 物件。|  
|[IRDSService 介面 (RDS)](../../../ado/reference/rds-api/irdsservice-interface-rds.md)|公開 [InvokeService (RDS) ](../../../ado/reference/rds-api/invokeservice-rds.md) 方法，這個方法可用來在更強大的物件版本上，將指標傳回所要求的介面。|  
  
## <a name="see-also"></a>另請參閱  
 [RDS API 參考](../../../ado/reference/rds-api/rds-api-reference.md)


