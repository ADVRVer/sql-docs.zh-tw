---
title: "防毒軟體 (Analytics Platform System)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 60ab9a88-d339-4917-a38b-f9481aef38fd
caps.latest.revision: "29"
ms.openlocfilehash: f1d5c81381b486ec89198fed6aa22ccff22a544a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="antivirus-software"></a>防毒軟體
如果您的資料中心需要防毒軟體，請使用下列指導方針來分析平台系統上安裝的防毒軟體。 我們建議不要安裝防毒軟體，除非確實需要資料中心。  
  
> [!WARNING]  
> 我們強烈建議您個別評估每個電腦與整體，Analytics Platform System 安全性風險，而且您選取適合每一部電腦的安全性風險層級的工具。 此外，我們建議您轉出任何病毒防護專案之前，您會測試整個系統的完整負載來測量在穩定性和效能的任何變更。  
>   
> 病毒防護軟體需要執行某些系統資源。 您必須執行測試之前和之後安裝您的防毒軟體，以判斷是否有任何影響之 Analytics Platform System 的效能。  
  
本主題中的指導方針以基礎[如何選擇在執行 SQL Server 的電腦上執行的防毒軟體](http://support.microsoft.com/kb/309422)和[KB 文章 961804](http://support.microsoft.com/kb/961804/en-us)。  
  
## <a name="exclusion-list-for-physical-hosts"></a>實體主機的排除清單  
若要在實體主機上安裝的防毒軟體，排除下列目錄和處理程序的清單。 這些不應該掃描的防毒軟體。  
  
**排除這些目錄：**  
  
-   C:\ProgramData\Microsoft\Windows\Hyper-V-虛擬機器設定目錄  
  
-   C:\Users\Public\Documents\Hyper-V\Virtual 硬碟的虛擬硬碟的預設目錄  
  
-   C:\clusterStorage-虛擬硬碟機目錄  
  
**排除這些處理程序：**  
  
-   虛擬機器管理 (Vmms.exe)  
  
-   虛擬機器工作流程 (Vmwp.exe)  
  
## <a name="exclusion-list-for-virtual-machines-vms"></a>虛擬機器 (Vm) 的排除清單  
若要在 Vm 上安裝的防毒軟體，排除下列目錄和檔案的清單。 這些不應該掃描的防毒軟體。  
  
***PDW_region*-CTL01**  
  
-   C:\windows\cluster\  
  
-   G:\  
  
***appliance_domain*-AD01**和 ***appliance_domain*-ad02 移**  
  
-   無限制  
  
**計算節點 Vm**  
  
-   C:\windows\cluster\  
  
-   G:\  
  
***appliance_domain*VMM**  
  
-   無限制  
  
***appliance_domain*-WDS**  
  
-   無限制  
  
***appliance_domain*-ISCSI01**  
  
-   C:\iscsitarget  
  
## <a name="see-also"></a>請參閱＜  
[應用裝置管理工作 &#40;Analytics Platform System &#41;](appliance-management-tasks.md)  
  
