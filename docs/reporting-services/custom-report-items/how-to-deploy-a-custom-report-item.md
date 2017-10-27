---
title: "如何： 部署自訂報表項目 |Microsoft 文件"
ms.custom: 
ms.date: 03/18/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- custom report items, deploying
ms.assetid: 80e97b0d-e355-4240-aebd-08cbc84089ed
caps.latest.revision: 26
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 742e80b96e6887188620b4f2a7ab3808475ceda2
ms.contentlocale: zh-tw
ms.lasthandoff: 08/12/2017

---
# <a name="how-to-deploy-a-custom-report-item"></a>如何：部署自訂報表項目
  若要在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中部署自訂報表項目，您必須修改報表伺服器組態檔，並將設計階段和執行階段元件組件複製到適當的報表設計師和報表伺服器應用程式資料夾中。  
  
### <a name="to-deploy-a-custom-report-item"></a>部署自訂報表項目  
  
1.  編輯 Rsreportdesigner.config 檔案，將自訂報表項目執行階段和設計階段元件設定為用於設計工具： 請注意， **ReportItemName**項目必須符合**CustomReportItemAttribute**屬性中使用您**CustomReportItemDesigner**類別。 例如：  
  
    ```  
    <ReportItems>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsCRI,PolygonsCRI"/>  
    </ReportItems>  
    <ReportItemDesigner>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsDesigner, PolygonsDesigner" />  
    </ReportItemDesigner>  
    <ReportItemConverter>  
       <Converter Source="Chart" Target="Polygons" Type="PolygonsCRI.PolygonsConverter, PolygonsDesigner" />  
    </ReportItemConverter>  
    ```  
  
2.  編輯 Rsreportserver.config 檔案來註冊自訂表單項目執行階段元件。 例如：  
  
    ```  
    <ReportItems>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsCRI,PolygonsCRI"/>  
    </ReportItems>  
    ```  
  
3.  編輯 Rsssrvpolicy.config 檔案以新增**CodeGroup** ，授與適當的權限的自訂報表項目。 例如：  
  
    ```  
    <CodeGroup   
       class="UnionCodeGroup"   
       version="1"   
       PermissionSetName="FullTrust"  
       Description="This code group grants MyCustomReportItem.dll FullTrust permission. ">  
       <IMembershipCondition   
          class="UrlMembershipCondition"  
          version="1"  
       Url="C:\Program Files\Microsoft SQL Server\ MSRS10_50.SQLSERVER\Reporting Services\ReportServer\bin\MyCustomReportItem.dll" />  
    </CodeGroup>  
    ```  
  
4.  將自訂報表項目執行階段元件 DLL 複製到 %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies and \Program Files\Microsoft SQL Server\MSRS10_50.SQLSERVER\Reporting Services\ReportServer\bin 目錄。  
  
5.  將自訂報表項目設計階段元件 DLL 複製到 %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies 目錄。  
  
## <a name="see-also"></a>另請參閱  
 [Reporting Services 組態檔](../../reporting-services/report-server/reporting-services-configuration-files.md)   
 [自訂報表項目類別庫](../../reporting-services/custom-report-items/custom-report-item-class-libraries.md)  
  
  

