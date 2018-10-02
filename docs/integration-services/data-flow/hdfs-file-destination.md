---
title: HDFS 檔案目的地 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.ssis.designer.hdfsfiledest.f1
ms.assetid: 4338ce9f-c077-4301-aca5-47ed070ec94d
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: addb3312def505802aab695301f7cca170eab3d7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47799666"
---
# <a name="hdfs-file-destination"></a>HDFS 檔案目的地
  HDFS 檔案目的地元件可讓 SSIS 封裝將資料寫入 HDFS 檔案。 支援的檔案格式為文字、Avro 和 ORC。  
  
 若要設定 HDFS 檔案目的地，請將 HDFS 檔案來源拖放到資料流程設計師，然後按兩下元件以開啟編輯器。  
  
 ![HDFS 檔案目的地編輯器](../../integration-services/data-flow/media/hdfs-file-dest.png "HDFS 檔案目的地編輯器")  
  
## <a name="options"></a>選項。  
 在 [Hadoop File Destination Editor (Hadoop 檔案目的地編輯器)] 對話方塊的 [一般] 索引標籤上，設定下列選項。  
  
|欄位|Description|  
|-----------|-----------------|  
|**Hadoop 連接**|指定現有的 Hadoop 連接管理員或建立新的連接管理員。 此連接管理員會指出 HDFS 檔案的裝載位置。|  
|**檔案路徑**|指定 HDFS 檔案的名稱。|  
|**檔案格式**|指定 HDFS 檔案的格式。 可用的選項為文字、Avro 和 ORC。|  
|**資料行分隔符號字元**|如果您選取文字格式，請指定資料行分隔符號字元。|  
|**第一個資料列的資料行名稱**|如果您選取文字格式，請指定檔案中的第一個資料列是否包含資料行名稱。|  
  
 設定這些選項之後，請選取 [資料行] 索引標籤，將資料流程中的來源資料行對應至目的地資料行。  
  
## <a name="see-also"></a>另請參閱  
 [Hadoop 連接管理員](../../integration-services/connection-manager/hadoop-connection-manager.md)   
 [HDFS 檔案來源](../../integration-services/data-flow/hdfs-file-source.md)  
  
  
