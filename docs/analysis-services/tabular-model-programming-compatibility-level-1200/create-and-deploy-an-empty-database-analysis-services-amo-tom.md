---
title: 建立及部署的空白資料庫 (Analysis Services AMO-TOM) |Microsoft 文件
ms.custom: ''
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: dcb916e9-97c5-47e0-922a-404891423b2a
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 88d505db25d797d2224857bcf128efdcaadc8a63
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="create-and-deploy-an-empty-database-analysis-services-amo-tom"></a>建立及部署的空白資料庫 (Analysis Services AMO-TOM)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
AMO TOM 程式設計的常見案例是產生資料庫和即時的模型。 這篇文章會引導您建立資料庫的步驟。 

如需表格式解決方案，沒有資料庫和模型，其中包含一個模型，每個資料庫之間的一對一對應。 您通常可以指定一個或另一個，，而且引擎會推斷遺漏的物件。 

建立並部署新的資料庫是三部分工作： 

* 具現化**資料庫**物件，並設定其屬性，其中包括名稱。 

* 新增**資料庫**物件**Server.Databases**集合。 

* 呼叫**更新**方法**資料庫**物件將其儲存到**伺服器**。 

## <a name="code-example-create-empty-database"></a>程式碼範例： 建立空的資料庫 

```
using System; 
using Microsoft.AnalysisServices; 
using Microsoft.AnalysisServices.Tabular; 
 
namespace TOMSamples 
{ 
    class Program 
    { 
        static void Main(string[] args) 
        { 
            // 
            // Connect to the local default instance of Analysis Services 
            // 
            string ConnectionString = "DataSource=localhost"; 
 
            // 
            // The using syntax ensures the correct use of the 
            // Microsoft.AnalysisServices.Tabular.Server object. 
            // 
            using (Server server = new Server()) 
            { 
                server.Connect(ConnectionString); 
 
                // 
                // Generate a new database name and use GetNewName 
                // to ensure the database name is unique. 
                // 
                string newDatabaseName = 
                    server.Databases.GetNewName("New Empty Database"); 
 
                // 
                // Instantiate a new  
                // Microsoft.AnalysisServices.Tabular.Database object. 
                // 
                var blankDatabase = new Database() 
                { 
                    Name = newDatabaseName, 
                    ID = newDatabaseName, 
                    CompatibilityLevel = 1200, 
                    StorageEngineUsed = StorageEngineUsed.TabularMetadata, 
                }; 
                // 
                // Add the new database object to the server's  
                // Databases connection and submit the changes 
                // with full expansion to the server. 
                // 
                server.Databases.Add(blankDatabase); 
                blankDatabase.Update(UpdateOptions.ExpandFull); 

                Console.Write("Database "); 
                Console.ForegroundColor = ConsoleColor.Yellow; 
                Console.Write(blankDatabase.Name); 
                Console.ResetColor(); 
                Console.WriteLine(" created successfully."); 
                Console.WriteLine(); 
            } 
            Console.WriteLine("Press Enter to close this console window."); 
            Console.ReadLine(); 
        } 
    } 
} 
```

## <a name="next-steps"></a>後續的步驟 

一旦建立資料庫時，您可以加入模型物件： 

- [將資料來源加入至表格式模型](../../analysis-services/tabular-model-programming-compatibility-level-1200/add-a-data-source-to-tabular-model-analysis-services-amo-tom.md)
- [表格式模型中建立資料表、 資料分割和資料行](../../analysis-services/tabular-model-programming-compatibility-level-1200/create-tables-partitions-and-columns-in-a-tabular-model.md)
 
