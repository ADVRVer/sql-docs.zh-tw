---
title: 來源小幫手 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.sourceassistant.f1
- sql13.dts.designer.addNewSource.f1
ms.assetid: 5ca9d821-7d61-4727-9133-5f9cb485c7f3
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 93bbfcc8b76fe6fe1028b5b13395e0a88a6b359a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "65726356"
---
# <a name="source-assistant"></a>Source Assistant

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  來源小幫手元件有助於建立來源元件和連線管理員。 該元件位於 SSIS 工具箱的 **[我的最愛]** 區段中。  
  
> [!NOTE]  
>  來源小幫手取代了 Integration Services 連接專案和對應的精靈。  
  
## <a name="add-a-source-with-source-assistant"></a>使用來源小幫手加入來源
本節提供使用來源小幫手加入新來源的步驟，也會列出可以在 [加入新來源]  對話方塊上使用的選項。當您將來源小幫手拖放至 SSIS 設計師，即會顯示此對話方塊。  

1.  在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中，開啟要加入來源元件的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝。  
  
2.  將 [來源小幫手]  元件從 SSIS 工具箱拖曳至 [資料流程]  索引標籤。[加入新來源]  對話方塊應會隨即出現。 下一節提供可以在對話方塊中使用之選項的詳細資訊。  
  
3.  在 [類型]  清單中選取目的地的類型。  
  
4.  在 [連線管理員]  清單中選取現有的連線管理員，或選取 [\<新增>]  ，以建立新的連線管理員。  
  
5.  如果您選取現有的連線管理員，請按一下 [確定]  ，以關閉 [加入新目的地]  對話方塊。 您應該會看到目的地和連線管理員已加入資料流程。  
  
6.  如果按一下 [\<新增>]  來建立新的連線管理員，應會顯示 [連線管理員]  對話方塊，讓您指定連線參數。 完成建立新的連接管理員之後，您會在 SSIS 設計師中看到目的地和連接管理員。  

## <a name="add-new-source-dialog-box"></a>加入新來源對話方塊
下表列出可以在 [加入新來源]  對話方塊中使用的選項。  
  
|選項|Description|  
|------------|-----------------|  
|類型|選取您要連接的來源類型。|  
|連接管理員|選取現有的連線管理員，或按一下 [\<新增>]  以建立新的連線管理員。|  
|僅顯示已安裝|指定是否只要檢視已安裝的來源。|  
|[確定]|按一下以儲存您的變更，並開啟任何後續的對話方塊設定其他選項。| 
  
