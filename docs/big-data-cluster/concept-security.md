---
title: 安全性概念
titleSuffix: SQL Server big data clusters
description: 本文描述 SQL Server 巨量資料叢集的安全性概念。 其中包括叢集端點和叢集驗證的說明。
author: nelgson
ms.author: negust
ms.reviewer: mikeray
ms.date: 10/23/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 35eb5e0a3236d8f016ed5ca99b769d628a4d81ed
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/04/2019
ms.locfileid: "73532368"
---
# <a name="security-concepts-for-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd"></a>[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] 的安全性概念

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

本文將涵蓋巨量資料叢集中與安全性相關的重要概念

[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] 能提供一致的授權和驗證。 巨量資料叢集可以與 Active Directory 整合，方法是透過自動化部署針對現有網域設定 Active Directory 整合。 在搭配 Active Directory 整合設定巨量資料叢集之後，您可以利用現有的身分識別和使用者群組在所有端點上進行統一存取。 此外，在您於 SQL Server 中建立外部資料表之後，您可以透過將外部資料表的存取權授與 Active Directory 使用者和群組，進而將資料存取原則集中到單一位置，來控制對資料來源的存取。

## <a name="authentication"></a>驗證

外部叢集端點支援 Active Directory 驗證。 這代表您可以使用您的 AD 身分識別來向巨量資料叢集進行驗證。

### <a name="cluster-endpoints"></a>叢集端點

巨量資料叢集有五個進入點

* 主要執行個體 - 用來透過資料庫工具和如 SSMS 或 Azure Data Studio 之類的應用程式存取叢集中 SQL Server 主要執行個體的 TDS 端點。 使用來自 Azdata 的 HDFS 或 SQL Server 命令時，視作業而定，該工具將會連線到其他端點。

* 用來存取 HDFS 檔案的閘道，Spark (Knox) - 這是 HTTPS 式的端點。 此端點是用來存取 webHDFS 和 Spark 等服務。

* 叢集管理服務 (控制器) 端點 - 公開 REST API 來管理叢集的巨量資料叢集管理服務。 Azdata 工具需要連線到此端點。

* 管理 Proxy - 用來存取「記錄搜尋」儀表板和「計量」儀表板。

* 應用程式 Proxy - 管理部署於巨量資料叢集內部之應用程式的端點。

![叢集端點](media/concept-security/cluster_endpoints.png)

目前沒有開啟其他連接埠從外部存取叢集的選項。

## <a name="authorization"></a>授權

在整個叢集中，從 Spark 和 SQL Server 一路將查詢發送到 HDFS 時，不同元件之間的整合式安全性將能使原始使用者的身分識別能夠傳遞。 如上所述，有各式各樣的外部叢集端點支援 AD 驗證。

在管理資料存取的叢集中有兩個層級的授權檢查。 巨量資料內容中的授權是在 SQL Server 中完成，方法是在物件上和具有控制清單 (ACL) 的 HDFS 中使用傳統 SQL Server 權限，這會將使用者身分識別與特定權限相關聯。

安全的巨量資料叢集是指在 SQL Server 與 HDFS/Spark 之間，針對驗證和授權案例提供一致且連貫的支援。 驗證是驗證使用者或服務識別的程序，並確保其為所宣稱的身分。 授權是指根據要求使用者的識別，授與或拒絕對特定資源的存取。 此步驟是在透過驗證識別使用者之後執行。

巨量資料內容中的授權通常是透過存取控制清單 (ACL) 執行，這會建立使用者識別與特定權限的關聯。 HDFS 藉由限制對服務 API、HDFS 檔案和作業執行的存取來支援授權。

## <a name="encryption-and-other-security-mechanisms"></a>加密及其他安全性機制

針對用戶端和外部端點之間，以及叢集內元件之間通訊的加密，是搭配 TLS/SSL 使用憑證來保護。

SQL Server 與 SQL Server 之間的所有通訊 (例如與資料集區通訊的 SQL 主要執行個體) 都是使用 SQL 登入來保護。

## <a name="basic-administrator-login"></a>基本系統管理員登入

您可以選擇在 Active Directory 模式中，或是僅使用基本系統管理員登入來部署叢集。 不過，使用基本系統管理員登入並非生產環境所支援的安全性模式，且主要是用來評估產品。

即使您選擇 Active Directory 模式，系統仍然會為叢集系統管理員建立基本登入。 這能在 AD 連線中斷時提供「後門」。

在部署之後，系統便會將叢集中的系統管理員權限授與此基本登入。 這代表該使用者將會成為 SQL Server 主要執行個體中的系統管理員，以及叢集控制器中的系統管理員。
Hadoop 元件不支援混合模式驗證，這代表基本系統管理員登入並無法用來對閘道 (Knox) 進行驗證。


這些是您需要在部署時定義的登入認證。

叢集管理使用者名稱：
 + `AZDATA_USERNAME=<username>`

叢集管理密碼：  
 + `AZDATA_PASSWORD=<password>`

> [!NOTE]
> 請注意，在非 AD 模式中，使用者名稱 "root" 必須搭配上述密碼使用，以針對閘道 (Knox) 進行驗證來存取 HDFS/Spark。

## <a name="next-steps"></a>後續步驟

若要深入了解 [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]，請參閱下列資源：

- [什麼是 [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]？](big-data-cluster-overview.md)
- [工作坊：Microsoft [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]架構](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters) \(英文\)
