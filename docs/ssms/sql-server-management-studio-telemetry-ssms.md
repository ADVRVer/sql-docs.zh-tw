---
title: SQL Server Management Studio - 遙測 (SSMS) | Microsoft Docs
ms.custom: ''
ms.date: 02/20/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c28ffa44-7b8b-4efa-b755-c7a3b1c11ce4
caps.latest.revision: 72
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 78e74f96f36c5bfb21859bbc1f4ef1916e061b59
ms.sourcegitcommit: abd71294ebc39695d403e341c4f77829cb4166a8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36926879"
---
# <a name="local-audit-for-ssms-usage-feedback-collection"></a>SSMS 使用意見收集的本機稽核
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
SQL Server Management Studio (SSMS) 包含使用已連線到網際網路的功能，可收集匿名的功能使用方式資料並傳送給 Microsoft。 SSMS 可能會收集標準的電腦資訊以及關於使用方式和效能的資訊，這些資訊可能會傳送給 Microsoft，並基於改善 SSMS 的品質、安全性和可靠性的目的加以分析。 我們不會收集　貴用戶的姓名、地址或是其他連絡資訊等資料。 如需詳細資訊，請參閱 [SQL Server 隱私權聲明](http://go.microsoft.com/fwlink/?LinkID=868444)。

## <a name="audit-feature-usage-data"></a>稽核功能的使用方式資料

若要查看 SSMS 所收集的功能使用方式資料，請執行下列作業：
1.  啟動 SSMS。
2.  按一下 [檢視]，然後按一下主功能表中的 [輸出] 以顯示 [輸出] 視窗。 
3.  當 [輸出] 視窗顯示時，選擇 [顯示輸出來源:] 功能表中的 [遙測]。

當您使用 SSMS 來與資料庫互動時，[輸出] 視窗會顯示所收集的資料。

## <a name="enable-or-disable-usage-feedback-collection-in-ssms"></a>啟用或停用 SSMS 中的使用意見收集

若要選擇參與或退出 SSMS 的使用方式資料收集，請參閱︰[如何設定 SQL Server 2016 以傳送意見給 Microsoft](http://support.microsoft.com/help/3153756/how-to-configure-sql-server-2016-to-send-feedback-to-microsoft)。

## <a name="see-also"></a>另請參閱

[SQL Server 使用意見收集的本機稽核](http://msdn.microsoft.com/library/mt743085.aspx)
