---
title: 多個檔案連線管理員 | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: connection-manager
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- folders [Integration Services], connections
- files [Integration Services], connections
- Multiple Files connection manager
- connection managers [Integration Services], Multiple Files
- connections [Integration Services], files
- multiple file connections
ms.assetid: 10bdc56e-c5cd-4ddb-b2f7-375fe57fe8b2
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1b558fa9dc8e8a65cc112376c636ec7e5ad6dc06
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="multiple-files-connection-manager"></a>多個檔案連接管理員
  「多個檔案」連接管理員會啟用封裝以參考現有的檔案和資料夾，或是在執行階段建立檔案和資料夾。  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中的內建工作和資料流程元件不會使用「多個檔案」連接管理員。 但是，您可以在指令碼工作或指令碼元件中使用這個連接管理員。 如需有關如何在指令碼工作中使用連接管理員的資訊，請參閱＜ [連接至指令碼工作中的資料來源](../../integration-services/extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md)＞。 如需有關如何在指令碼元件中使用連接管理員的詳細資訊，請參閱＜ [連接到指令碼元件中的資料來源](../../integration-services/extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md)＞。  
  
## <a name="usage-types-of-the-multiple-files-connection-manager"></a>多個檔案連接管理員的使用類型  
 「多個檔案」連接管理員的 **FileUsageType** 屬性會指定如何使用連接。 「多個檔案」連接管理員可以建立檔案、建立資料夾、使用現有的檔案，以及使用現有的資料夾。  
  
 下表列出 **FileUsageType**的值。  
  
|ReplTest1|描述|  
|-----------|-----------------|  
|**0**|「多個檔案」連接管理員會使用現有的檔案。|  
|**1**|「多個檔案」連接管理員會建立檔案。|  
|**2**|「多個檔案」連接管理員會使用現有的資料夾。|  
|**3**|「多個檔案」連接管理員會建立資料夾。|  
  
## <a name="configuration-of-the-multiple-files-connection-manager"></a>設定多個檔案連接管理員  
 當您將「多個檔案」連線管理員加入封裝時， [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 會建立連線管理員，用來在執行階段解析為「多個檔案」連接、設定「多個檔案」連接屬性，以及將「多個檔案」連接加入封裝的 **Connections** 集合。  
  
 連接管理員的 **ConnectionManagerType** 屬性會設為 **MULTIFILE**。  
  
 您可以利用下列方式設定「多個檔案」連接管理員：  
  
-   指定檔案和資料夾的使用類型。  
  
-   指定檔案和資料夾。  
  
-   如果使用多個檔案和資料夾，請指定存取這些檔案和資料夾的順序。  
  
 如果「多個檔案」連接管理員參考多個檔案和資料夾，則檔案和資料夾的路徑會以垂直線 (|) 字元隔開。 連接管理員的 **ConnectionString** 屬性具有下列格式：  
  
 \<*path*>|\<*path*>  
  
 您也可以使用萬用字元來指定多個檔案或資料夾。 例如，若要參考 C 磁碟機上的所有文字檔， **ConnectionString** 屬性的值可以設定為 C:\\*.txt。  
  
 您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。  
  
 如需可在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計工具中設定之屬性的詳細資訊，請參閱 [Add File Connection Manager Dialog Box UI Reference](../../integration-services/connection-manager/add-file-connection-manager-dialog-box-ui-reference.md)(加入 [檔案連線管理員] 對話方塊 UI 參考)。  
  
 如需以程式設計方式設定連線管理員的詳細資訊，請參閱 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 和 [以程式設計方式加入連接](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md)＞。  
  
  
