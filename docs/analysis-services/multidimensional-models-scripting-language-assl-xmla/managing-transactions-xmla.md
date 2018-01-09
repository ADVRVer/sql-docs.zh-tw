---
title: "管理交易 (XMLA) |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- XML for Analysis, transactions
- XMLA, transactions
- explicit transactions [XMLA]
- implicit transactions
- transactions [XML for Analysis]
- rolling back transactions, XMLA
- reference counts [XML for Analysis]
- committing transactions
- starting transactions
ms.assetid: f5112e01-82f8-4870-bfb7-caa00182c999
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: dde9ffdff1ffb209cea7afeb4de5849bedea83fd
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2018
---
# <a name="managing-transactions-xmla"></a>管理交易 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]每個 XML for Analysis (XMLA) 命令傳送至執行個體[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]目前隱含或明確工作階段上的交易內容中執行。 若要管理每個交易，您使用[BeginTransaction](../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md)， [CommitTransaction](../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)，和[RollbackTransaction](../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md)命令。 透過使用這些命令，您可以建立隱含或是明確的交易、變更交易參考計數，以及開始、認可或是回復交易。  
  
## <a name="implicit-and-explicit-transactions"></a>隱含與明確交易。  
 交易是隱含或明確的：  
  
 **隱含交易**  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]建立*隱含*為 xmla 命令，如果**BeginTransaction**命令未指定開始的交易。 如果命令成功，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 永遠都會認可隱含交易。而如果命令失敗，則會回復隱含交易。  
  
 **明確交易**  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]建立*明確*交易如果**BeginTransaction**命令啟動的交易。 不過，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]只會認可明確交易如果**CommitTransaction**命令會傳送，而且如果回復明確交易**RollbackTransaction**傳送命令。  
  
 此外，如果目前的工作階段在使用中交易完成之前就結束了目前的工作階段，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 則會回復隱含交易和明確交易。  
  
## <a name="transactions-and-reference-counts"></a>交易和參考計數  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會為每個工作階段維護一個交易參考計數。 不過，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 並不支援巢狀交易，因為每個工作階段都只會維護一個使用中交易。 如果目前的工作階段沒有使用中交易，則會將交易參考計數設定為 0。  
  
 換句話說，每個**BeginTransaction**命令的參考計數遞增一，而每一個**CommitTransaction**命令遞減參考計數的其中一個。 如果**CommitTransaction**命令會將交易計數設定為零，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]認可交易。  
  
 不過， **RollbackTransaction**命令會回復交易參考計數在使用中交易目前的值為何。 換句話說，單一**RollbackTransaction**命令會回復使用中的交易，不論多少**BeginTransaction**命令或**CommitTransaction**命令所送出，並設定交易參考計數為零。  
  
## <a name="beginning-a-transaction"></a>開始交易  
 **BeginTransaction**命令開始明確交易目前的工作階段上，並依其中一個目前工作階段遞增交易參考計數。 所有後續的命令會被視為在使用中交易，直到足夠**CommitTransaction**命令傳送至使用中交易或單一認可**RollbackTransaction**傳送命令來回復使用中交易。  
  
## <a name="committing-a-transaction"></a>認可交易  
 **CommitTransaction**命令認可之後所執行的命令的結果**BeginTransaction**命令已在目前工作階段上執行。 每個**CommitTransaction**命令遞減參考計數的使用中交易的工作階段上。 如果**CommitTransaction**命令將參考計數設定為零，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]認可使用中交易。 如果沒有使用中交易 （換句話說，交易參考計數，目前工作階段已設定為零）， **CommitTransaction**命令會產生錯誤。  
  
## <a name="rolling-back-a-transaction"></a>回復交易  
 **RollbackTransaction**命令會回復之後所執行的命令的結果**BeginTransaction**命令已在目前工作階段上執行。 **RollbackTransaction**命令會回復使用中交易，不論目前的交易參考計數，並將交易參考計數設定為零。 如果沒有使用中交易 （換句話說，交易參考計數，目前工作階段已設定為零）， **RollbackTransaction**命令會產生錯誤。  
  
## <a name="see-also"></a>請參閱  
 [在 Analysis Services 中使用 XMLA 進行開發](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
