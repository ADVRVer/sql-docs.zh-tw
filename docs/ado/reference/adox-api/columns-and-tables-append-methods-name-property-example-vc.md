---
title: 資料行和資料表附加方法中，屬性的範例 （VC + +） |Microsoft 文件
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Name property [ADOX], VC++ example
- Append method [ADOX], VC++ example
ms.assetid: 2b6dfef9-bcdf-483d-a164-2fa3ec81a43f
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d13c67db7452966f434e63646ba785141205ef51
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="columns-and-tables-append-methods-name-property-example-vc"></a>資料行和資料表附加方法名稱屬性的範例 （VC + +）
下列程式碼會示範如何建立新的資料表。  
  
```  
// BeginCreateTableCpp.cpp  
// compile with: /EHsc  
#import "msadox.dll" no_namespace  
  
#include "iostream"  
using namespace std;  
  
// Function declarations  
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};  
  
int main() {  
   if ( FAILED(::CoInitialize(NULL) ) )  
      return -1;  
  
   HRESULT hr = S_OK;  
  
   // Define ADOX object pointers, initialize pointers.  These are in ADOX namespace.  
   _CatalogPtr m_pCatalog = NULL;  
   _TablePtr m_pTable = NULL;  
  
   try {  
      TESTHR(hr = m_pCatalog.CreateInstance(__uuidof(Catalog)));  
  
      // Open the catalog  
      m_pCatalog->PutActiveConnection("Provider='Microsoft.JET.OLEDB.4.0';data source='c:\\Northwind.mdb';");  
  
      TESTHR(hr = m_pTable.CreateInstance(__uuidof(Table)));  
      m_pTable->PutName("MyTable");  
      m_pTable->Columns->Append("Column1",adInteger,0);  
      m_pTable->Columns->Append("Column2",adInteger,0);  
      m_pTable->Columns->Append("Column3",adVarWChar,50);  
      m_pCatalog->Tables->Append(_variant_t((IDispatch *)m_pTable));  
      printf("Table 'MyTable' is added.\n");  
  
      // Delete the table as this is a demonstration.  
      m_pCatalog->Tables->Delete("MyTable");  
      printf("Table 'MyTable' is deleted.\n");  
   }  
  
   catch(_com_error &e) {  
      // Notify the user of errors if any.  
      _bstr_t bstrSource(e.Source());  
      _bstr_t bstrDescription(e.Description());  
  
      printf("\n\tSource :  %s \n\tdescription : %s \n ", (LPCSTR)bstrSource, (LPCSTR)bstrDescription);  
   }  
  
   catch(...) {  
      cout << "Error occured in include files...."<< endl;  
   }  
  
   ::CoUninitialize();  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [Append 方法 （ADOX 資料行）](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append 方法 （ADOX 資料表）](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Name 屬性 (ADOX)](../../../ado/reference/adox-api/name-property-adox.md)
