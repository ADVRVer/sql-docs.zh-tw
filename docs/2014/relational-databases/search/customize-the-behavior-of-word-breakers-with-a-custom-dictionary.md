---
title: 使用自訂字典自訂斷詞工具行為 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
ms.assetid: a8e278d1-aeaa-48f1-a0c6-5de232c983e4
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d5bf593282108c2059e85a542317fb4d38753d83
ms.sourcegitcommit: 45a9d7ffc99502c73f08cb937cbe9e89d9412397
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2019
ms.locfileid: "66011452"
---
# <a name="customize-the-behavior-of-word-breakers-with-a-custom-dictionary"></a>使用自訂字典自訂斷詞工具行為
  您可以建立語言特有自訂字典檔案，以自訂特定語言之斷詞工具的行為。 例如，您可以防止斷詞工具中斷特定詞彙或模式。  
  
 如需詳細資訊，請參閱下列 SharePoint 文章：  
  
 [建立自訂字典 (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?LinkId=215011)  
  
 針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，將自訂字典檔案放入下列資料夾中：  
  
 `C:\Program Files\Microsoft SQL Server\<instance name>\MSSQL\Binn`  
  
 建立或變更自訂字典檔案之後，請使用下列命令重新啟動 SQL 全文檢索背景程式啟動器：  
  
 `exec sp_fulltext_service 'restart_all_fdhosts'`  
  
  
