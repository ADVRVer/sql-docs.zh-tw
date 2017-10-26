---
title: "ConfigTranslator 函式 |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- ConfigTranslator
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- ConfigTranslator
helpviewer_keywords:
- ConfigTranslator [ODBC]
ms.assetid: 7c22f07e-36de-425b-aa67-e32a84afae92
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f9de00042d81ac74bbda54be2060a331cf1ac3ad
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="configtranslator-function"></a>ConfigTranslator 函式
**一致性**  
 版本引進了： ODBC 2.0  
  
 **摘要**  
 **ConfigTranslator**轉譯器會傳回預設轉譯選項。 它可以是轉譯程式 DLL 或個別的安裝程式 DLL。  
  
## <a name="syntax"></a>語法  
  
```  
  
BOOL ConfigTranslator(  
     HWND     hwndParent,  
     DWORD *  pvOption);  
```  
  
## <a name="arguments"></a>引數  
 *hwndParent*  
 [輸入]父視窗控制代碼。 如果控制代碼為 null，函式不會顯示任何對話方塊。  
  
 *pvOption*  
 [輸出]32 位元轉譯選項。  
  
## <a name="returns"></a>傳回值  
 如果成功，FALSE 如果失敗，則函數會傳回 TRUE。  
  
## <a name="diagnostics"></a>診斷  
 當**ConfigTranslator**傳回 FALSE，相關聯* \*pfErrorCode*值由呼叫張貼至安裝程式錯誤緩衝區**SQLPostInstallerError**而且可以藉由呼叫取得**SQLInstallerError**。 下表列出* \*pfErrorCode*可以傳回的值**SQLInstallerError** ，並說明每個內容中的這個函式。  
  
|*\*pfErrorCode*|錯誤|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_HWND|無效的視窗控制代碼|*HwndParent*引數以前是無效或為 NULL。|  
|ODBC_ERROR_DRIVER_SPECIFIC|特定驅動程式或轉譯器錯誤|驅動程式特有的錯誤，它沒有任何已定義的 ODBC 安裝程式發生錯誤。 *SzError*呼叫中的引數**SQLPostInstallerError**函式應該包含驅動程式特有的錯誤訊息。|  
|ODBC_ERROR_INVALID_OPTION|無效的轉譯選項|*PvOption*引數包含無效的值。|  
  
## <a name="comments"></a>註解  
 如果轉譯器支援只有單一轉譯選項**ConfigTranslator** ，則傳回 TRUE，並設定*pvOption*至 32 位元選項。 否則，它會判斷要使用的預設轉譯選項。 **ConfigTranslator**可以顯示與使用者選取預設轉譯選項的對話方塊。  
  
## <a name="related-functions"></a>相關函數  
  
|如需詳細資訊|請參閱|  
|---------------------------|---------|  
|取得轉譯選項|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|選取的轉譯器|[SQLGetTranslator](../../../odbc/reference/syntax/sqlgettranslator-function.md)|  
|設定轉譯選項|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|

