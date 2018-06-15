---
title: Filestore 屬性 |Microsoft 文件
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3a5bf8e90352218b222bbd6a58ad876ca0e1364b
ms.sourcegitcommit: 6e55a0a7b7eb6d455006916bc63f93ed2218eae1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2018
ms.locfileid: "35239038"
---
# <a name="filestore-properties"></a>FileStore 屬性
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 支援`filestore`下表中列出的伺服器屬性。 這些全部都是進階屬性，除非是在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援人員的指導之下，否則不應隨意變更。 如需其他伺服器屬性以及如何設定伺服器屬性的詳細資訊，請參閱 [Analysis Services 中的伺服器屬性](../../analysis-services/server-properties/server-properties-in-analysis-services.md)。  
  
 **適用於：** 多維度與表格式伺服器模式  
  
## <a name="properties"></a>屬性  
 **MemoryLimit**  
 此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。  
  
 **MemoryLimitMin**  
 此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。  
  
 **PercentScanPerPrice**  
 此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。  
  
 **PerformanceTrace**  
 此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。  
  
 **RandomFileAccessMode**  
 此為布林屬性，指出是否在隨機檔案存取模式下存取資料庫檔案和快取檔案。 此屬性預設為關閉。 根據預設，伺服器時不會設定隨機檔案存取旗標開啟分割資料檔讀取權限。  
  
 在高階系統上，尤其是具有大型記憶體資源和多個 NUMA 節點的系統，使用隨機檔案存取會很有幫助。 在隨機存取模式中，Windows 會略過頁面對應作業從磁碟讀入系統檔案快取中，藉此降低快取的競爭情況。  
  
 您將需要執行比較測試，判斷變更此屬性是否使查詢效能獲得改善。 如需執行比較測試的最佳作法，包括清除快取和避免常見的錯誤，請參閱 [SQL Server 2008 R2 Analysis Services 作業指南](http://go.microsoft.com/fwlink/?LinkID=225539)。 使用此屬性之權衡取捨其他資訊，請參閱[ http://support.microsoft.com/kb/2549369 ](http://support.microsoft.com/kb/2549369)。  
  
 若要在 Management Studio 中檢視或修改這個屬性，請在伺服器屬性頁面中啟用進階屬性清單。 您也可以變更 msmdsrv.ini 檔案中的屬性。 設定這個屬性之後，建議重新啟動伺服器，否則會繼續在之前的模式下存取已開啟的檔案。  
  
 **UnbufferedThreshold**  
 此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。  
  
## <a name="memory-model-category"></a>記憶體模型類別目錄  
 **MemoryModel\Tax**  
 此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。  
  
 **MemoryModel\Income**  
 此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。  
  
 **MemoryModel\MaximumBalance**  
 此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。  
  
 **MemoryModel\MinimumBalance**  
 此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。  
  
 **MemoryModel\InitialBonus**  
 此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。  
  
## <a name="see-also"></a>另請參閱  
 [Analysis Services 中的伺服器屬性](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [判斷 Analysis Services 執行個體的伺服器模式](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
