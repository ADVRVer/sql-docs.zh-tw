---
title: 工作主機容器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.taskhostcontainer.f1
helpviewer_keywords:
- containers [Integration Services], Task Host
- Task Host container
ms.assetid: 7394a2c2-1b07-427d-b94a-9792e7783d35
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 9d5c965f4012244a3ccc2eb80470205e8d55e887
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "62830055"
---
# <a name="task-host-container"></a>工作主機容器
  工作主機容器會封裝單一工作。 在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師中，工作主機不會另外設定，而是在您設定其封裝之工作的屬性時設定。 如需工作主機容器所封裝工作的詳細資訊，請參閱 [Integration Services 工作](integration-services-tasks.md)。  
  
 此容器會將變數與事件處理常式的使用延伸至工作層級。 如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 事件處理常式](../integration-services-ssis-event-handlers.md)和 [Integration Services &#40;SSIS&#41; 變數](../integration-services-ssis-variables.md)。  
  
## <a name="configuration-of-the-task-host"></a>設定工作主機  
 您可以在  **的 [屬性]** [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 視窗中，或以程式設計方式設定屬性。  
  
 如需在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中設定這些屬性的相關資訊，請參閱 [設定工作或容器的屬性](../set-the-properties-of-a-task-or-container.md)。  
  
 如需以程式設計方式設定這些屬性的詳細資訊，請參閱 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>。  
  
## <a name="related-tasks"></a>相關工作  
  
-   [設定工作或容器的屬性](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a>另請參閱  
 [Integration Services 容器](integration-services-containers.md)  
  
  
