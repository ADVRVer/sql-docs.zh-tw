---
title: "SQLAllocConnect 對應 |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLAllocConnect function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLAllocConnect
ms.assetid: ac89dd1f-c565-47cc-8fa3-6fa5f80b5d63
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7a699be0e0c93ea48646375c0f6d9c0ab55ba74a
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2017
---
# <a name="sqlallocconnect-mapping"></a>SQLAllocConnect 對應
當應用程式呼叫**SQLAllocConnect**透過 ODBC 3。*x*驅動程式，會呼叫**SQLAllocConnect**(*henv*， *phdbc*) 會對應至**SQLAllocHandle** ，如下所示：  
  
1.  驅動程式管理員配置的連接，並傳回至應用程式。  
  
2.  當應用程式建立連接時，驅動程式管理員呼叫  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_DBC, InputHandle, OutputHandlePtr)  
    ```  
  
     在驅動程式搭配*InputHandle*設*henv*，和*OutputHandlePtr*設*phdbc*。
