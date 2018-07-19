---
title: 大型 CLR 使用者定義型別 (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-ole-db
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- large CLR user-defined types [OLE DB]
ms.assetid: 4bf12058-0534-42ca-a5ba-b1c23b24d90f
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 36a553d8c9117289d1c20174fe3c7f1a4a70511a
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37408357"
---
# <a name="large-clr-user-defined-types-ole-db"></a>大型 CLR 使用者定義型別 (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  本主題討論 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 中 OLE DB 的變更，以支援大型 Common Language Runtime (CLR) 使用者定義型別 (UDT)。  
  
 如需中的大型 CLR Udt 支援的詳細資訊[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]原生用戶端，請參閱[Large CLR User-Defined 類型](../../../relational-databases/native-client/features/large-clr-user-defined-types.md)。 如需範例，請參閱[使用大型 CLR Udt &#40;OLE DB&#41;](../../../relational-databases/native-client-ole-db-how-to/use-large-clr-udts-ole-db.md)。  
  
## <a name="data-format"></a>資料格式  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 使用 ~0 來代表大型物件 (LOB) 類型的無限制大小的值長度。 ~0 也代表大於 8,000 個位元組的 CLR UDT 大小。  
  
 下表顯示參數和資料列集內的資料類型對應：  
  
|SQL Server 資料類型|OLE DB 資料類型|記憶體配置|值|  
|--------------------------|----------------------|-------------------|-----------|  
|CLR UDT|DBTYPE_UDT|BYTE [] （位元組陣列\)|132 (oledb.h)|  
  
 UDT 值會表示為位元組陣列。 支援與十六進位字串之間的來回轉換。 常值會表示為具有 "0x" 前置詞的十六進位字串。 十六進位字串是基底 16 的二進位資料文字表示法。 範例是從伺服器類型轉換**varbinary(10)** 至 DBTYPE_STR，這會導致 20 個字元，其中每一組字元都代表單一位元組的十六進位表示法。  
  
## <a name="parameter-properties"></a>參數屬性  
 DBPROPSET_SQLSERVERPARAMETER 屬性集會透過 OLE DB 支援 UDT。 如需詳細資訊，請參閱 < [Using User-Defined 類型](~/relational-databases/native-client/features/using-user-defined-types.md)。  
  
## <a name="column-properties"></a>資料行屬性  
 DBPROPSET_SQLSERVERCOLUMN 屬性集會透過 OLE DB 支援資料表的建立。 如需詳細資訊，請參閱 < [Using User-Defined 類型](~/relational-databases/native-client/features/using-user-defined-types.md)。  
  
## <a name="data-type-mapping-in-itabledefinitioncreatetable"></a>ITableDefinition::CreateTable 中的資料類型對應  
 下列資訊會在**DBCOLUMNDESC** itabledefinition:: Createtable 需要 UDT 資料行時使用的結構：  
  
|OLE DB 資料類型 (*wType*)|*pwszTypeName*|SQL Server 資料類型|*rgPropertySets*|  
|----------------------------------|--------------------|--------------------------|----------------------|  
|DBTYPE_UDT|忽略|UDT|必須包含 DBPROPSET_SQLSERVERCOLUMN 屬性集。|  
  
## <a name="icommandwithparametersgetparameterinfo"></a>ICommandWithParameters::GetParameterInfo  
 以 DBPARAMINFO 結構透過傳回的資訊**prgParamInfo**如下所示：  
  
|參數類型|*wType*|*ulParamSize*|*bPrecision*|*bScale*|*dwFlags* DBPARAMFLAGS_ISLONG|  
|--------------------|-------------|-------------------|------------------|--------------|------------------------------------|  
|DBTYPE_UDT<br /><br /> (長度小於或等於 8,000 個位元組)|"DBTYPE_UDT"|*n*|未定義|未定義|清除|  
|DBTYPE_UDT<br /><br /> (長度大於 8,000 個位元組)|"DBTYPE_UDT"|~0|未定義|未定義|集合|  
  
## <a name="icommandwithparameterssetparameterinfo"></a>ICommandWithParameters::SetParameterInfo  
 以 DBPARAMBINDINFO 結構所提供的資訊必須與下列相符：  
  
|參數類型|*pwszDataSourceType*|*ulParamSize*|*bPrecision*|*bScale*|*dwFlags* DBPARAMFLAGS_ISLONG|  
|--------------------|--------------------------|-------------------|------------------|--------------|------------------------------------|  
|DBTYPE_UDT<br /><br /> (長度小於或等於 8,000 個位元組)|DBTYPE_UDT|*n*|忽略|忽略|如果要使用 DBTYPE_IUNKNOWN 傳遞此參數，則必須設定。|  
|DBTYPE_UDT<br /><br /> (長度大於 8,000 個位元組)|DBTYPE_UDT|~0|忽略|忽略|忽略|  
  
## <a name="isscommandwithparameters"></a>ISSCommandWithParameters  
 應用程式會使用**ISSCommandWithParameters**來取得和設定參數屬性 區段中定義的參數屬性。  
  
## <a name="icolumnsrowsetgetcolumnsrowset"></a>IColumnsRowset::GetColumnsRowset  
 傳回的資料行如下：  
  
|資料行類型|DBCOLUMN_TYPE|DBCOLUMN_COLUMNSIZE|DBCOLUMN_PRECISION|DBCOLUMN_SCALE|DBCOLUMN_FLAGS_ISLONG|DBCOLUMNS_ISSEARCHABLE|DBCOLUMN_OCTETLENGTH|  
|-----------------|--------------------|--------------------------|-------------------------|---------------------|-----------------------------|-----------------------------|---------------------------|  
|DBTYPE_UDT<br /><br /> (長度小於或等於 8,000 個位元組)|DBTYPE_UDT|*n*|NULL|NULL|Clear|DB_ALL_EXCEPT_LIKE|n|  
|DBTYPE_UDT<br /><br /> (長度大於 8,000 個位元組)|DBTYPE_UDT|~0|NULL|NULL|將|DB_ALL_EXCEPT_LIKE|0|  
  
 下列資料行也會針對 UDT 而定義：  
  
|資料行識別碼|類型|描述|  
|-----------------------|----------|-----------------|  
|DBCOLUMN_UDT_CATALOGNAME|DBTYPE_WSTR|對於 UDT 資料行而言，此為定義 UDT 之目錄的名稱。|  
|DBCOLUMN_UDT_SCHEMANAME|DBTYPE_WSTR|對於 UDT 資料行而言，此為定義 UDT 之結構描述的名稱。|  
|DBCOLUMN_UDT_NAME|DBTYPE_WSTR|對於 UDT 資料行而言，此為 UDT 的單一部分名稱。|  
|DBCOLUMN_ASSEMBLY_TYPENAME|DBTYPE_WSTR|對於 UDT 資料行而言，此為 UDT 的完整類型名稱。 組件類型的完整名稱可以讓您使用 Type.GetType 方法來具現化該類型的物件。|  
  
## <a name="icolumnsinfogetcolumninfo"></a>IColumnsInfo::GetColumnInfo  
 以 DBCOLUMNINFO 結構所傳回的資訊如下：  
  
|參數類型|*wType*|*ulColumnSize*|*bPrecision*|*bScale*|*dwFlags*<br /><br /> DBCOLUMNFLAGS_ISLONG|  
|--------------------|-------------|--------------------|------------------|--------------|-----------------------------------------|  
|DBTYPE_UDT<br /><br /> (長度小於或等於 8,000 個位元組)|DBTYPE_UDT|*n*|~0|~0|Clear|  
|DBTYPE_UDT<br /><br /> (長度大於 8,000 個位元組)|DBTYPE_UDT|~0|~0|~0|將|  
  
## <a name="columns-rowset-schema-rowsets"></a>COLUMNS 資料列集 (結構描述資料列集)  
 下列資料行值是針對 UDT 類型所傳回：  
  
|資料行類型|DATA_TYPE|COLUMN_FLAGS、DBCOLUMFLAGS_ISLONG|CHARACTER_OCTET_LENGTH|  
|-----------------|----------------|-----------------------------------------|------------------------------|  
|DBTYPE_UDT<br /><br /> (長度小於或等於 8,000 個位元組)|DBTYPE_UDT|Clear|*n*|  
|DBTYPE_UDT<br /><br /> (長度大於 8,000 個位元組)|DBTYPE_UDT|將|0|  
  
 下列其他資料行也會針對 UDT 而定義：  
  
|資料行識別碼|類型|描述|  
|-----------------------|----------|-----------------|  
|SS_UDT_CATALOGNAME|DBTYPE_WSTR|對於 UDT 資料行而言，此為定義 UDT 之目錄的名稱。|  
|SS_UDT_SCHEMANAME|DBTYPE_WSTR|對於 UDT 資料行而言，此為定義 UDT 之結構描述的名稱。|  
|SS_UDT_NAME|DBTYPE_WSTR|對於 UDT 資料行而言，此為 UDT 的單一部分名稱。|  
|SS_ASSEMBLY_TYPENAME|DBTYPE_WSTR|對於 UDT 資料行而言，此為 UDT 的完整類型名稱。 組件類型的完整名稱可以讓您使用 Type.GetType 方法來具現化該類型的物件。|  
  
 有關 PROCEDURE_PARAMETERS 資料列集方面，DATA_TYPE 會包含與 COLUMNS 結構描述資料列集相同的值，而 TYPE_NAME 則會包含 UDT。 也會定義相同的其他資料行。  
  
 使用者定義型別不會出現在 PROVIDER_TYPES 結構描述資料列集中。  
  
## <a name="bindings-and-conversions"></a>繫結和轉換  
  
|繫結資料類型|UDT 到伺服器|非 UDT 到伺服器|從伺服器中的 UDT|從伺服器中的非 UDT|  
|----------------------|-------------------|------------------------|---------------------|--------------------------|  
|DBTYPE_UDT|支援 (5)|錯誤 (1)|支援 (5)|錯誤 (4)|  
|DBTYPE_BYTES|支援 (5)|不適用|支援 (5)|不適用|  
|DBTYPE_WSTR|支援 (2)、(5)|不適用|支援 (3)、(5)、(6)|不適用|  
|DBTYPE_BSTR|支援 (2)、(5)|不適用|支援 (3)、 (5)|不適用|  
|DBTYPE_STR|支援 (2)、(5)|不適用|支援 (3)、 (5)|不適用|  
|DBTYPE_IUNKNOWN|支援 (6)|不適用|支援 (6)|不適用|  
|DBTYPE_VARIANT (VT_UI1 &AMP;#124; VT_ARRAY)|支援 (5)|不適用|支援 (3)、 (5)|不適用|  
|DBTYPE_VARIANT (VT_BSTR)|支援 (2)、(5)|不適用|不適用|不適用|  
  
### <a name="key-to-symbols"></a>符號的索引鍵  
  
|符號|意義|  
|------------|-------------|  
|1|如果指定了 DBTYPE_UDT 以外的伺服器類型**icommandwithparameters:: Setparameterinfo**而且存取子類型為 DBTYPE_UDT，執行陳述式時，就會發生錯誤。  此錯誤將是 DB_E_ERRORSOCCURRED，而參數狀態將是 DBSTATUS_E_BADACCESSOR。<br /><br /> 針對不是 UDT 的伺服器參數指定 UDT 類型的參數是一項錯誤。|  
|2|資料會從十六進位字串轉換成二進位資料。|  
|3|資料會從二進位資料轉換成十六進位字串。|  
|4|使用時，可能會進行驗證**CreateAccessor**或是**GetNextRows**。 錯誤是 DB_E_ERRORSOCCURRED。 繫結狀態設定為 DBBINDSTATUS_UNSUPPORTEDCONVERSION。|  
|5|可能會使用 BY_REF。|  
|6|UDT 參數可以在 DBBINDING 中繫結為 DBTYPE_IUNKNOWN。 繫結至 DBTYPE_IUNKNOWN 表示應用程式想要將資料當作使用 ISequentialStream 介面以資料流處理。 當取用者的指定*wType*繫結為類型 DBTYPE_IUNKNOWN，並對應資料行或輸出中的預存程序的參數是 UDT，SQL Server Native Client 會傳回 ISequentialStream。 輸入參數，如 SQL Server Native Client 將查詢的 ISequentialStream 介面。<br /><br /> 在大型 UDT 的情況下，您可以選擇不要在使用 DBTYPE_IUNKNOWN 繫結時繫結 UDT 資料的長度。 不過，小型 UDT 則必須繫結長度。 如果下列其中一項或多項成立，則 DBTYPE_UDT 參數可以指定為大型 UDT：<br />*ulParamParamSize*為 ~ 0。<br />DBPARAMFLAGS_ISLONG 會在 DBPARAMBINDINFO 結構中設定。<br /><br /> 對於資料列資料而言，DBTYPE_IUNKNOWN 繫結只適用於大型 UDT。 您可以找出資料行是否為大型 UDT 類型的資料列集上使用 icolumnsinfo:: Getcolumninfo 方法或命令物件的 IColumnsInfo 介面。 如果下列其中一項或多項成立，則 DBTYPE_UDT 資料行會是大型 UDT 資料行：<br />DBCOLUMNFLAGS_ISLONG 旗標設定*dwFlags* DBCOLUMNINFO 結構的成員。 <br />*ulColumnSize* DBCOLUMNINFO 的成員為 ~ 0。|  
  
 DBTYPE_NULL 和 DBTYPE_EMPTY 可以針對輸入參數而繫結，但是不能針對輸出參數或結果而繫結。 當針對輸入參數來繫結時，狀態必須針對 DBTYPE_NULL 設定為 DBSTATUS_S_ISNULL，或針對 DBTYPE_EMPTY 設定為 DBSTATUS_S_DEFAULT。 DBTYPE_BYREF 不適用於 DBTYPE_NULL 或 DBTYPE_EMPTY。  
  
 DBTYPE_UDT 也可以轉換成 DBTYPE_EMPTY 或 DBTYPE_NULL。 不過，DBTYPE_NULL 和 DBTYPE_EMPTY 不能轉換成 DBTYPE_UDT。 這與 DBTYPE_BYTES 一致。 **ISSCommandWithParameters**用來處理 Udt 做為參數。  
  
 OLE DB 核心服務所提供的資料轉換 (**IDataConvert**) 並不適用於 DBTYPE_UDT。  
  
 不支援其他任何繫結。  
  
## <a name="comparability-for-irowsetfind"></a>IRowsetFind 的相容性  
 對於 UDT 類型而言，只支援下列比較：  
  
-   EQ  
  
-   NE  
  
-   IGNORE  
  
 如果嘗試其他任何比較，就會傳回 DB_E_BADCOMPAREOP。  
  
## <a name="bcp-support-for-udts"></a>UDT 的 BCP 支援  
 UDT 值只能當做字元或二進位值來匯入及匯出。  
  
## <a name="down-level-client-behavior-for-udts"></a>UDT 的下層用戶端行為  
 UDT 受限於與下層用戶端對應的類型，如下所示：  
  
|用戶端版本|DBTYPE_UDT<br /><br /> (長度小於或等於 8,000 個位元組)|DBTYPE_UDT<br /><br /> (長度大於 8,000 個位元組)|  
|--------------------|------------------------------------------------------------------|---------------------------------------------------------|  
|SQL Server 2005|UDT|varbinary(max)|  
|SQL Server 2008 及更新版本|UDT|UDT|  
  
 當**DataTypeCompatibility** (SSPROP_INIT_DATATYPECOMPATIBILITY) 設定為"80"，大型 UDT 類型給用戶端會出現在相同的方式出現下層用戶端。  
  
## <a name="see-also"></a>另請參閱  
 [大型 CLR 使用者定義型別](~/relational-databases/native-client/features/large-clr-user-defined-types.md)  
  
  

