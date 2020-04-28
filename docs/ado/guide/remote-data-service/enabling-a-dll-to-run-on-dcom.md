---
title: 啟用 DLL 以在 DCOM 上執行 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- DLL on DCOM in RDS [ADO]
- DCOM in RDS [ADO]
- business objects in RDS [ADO]
ms.assetid: 5f1c2205-191c-4fb4-9bd9-84c878ea46ed
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9ea7ea83219780602f8d8d68e5c807178e775bc2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "67922706"
---
# <a name="enabling-a-dll-to-run-on-dcom"></a>啟用 DLL 以在 DCOM 上執行
> [!IMPORTANT]
>  從 Windows 8 和 Windows Server 2012 開始，Windows 作業系統不再包含 RDS 伺服器元件（如需詳細資訊，請參閱 Windows 8 和[Windows Server 2012 相容性操作手冊](https://www.microsoft.com/download/details.aspx?id=27416)）。 RDS 用戶端元件將會在未來的 Windows 版本中移除。 請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。 使用 RDS 的應用程式應該遷移至[WCF 資料服務](https://go.microsoft.com/fwlink/?LinkId=199565)。  
  
 下列步驟概述如何啟用商務物件 .dll，以透過元件服務使用 DCOM 和 Microsoft Internet Information Services （HTTP）。  
  
1.  在 [元件服務] MMC 嵌入式管理單元中建立新的空白封裝。  
  
     您將使用 [元件服務] MMC 嵌入式管理單元來建立封裝，並將該 DLL 新增到此封裝中。 這可讓 .dll 透過 DCOM 來存取，但它會移除透過 IIS 的存取範圍。 （如果您在登錄中存有 .dll，則**inproc**索引鍵現在是空的; 設定啟用屬性（在本主題稍後說明）會在**Inproc**索引鍵中新增一個值）。  
  
2.  將商務物件安裝到封裝中。  
  
     -或-  
  
     將[RDSServer. DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)物件匯入封裝中。  
  
3.  **在建立者的進程**（程式庫應用程式）中，將套件的啟用屬性設定為。  
  
     若要透過相同電腦上的 DCOM 和 IIS 來存取 .dll，您必須在 [元件服務] MMC 嵌入式管理單元中設定元件的 [啟用] 屬性。 在建立**者的程式中**將屬性設定為之後，您會注意到登錄中的**Inproc**伺服器機碼已加入指向元件服務的代理 .dll。  
  
 如需有關元件服務（或 Microsoft 交易服務，如果您使用的是 Windows NT）以及如何執行這些步驟的詳細資訊，請造訪 Microsoft Transaction Server 網站。


