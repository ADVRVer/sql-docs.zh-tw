---
title: Azure Blob 下載工作 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpblobdltask.f1
- sql11.dts.designer.afpblobdltask.f1
ms.assetid: 8a63bf44-71be-456d-9a5c-be7c31aff065
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0c4b50078f1d0192dd039ce17b3d4dd6c8d4524e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48092438"
---
# <a name="azure-blob-download-task"></a>Azure Blob 下載工作
  Azure Blob 下載工作可讓 SSIS 封裝能從 Azure Blob 儲存體下載檔案。   
若要加入 **Azure Blob 下載工作**，請將其拖放至 SSIS 設計工具，然後按兩下或在其上按一下滑鼠右鍵，再按一下 [編輯]  ，即可看到以下 [Azure Blob 下載工作編輯器]  對話方塊。  
  
 下表提供此對話方塊中欄位的描述。  
  
|||  
|-|-|  
|**欄位**|**說明**|  
|AzureStorageConnection|指定現有的 Azure 儲存體連線管理員，或建立參考 Azure 儲存體帳戶的新連線管理員，而該儲存體帳戶指向裝載 Blob 檔案之處。|  
|BlobContainer|指定包含要下載的 Blob 檔案之 Blob 容器的名稱。|  
|BlobDirectory|指定包含要下載之 Blob 檔案的 Blob 目錄。 Blob 目錄是虛擬的階層式結構。|  
|LocalDirectory|指定將儲存已下載之 Blob 檔案的本機目錄。|  
|FileName|指定名稱篩選，利用指定的名稱模式來選取檔案。 例如 MySheet*.xls\* 包含 MySheet001.xls 及 MySheetABC.xlsx 等檔案。|  
|TimeRangeFrom/TimeRangeTo|指定時間範圍篩選。 將會包含在 **TimeRangeFrom** 之後且 **TimeRangeTo** 之前所修改的檔案。|  
  
  
