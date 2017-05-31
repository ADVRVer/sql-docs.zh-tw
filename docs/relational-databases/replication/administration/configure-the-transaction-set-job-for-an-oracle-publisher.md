---
title: "設定 Oracle 發行者的交易集作業 | Microsoft Docs"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- TSQL
helpviewer_keywords:
- sp_publisherproperty
- Oracle publishing [SQL Server replication], configuring
ms.assetid: beea1a5c-0053-4971-a68f-0da53063fcbb
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 71b5f3a28a8846cae63917f72b13405fb4f75170
ms.contentlocale: zh-tw
ms.lasthandoff: 04/11/2017

---
# <a name="configure-the-transaction-set-job-for-an-oracle-publisher"></a>設定 Oracle 發行者的交易集作業
  **Xactset** 作業是由在「Oracle 發行者」端執行的複寫所建立的 Oracle 資料庫作業，可在「記錄讀取器代理程式」未與「發行者」連接時建立交易集。 您可以使用複寫預存程序，以程式設計的方式從「散發者」啟用和設定此作業。 如需詳細資訊，請參閱 [Oracle 發行者的效能微調](../../../relational-databases/replication/non-sql/performance-tuning-for-oracle-publishers.md)。  
  
### <a name="to-enable-the-transaction-set-job"></a>若要啟用交易集作業  
  
1.  在「Oracle 發行者」端，將 **job_queue_processes** 初始化參數設定為足夠的值，以允許 Xactset 作業執行。 如需有關此參數的詳細資訊，請參閱「Oracle 發行者」的資料庫文件。  
  
2.  在「散發者」端執行 [sp_publisherproperty &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md)。 針對 **@publisher**指定「Oracle 發行者」的名稱、針對 **@propertyname** @propertyname **@propertyname**的值，並針對 **@propertyvalue** @propertyname **@propertyvalue**。  
  
3.  在「散發者」端執行 [sp_publisherproperty &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md)。 針對 **@publisher**指定「Oracle 發行者」的名稱、針對 **@propertyname** @propertyname **@propertyname**的值，並針對 **@propertyvalue**。  
  
4.  在「散發者」端執行 [sp_publisherproperty &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md)。 針對 **@publisher**指定「Oracle 發行者」的名稱、針對 **@propertyname** @propertyname **@propertyname**的值，並針對 **@propertyvalue** @propertyname **@propertyvalue**。  
  
### <a name="to-configure-the-transaction-set-job"></a>若要設定交易集作業  
  
1.  (選擇性) 在「散發者」端執行 [sp_publisherproperty &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md)。 針對 **@publisher**。 這麼做會傳回「發行者」端 **Xactset** 作業的屬性。  
  
2.  在「散發者」端執行 [sp_publisherproperty &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md)。 針對 **@publisher**的「Oracle 發行者」名稱、指定針對 **@propertyname**所設定之 Xactset 作業屬性的名稱，並指定 **@propertyvalue**。  
  
3.  (選擇性) 針對每個要設定的 Xactset 作業屬性重複步驟 2。 在變更 **xactsetjobinterval** 屬性時，您必須在「Oracle 發行者」上重新啟動作業，新的間隔才會生效。  
  
### <a name="to-view-properties-of-the-transaction-set-job"></a>若要檢視交易集作業的屬性  
  
1.  在「散發者」端執行 [sp_helpxactsetjob](../../../relational-databases/system-stored-procedures/sp-helpxactsetjob-transact-sql.md)。 針對 **@publisher**。  
  
### <a name="to-disable-the-transaction-set-job"></a>若要停用交易集作業  
  
1.  在「散發者」端執行 [sp_publisherproperty &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md)。 針對 **@publisher**指定「Oracle 發行者」的名稱、針對 **@propertyname** @propertyname **@propertyname**的值，並針對 **@propertyvalue** @propertyname **@propertyvalue**。  
  
## <a name="example"></a>範例  
 下列範例會啟用 `Xactset` 作業，並在執行之間設定三分鐘的間隔。  
  
 [!code-sql[HowTo#sp_enable_xactsetjob](../../../relational-databases/replication/codesnippet/tsql/configure-the-transactio_1.sql)]  
  
## <a name="see-also"></a>另請參閱  
 [Oracle 發行者的效能微調](../../../relational-databases/replication/non-sql/performance-tuning-for-oracle-publishers.md)   
 [Replication System Stored Procedures Concepts](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)  
  
  
