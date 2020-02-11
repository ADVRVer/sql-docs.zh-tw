---
title: 設定「For 迴圈」容器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], For Loop
- For Loop containers
ms.assetid: b9cd7ea7-b198-4a35-8b16-6acf09611ca5
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: fe51deb631f0c3d794bdce3f05af61b5e030d5e3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "66060833"
---
# <a name="configure-a-for-loop-container"></a>設定 For 迴圈容器
  此程序描述如何使用 [For 迴圈編輯器]**** 對話方塊設定「For 迴圈」容器。  
  
 如需 For 迴圈容器的範例，請參閱 bimonkey.com 上的 [SSIS Loops that do not fail](https://go.microsoft.com/fwlink/?LinkId=240295)。  
  
### <a name="to-configure-the-for-loop-container"></a>設定 For 迴圈容器  
  
1.  在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中，按兩下「For 迴圈」容器以開啟 [For 迴圈編輯器]****。  
  
2.  (選擇性) 修改「For 迴圈」容器的名稱和描述。  
  
3.  (選擇性) 在 [InitExpression]**** 文字方塊中輸入初始化運算式。  
  
4.  在 [EvalExpression]**** 文字方塊中輸入評估運算式。  
  
    > [!NOTE]  
    >  運算式必須評估為布林。 如果運算式的評估為 `false`，迴圈將停止執行。  
  
5.  (選擇性) 在 [AssignExpression]**** 文字方塊中輸入指派運算式。  
  
6.  (選擇性) 按一下 [運算式]****，然後在 [運算式]**** 頁面上建立「For 迴圈」容器之屬性的屬性運算式。 如需詳細資訊，請參閱[加入或變更屬性運算式](expressions/add-or-change-a-property-expression.md)。  
  
7.  按一下 [確定]****，以關閉 [For 迴圈編輯器]****。  
  
## <a name="see-also"></a>另請參閱  
 [For 迴圈容器](control-flow/for-loop-container.md)   
 [Integration Services &#40;SSIS&#41; 運算式](expressions/integration-services-ssis-expressions.md)   
 [在套件中使用屬性運算式](expressions/use-property-expressions-in-packages.md)  
  
  
