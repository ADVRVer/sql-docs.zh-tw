---
description: MSSQLSERVER_10003
title: MSSQLSERVER_10003 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10003 (Database Engine error)
ms.assetid: 9e2cb199-f077-4d88-8117-1b7550afc696
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d25d4a203c5871c4d9542c03e3872dd1206bb543
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88339634"
---
# <a name="mssqlserver_10003"></a>MSSQLSERVER_10003
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>詳細資料  
  
| 屬性 | 值 |  
| :-------- | :---- |  
|產品名稱|SQL Server|  
|事件識別碼|10003|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|HR_E_OUTOFMEMORY|  
|訊息文字|提供者已用完記憶體。|  
  
## <a name="explanation"></a>說明  
系統記憶體不足導致 OLE DB 提供者用完記憶體。  
  
## <a name="user-action"></a>使用者動作  
重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的執行個體。 如果這樣做沒有用，請重新啟動電腦。 如果持續發生此問題，請使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 來收集 OLE DB 追蹤事件，並提供這項資料給 OLE DB 提供者的產品支援部門。  
  
## <a name="see-also"></a>另請參閱  
[SQL Server Profiler 範本和權限](~/tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)  
[SQL Server Native Client &#40;OLE DB&#41;](~/relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
