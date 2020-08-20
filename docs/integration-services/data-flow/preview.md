---
description: 預覽
title: 預覽 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 551494c4-9e27-4592-9200-c6bf19e80c9a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d6d3404eecd7c1a054f82442263802784c35c4d2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88457288"
---
# <a name="preview"></a>預覽 

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  使用 **[預覽]** 對話方塊可以預覽 SAP BW 來源即將擷取的資料。  
  
> [!IMPORTANT]  
>  **[SAP BW 來源編輯器]** 之 **[連接管理員]** 頁面上提供的 **[預覽]** 選項會實際擷取資料。 如果您已將 SAP Netweaver BW 設定為僅擷取自從上次擷取以來已變更的資料，則選取 **[預覽]** 將會從下次擷取中排除已預覽的資料。  
  
 若要深入了解 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的 SAP BW 來源元件，請參閱 [SAP BW 來源](../../integration-services/data-flow/sap-bw-source.md)。  
  
> [!IMPORTANT]  
>  Microsoft Connector 1.1 for SAP BW 的文件集是假設使用者已熟悉 SAP Netweaver BW 環境。 如需有關 SAP Netweaver BW 的詳細資訊，或有關如何設定 SAP Netweaver BW 物件與處理序的詳細資訊，請參閱 SAP 文件集。  
  
> [!IMPORTANT]  
>  擷取 SAP Netweaver BW 中的資料需要額外的 SAP 授權。 請洽詢 SAP 以確認這些需求。  
  
 **若要開啟預覽對話方塊**  
  
1.  在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含 SAP BW 來源的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝。  
  
2.  在 [資料流程] 索引標籤上，按兩下 SAP BW 來源。  
  
3.  在 **[SAP BW 來源編輯器]** 中，按一下 **[連接管理員]** 開啟編輯器的 **[連接管理員]** 頁面。  
  
4.  設定 SAP BW 來源。  
  
5.  在您設定 SAP BW 來源之後，請在 **[連接管理員]** 頁面上，按一下 **[預覽]** ，即可在 **[預覽]** 對話方塊中預覽資料。  
  
    > [!NOTE]  
    >  按一下 **[預覽]** 也會開啟 **[要求記錄檔]** 對話方塊。 如需有關此對話方塊的詳細資訊，請參閱＜ [Request Log](../../integration-services/data-flow/request-log.md)＞。  
  
## <a name="options"></a>選項。  
 **[預覽]** 對話方塊會顯示向 SAP Netweaver BW 系統要求的資料列。 顯示的資料行就是來源資料中定義的資料行。  
  
 這個對話方塊沒有其他選項。  
  
## <a name="see-also"></a>另請參閱  
 [SAP BW 來源編輯器 &#40;連線管理員頁面&#41;](../../integration-services/data-flow/sap-bw-source-editor-connection-manager-page.md)   
 [Microsoft Connector for SAP BW F1 說明](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  
