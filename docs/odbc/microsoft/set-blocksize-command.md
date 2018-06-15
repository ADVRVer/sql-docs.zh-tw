---
title: SET BLOCKSIZE 命令 |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- set blocksize command [ODBC]
ms.assetid: 0c11580f-37f5-4a8e-99be-9fb9c44bb433
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 85b9df4f40c68d68ea28a4bfad006105e4a98d7b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32901813"
---
# <a name="set-blocksize-command"></a>SET BLOCKSIZE 命令
指定如何配置備忘欄位的儲存體的磁碟空間。  
  
## <a name="syntax"></a>語法  
  
```  
  
SET BLOCKSIZE TO nBytes  
```  
  
## <a name="arguments"></a>引數  
 *nBytes*  
 指定磁碟空間，附註欄位為已配置的區塊大小。 如果*nBytes*是 0，單一位元組 （1 個位元組的區塊） 中配置磁碟空間。 如果*nBytes*是介於 1 到 32、 磁碟空間之間的整數的區塊中配置給*nBytes*位元組乘以 512。 如果*nBytes* 32、 大於配置的區塊中的磁碟空間*nBytes*位元組。 如果您指定大於 32 的區塊大小值，您可以儲存大量的磁碟空間。  
  
## <a name="remarks"></a>備註  
 設定區塊大小的預設值為 64。 若要建立檔案之後，請重設為不同值的區塊大小，將它設定為新的值，然後使用複製來建立新的資料表。 新的資料表有指定的區塊大小。
