---
title: SQL Server 機器學習服務使用 Python |Microsoft 文件
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: b8ef234b0e8c09e3d4be9488b7ac628c225e67f6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31201990"
---
# <a name="sql-server-machine-learning-services-with-python"></a>SQL Server 機器學習服務使用 Python
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Python 是機器的一種語言，提供了相當大的彈性而且各種不同學習工作的功能。 For Python 開放原始碼程式庫包含數個平台，可自訂的類神經網路，以及常用的程式庫進行自然語言處理。 現在，在 SQL Server 2017 機器學習中支援這個廣泛使用的語言。

因為與整合 Python[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資料庫引擎，您可以讓分析資料並不需要成本和移動資料相關聯的安全性風險。  您可以部署使用方便且熟悉的工具，例如 Visual Studio 的 Python 為基礎的機器學習解決方案。 生產應用程式可以取得模型的預測或視覺效果的 Python 3.5 執行階段，只需呼叫 T-SQL 預存程序。

此版本包含 Python 的 Anaconda 發佈與[revoscalepy](../python/what-is-revoscalepy.md)程式庫，以改善的小數位數和您的機器學習解決方案的效能。

您可以安裝您要開始使用 Python 透過 SQL Server 2017 安裝程式的所有項目：

+ [**機器學習服務 （資料庫）**](../install/sql-machine-learning-services-windows-install.md)： 安裝這項功能，以及 SQL Server 資料庫引擎，以啟用安全執行 Python 指令碼上[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]電腦。
  
     當您選取這項功能，擴充功能會安裝在資料庫引擎可支援執行 Python 指令碼，並建立新的服務時，[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]來管理 Python 執行階段之間的通訊和[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體。

+ [**機器學習的伺服器 （獨立）**](../install/sql-machine-learning-standalone-windows-install.md)： 如果您不需要 SQL Server 整合，安裝才能取得分散式的機器學習的 Python 和 R 支援這項功能。

## <a name="see-also"></a>另請參閱

+ [SQL Server 機器學習和 R 服務 （資料庫）](../r/sql-server-r-services.md)
+ [SQL Server 機器學習和 R 伺服器 （獨立）](../r/r-server-standalone.md)
+ [Python 架構](architecture-overview-sql-server-python.md)
+ [Python 教學課程](../tutorials/sql-server-python-tutorials.md)
