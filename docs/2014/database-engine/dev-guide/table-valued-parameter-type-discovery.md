---
title: 資料表值參數類型探索 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, type discovery
ms.assetid: f55818c2-ebb5-4cf6-8c0c-0da41f592560
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cf3f7b4d6754902ac38172ffa0e8fc392599d307
ms.sourcegitcommit: b87c384e10d6621cf3a95ffc79d6f6fad34d420f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60154834"
---
# <a name="table-valued-parameter-type-discovery"></a>資料表值參數類型探索
  取用者-亦即，用戶端應用程式使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者可以探索每個命令參數的型別，如果命令文字已經提供給 OLE DB 提供者。 知道了資料表值參數的類型之後，取用者就可以針對資料表值參數的每一個個別資料行來探索中繼資料資訊。  
  
 對於大部分的參數類型支援 icommandwithparameters:: Getparameterinfo 程序參數的型別資訊。 開頭[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]，採用使用者定義型別和`xml`資料型別，GetParameterInfo 方法無法滿足此用途因為它不提供使用者定義型別資訊 (名稱、 結構描述，以及透過 ICommandWithParameters 目錄）。 新的介面，ISSCommandWithParameters，被定義為提供擴充的類型資訊。  
  
 資料表值參數，您也使用 ISSCommandWithParameters 介面來探索的詳細的資訊。 用戶端會呼叫 ISSCommandWithParameters::GetParameterInfo 準備命令物件之後。 如果是資料表值參數，DBPARAMINFO 結構的 *wType* 成員會由提供者設定為 DBTYPE_TABLE。 DBPARAMINFO 結構的 *ulParamSize* 欄位具有 ~0 的值。  
  
 然後取用者會使用 ISSCommandWithParameters::GetParameterProperties 來要求其他屬性 (資料表值參數類型目錄名稱、資料表值參數類型結構描述名稱、資料表值參數類型名稱、資料行排序和預設資料行)。  
  
 如果在知道了類型名稱之後要擷取個別資料行資訊，取用者必須呼叫 IOpenRowset::OpenRowsetor 或取得 DBSCHEMA_TABLE_TYPE_COLUMNS 資料列集，其方式是將資料表值參數類型名稱指定為資料表名稱。  
  
## <a name="see-also"></a>另請參閱  
 [資料表值參數 &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [使用資料表值參數 &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
