---
title: Server Properties in Analysis Services |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ce74bb210e3d5d3cd01120b0bd406672db6dd5ed
ms.sourcegitcommit: f46fd79fd32a894c8174a5cb246d9d34db75e5df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/26/2018
ms.locfileid: "53785819"
---
# <a name="server-properties-in-analysis-services"></a>Analysis Services 中的伺服器屬性
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 管理員可以修改 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體的預設伺服器組態屬性。 每一個執行個體都有自己的組態屬性，與同一部伺服器上的其他執行個體分開設定。  
  
 若要設定伺服器，使用 SQL Server Management Studio，或是編輯特定的 SQL Server Analysis Services 執行個體的 msmdsrv.ini 檔。  
 
SQL Server Management Studio 的 [屬性] 頁會顯示最有可能修改的屬性子集。 完整的屬性清單位在 msmdsrv.ini 檔中。   
  
> [!NOTE]  
>  在預設 SQL Server Analysis Services 安裝中，msmdsrv.ini 篇 \Program Files\Microsoft SQL Server\MSAS13。MSSQLSERVER\OLAP\Config 資料夾中。
> 
> 其他會影響伺服器組態的屬性包括 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中的部署組態屬性。 如需這些屬性的詳細資訊，請參閱 [指定方案部署的組態設定](../../analysis-services/multidimensional-models/deployment-script-files-solution-deployment-config-settings.md)。
 
## <a name="configure-properties-in-management-studio"></a>在 Management Studio 中設定屬性 
  
1.  在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，連接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體。  
  
2. 在物件總管中，以滑鼠右鍵按一下 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體，然後按一下 [屬性]。 [一般] 頁面隨即顯示，其中顯示最常使用的屬性。  

3.  若要檢視其他屬性，請按一下頁面底部的 [顯示進階 (全部) 屬性] 核取方塊。  
  
     只有表格式模式和多維度模式伺服器支援修改伺服器屬性。 如果您已安裝 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]，除非 Microsoft 支援服務另有指示，否則請一律使用預設值。  
  
  
## <a name="configure-properties-in-msmdsrvini"></a>設定 msmdsrv.ini 中的屬性
  
部分屬性只能在 msmdrsrv.ini 檔中設定。 這些屬性並不適用於 Azure Analysis Services。
如果即使在顯示進階屬性之後仍看不到您要設定的屬性，可能需要直接編輯 msmdsrv.ini 檔。 
  
1.  請檢查 Management Studio 中 [一般] 屬性頁的 **DataDir** 屬性，以確認 Analysis Services 程式檔的位置，包括 msmdsrv.ini 檔。

     在有多個執行個體的伺服器上，檢查程式檔案位置可確保您修改的是正確的檔案。  
  
2.  巡覽至程式檔案資料夾位置的 **config** 資料夾。

3. 建立檔案的備份，以免需要還原原始檔案。  
  
4.  使用文字編輯器檢視或編輯 msmdsrv.ini 檔。  
  
5.  儲存檔案後再重新啟動服務。  
  
##  <a name="server-property-reference"></a>伺服器屬性參考  
  
 下列主題說明各種 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 組態屬性：  
  
|主題|描述|  
|-----------|-----------------|  
|[一般屬性](../../analysis-services/server-properties/general-properties.md)|一般屬性是基本和進階屬性，並且包含定義資料目錄、備份目錄和其他伺服器行為的屬性。|  
|[資料採礦屬性](../../analysis-services/server-properties/data-mining-properties.md)|資料採礦屬性控制要啟用和停用哪些資料採礦演算法。 依預設，會啟用所有的演算法。| 
|[DAX 屬性](../../analysis-services/server-properties/dax-properties.md)|定義與 DAX 查詢相關的屬性。|
|DSO|不再支援 DSO。 DSO 屬性會遭到忽略。|  
|[功能屬性](../../analysis-services/server-properties/feature-properties.md)|與產品功能有關的功能屬性，大部分是進階屬性，包含控制伺服器執行個體間之連結的屬性。|  
|[Filestore 屬性](../../analysis-services/server-properties/filestore-properties.md)|檔案存放區屬性僅供進階使用。 其中包含進階記憶體管理設定。|  
|[鎖定管理員屬性](../../analysis-services/server-properties/lock-manager-properties.md)|鎖定管理員屬性定義與鎖定和逾時有關的伺服器行為。 這些屬性大部分僅供進階使用。|  
|[記錄屬性](../../analysis-services/server-properties/log-properties.md)|記錄屬性控制在伺服器上是否記錄事件、記錄於何處以及如何記錄。 這包含錯誤記錄、例外狀況記錄、飛行記錄器、查詢記錄和追蹤。|  
|[記憶體屬性](../../analysis-services/server-properties/memory-properties.md)|記憶體屬性控制伺服器如何使用記憶體。 這些屬性主要是供進階使用。|  
|[網路屬性](../../analysis-services/server-properties/network-properties.md)|網路屬性控制與網路有關的伺服器行為，包含控制壓縮和二進位 XML 的屬性。 這些屬性大部分僅供進階使用。|  
|[OLAP 屬性](../../analysis-services/server-properties/olap-properties.md)|OLAP 屬性控制 Cube 和維度處理、延遲處理、資料快取，以及查詢行為。 這些包含基本和進階屬性。|  
|[安全性屬性](../../analysis-services/server-properties/security-properties.md)|安全性區段包含定義存取權限的基本和進階屬性。 這包含與管理員和使用者有關的設定。|  
|[執行緒集區屬性](../../analysis-services/server-properties/thread-pool-properties.md)|執行緒集區屬性控制伺服器會建立多少執行緒。 這些屬性主要是進階屬性。|  
  
## <a name="see-also"></a>另請參閱  
 [Analysis Services 執行個體管理](../../analysis-services/instances/analysis-services-instance-management.md)   
 [指定方案部署的組態設定](../../analysis-services/multidimensional-models/deployment-script-files-solution-deployment-config-settings.md)  
  
  
