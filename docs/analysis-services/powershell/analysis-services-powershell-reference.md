---
title: "Analysis Services PowerShell 參考 |Microsoft 文件"
ms.custom: 
ms.date: 06/21/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: powershell
ms.reviewer: 
ms.suite: sql
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6c435e40-bfaf-4073-8cef-bc3260602246
caps.latest.revision: "9"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 8f23632c4b4dde2943d74a40e7ea0c75de963a4b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="analysis-services-powershell-reference"></a>Analysis Services PowerShell 參考

[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]


  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]PowerShell 指令程式會包含在[SqlServer 模組](https://www.powershellgallery.com/packages/SqlServer/21.0.17099)。 
  
>[!NOTE] 
> Azure Analysis Services 資料庫的作業為 SQL Server Analysis Services 使用相同的 SqlServer 模組。 不過，並非所有的指令程式支援 Azure Analysis Services。 若要進一步了解，請參閱[使用 PowerShell 管理 Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-powershell)。
  
##  <a name="bkmk_cmdlets"></a> Analysis Services 指令程式  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 提供對應到 **Microsoft.AnalysisServices** 命名空間之方法的 Cmdlet。 下表描述每個指令程式，並提供對應 AMO 方法的連結。  
  
 如果您要使用 PowerShell 執行未在下列清單中表示的工作 (例如建立或同步處理資料庫)，可以為該動作撰寫 TMSL 或 XMLA 指令碼，然後使用 **Invoke-ASCmd** Cmdlet 執行它。  
  
|指令程式|說明|對等 AMO 方法|  
|------------|-----------------|----------------------------|  
|[Add-RoleMember 指令程式](../../analysis-services/powershell/add-rolemember-cmdlet.md)|將成員加入至資料庫角色。|<xref:Microsoft.AnalysisServices.RoleMemberCollection.Add%2A>|  
|[Backup-ASDatabase 指令程式](../../analysis-services/powershell/backup-asdatabase-cmdlet.md)|備份 Analysis Services 資料庫。|[Database.Backup](https://msdn.microsoft.com/library/microsoft.analysisservices.database.backup.aspx)|  
|[Invoke-ASCmd cmdlet](../../analysis-services/powershell/invoke-ascmd-cmdlet.md)|執行 XMLA 或 TSML (JSON) 格式的查詢或指令碼。|<xref:Microsoft.AnalysisServices.Core.Server.Execute%2A>|  
|[Invoke-ProcessASDatabase](../../analysis-services/powershell/invoke-processasdatabase.md)|處理資料庫。|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Invoke-ProcessCube 指令程式](../../analysis-services/powershell/invoke-processcube-cmdlet.md)|處理 Cube。|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Invoke-ProcessDimension 指令程式](../../analysis-services/powershell/invoke-processdimension-cmdlet.md)|處理維度。|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Invoke-ProcessPartition 指令程式](../../analysis-services/powershell/invoke-processpartition-cmdlet.md)|處理資料分割。|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Invoke-ProcessTable cmdlet](../../analysis-services/powershell/invoke-processtable-cmdlet.md)|處理表格式模型中，相容性模型 1200年或更高版本中的資料表。|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Merge-Partition cmdlet](../../analysis-services/powershell/merge-partition-cmdlet.md)|合併資料分割。|<xref:Microsoft.AnalysisServices.Partition.Merge%2A>|  
|[New-RestoreFolder 指令程式](../../analysis-services/powershell/new-restorefolder-cmdlet.md)|建立要包含資料庫備份的資料夾。|<xref:Microsoft.AnalysisServices.RestoreFolder>|  
|[New-RestoreLocation 指令程式](../../analysis-services/powershell/new-restorelocation-cmdlet.md)|指定一個或多個要還原資料庫的遠端伺服器。|<xref:Microsoft.AnalysisServices.RestoreLocation>|  
|[Remove-RoleMember 指令程式](../../analysis-services/powershell/remove-rolemember-cmdlet.md)|從資料庫角色中移除成員。|<xref:Microsoft.AnalysisServices.RoleMemberCollection.Remove%2A>|  
|[Restore-ASDatabase 指令程式](../../analysis-services/powershell/restore-asdatabase-cmdlet.md)|在伺服器執行個體上還原資料庫。|<xref:Microsoft.AnalysisServices.Core.Server.Restore%2A>|  
  

  
  
