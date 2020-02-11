---
title: SQLAllocEnv 對應 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLAllocEnv function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLAllocEnv
ms.assetid: 4bb51845-ee91-4b97-9dd4-2fab977f2aec
author: MightyPen
ms.author: genemi
ms.openlocfilehash: afbd1404cb40408166ecfc59993db7b183ae5ed2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68065010"
---
# <a name="sqlallocenv-mapping"></a>SQLAllocEnv 對應
當應用程式*透過 ODBC 3.x 驅動程式呼叫* **SQLAllocEnv**時， **SQLAllocEnv**（*Phenv*）的呼叫會對應到**SQLAllocHandle** ，如下所示：  
  
1.  驅動程式管理員會配置環境控制碼，並將它傳回給應用程式。 驅動程式管理員會呼叫**SQLSetEnvAttr** ，將 SQL_ATTR_ODBC_VERSION 環境屬性設定為 SQL_OV_ODBC2。  
  
2.  當應用程式建立與驅動程式的第一個連接時，驅動程式管理員會呼叫  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, OutputHandlePtr)  
    ```  
  
     在*OutputHandlePtr*設定為*phenv*的驅動程式中。
