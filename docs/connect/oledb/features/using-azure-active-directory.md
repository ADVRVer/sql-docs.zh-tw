---
title: 使用 Azure Active Directory |SQL Server 的 Microsoft Docs
ms.custom: ''
ms.date: 10/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: bazizi
ms.author: v-beaziz
ms.openlocfilehash: b459877be731da11b33d13772bbf186ecf72198c
ms.sourcegitcommit: 4c75b49599018124f05f91c1df3271d473827e4d
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72381854"
---
# <a name="using-azure-active-directory"></a>使用 Azure Active Directory
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

## <a name="purpose"></a>目的

從版本18.2.1 版開始，適用于 SQL Server 的 Microsoft OLE DB 驅動程式可讓 OLE DB 應用程式使用同盟身分識別連接到 Azure SQL Database 的實例。 新的驗證方法包括：
- Azure Active Directory 登入識別碼和密碼
- Azure Active Directory 存取權杖
- Azure Active Directory 整合式驗證
- SQL 登入識別碼和密碼

18.3 版新增了下列驗證方法的支援：
- Azure Active Directory 互動式驗證
- Azure Active Directory MSI 驗證

> [!NOTE]
> **不**支援在 `DataTypeCompatibility` （或其對應的屬性）設定為 `80` 的情況下使用下列驗證模式：
> - 使用登入識別碼和密碼 Azure Active Directory 驗證
> - 使用存取權杖 Azure Active Directory 驗證
> - Azure Active Directory 整合式驗證
> - Azure Active Directory 互動式驗證
> - Azure Active Directory MSI 驗證

## <a name="connection-string-keywords-and-properties"></a>連接字串關鍵字和屬性
已引進下列連接字串關鍵字來支援 Azure Active Directory 驗證：

|連接字串關鍵字|連線屬性|Description|
|---               |---                |---        |
|存取權杖|SSPROP_AUTH_ACCESS_TOKEN|指定要驗證 Azure Active Directory 的存取權杖。 |
|驗證|SSPROP_AUTH_MODE|指定要使用的驗證方法。|

如需新關鍵字/屬性的詳細資訊，請參閱下列頁面：
- [利用 OLE DB Driver for SQL Server 使用連接字串關鍵字](../applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)
- [初始化和授權屬性](../ole-db-data-source-objects/initialization-and-authorization-properties.md)

## <a name="encryption-and-certificate-validation"></a>加密和憑證驗證
本節討論加密和憑證驗證行為的變更。 這些變更只有在使用新的驗證或存取權杖連接字串關鍵字（或其對應的屬性）時**才**有效。

### <a name="encryption"></a>加密
為了提升安全性，當使用新的連線屬性/關鍵字時，驅動程式會將預設的加密值設定為 `yes` 來覆寫。 覆寫會發生在資料來源物件初始化時間。 如果在以任何方式初始化之前設定加密，則會遵守且不會覆寫值。

> [!NOTE]   
> 在 ADO 應用程式中，以及在透過 `IDataInitialize::GetDataSource` 取得 `IDBInitialize` 介面的應用程式中，執行介面的核心元件會將加密明確設定為其 `no` 的預設值。 因此，新的驗證屬性/關鍵字會遵守此設定，而且**不**會覆寫加密值。 因此，**建議您**明確地將這些應用程式設定 `Use Encryption for Data=true` 以覆寫預設值。

### <a name="certificate-validation"></a>憑證驗證
為了提升安全性，新的連接屬性/關鍵字會採用與**用戶端加密設定無關**的 `TrustServerCertificate` 設定（及其對應的連接字串關鍵字/屬性）。 因此，預設會驗證伺服器憑證。

> [!NOTE]   
> 憑證驗證也可以透過 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SNI18.0\GeneralFlags\Flag2` 登錄專案的 [`Value`] 欄位來控制。 有效值為 `0` 或 `1`。 OLE DB 驅動程式會在登錄和連接屬性/關鍵字設定之間選擇最安全的選項。 也就是說，只要至少其中一個登錄/連線設定啟用伺服器憑證驗證，驅動程式就會驗證伺服器憑證。

## <a name="gui-additions"></a>新增 GUI
驅動程式圖形化使用者介面已經過增強，以允許 Azure Active Directory 驗證。 如需詳細資訊，請參閱：
- [SQL Server 登入對話方塊](../help-topics/sql-server-login-dialog.md)
- [通用資料連結 (UDL) 設定](../help-topics/data-link-pages.md)

## <a name="example-connection-strings"></a>範例連接字串
本節顯示新的和現有連接字串關鍵字的範例，以搭配 `IDataInitialize::GetDataSource` 和 `DBPROP_INIT_PROVIDERSTRING` 屬性使用。

### <a name="sql-authentication"></a>SQL 驗證
- 使用 `IDataInitialize::GetDataSource`：
    - 新增：
        > Provider = 內含 MSOLEDBSQL.H; 資料來源 = [伺服器]; 初始目錄 = [資料庫];**Authentication = SqlPassword**;使用者識別碼 = [username];Password = [password];針對資料使用加密 = true
    - 已淘汰：
        > Provider = 內含 MSOLEDBSQL.H; 資料來源 = [伺服器]; 初始目錄 = [資料庫];使用者識別碼 = [username];Password = [password];針對資料使用加密 = true
- 使用 `DBPROP_INIT_PROVIDERSTRING`：
    - 新增：
        > Server=[server];Database=[database];**Authentication=SqlPassword**;UID=[username];PWD=[password];Encrypt=yes
    - 已淘汰：
        > Server=[server];Database=[database];UID=[username];PWD=[password];Encrypt=yes

### <a name="integrated-windows-authentication-using-security-support-provider-interface-sspi"></a>使用安全性支援提供者介面（SSPI）的整合式 Windows 驗證

- 使用 `IDataInitialize::GetDataSource`：
    - 新增：
        > Provider = 內含 MSOLEDBSQL.H; 資料來源 = [伺服器]; 初始目錄 = [資料庫];**Authentication = ActiveDirectoryIntegrated**;針對資料使用加密 = true
    - 已淘汰：
        > Provider = 內含 MSOLEDBSQL.H; 資料來源 = [伺服器]; 初始目錄 = [資料庫];**整合式安全性 = SSPI**;針對資料使用加密 = true
- 使用 `DBPROP_INIT_PROVIDERSTRING`：
    - 新增：
        > Server=[server];Database=[database];**Authentication=ActiveDirectoryIntegrated**;Encrypt=yes
    - 已淘汰：
        > Server=[server];Database=[database];**Trusted_Connection=yes**;Encrypt=yes

### <a name="azure-active-directory-username-and-password-authentication"></a>Azure Active Directory 使用者名稱和密碼驗證

- 使用 `IDataInitialize::GetDataSource`：
    > Provider = 內含 MSOLEDBSQL.H; 資料來源 = [伺服器]; 初始目錄 = [資料庫];**Authentication = ActiveDirectoryPassword**;使用者識別碼 = [username];Password = [password];針對資料使用加密 = true
- 使用 `DBPROP_INIT_PROVIDERSTRING`：
    > Server=[server];Database=[database];**Authentication=ActiveDirectoryPassword**;UID=[username];PWD=[password];Encrypt=yes

### <a name="azure-active-directory-integrated-authentication"></a>Azure Active Directory 整合式驗證

- 使用 `IDataInitialize::GetDataSource`：
    > Provider = 內含 MSOLEDBSQL.H; 資料來源 = [伺服器]; 初始目錄 = [資料庫];**Authentication = ActiveDirectoryIntegrated**;針對資料使用加密 = true
- 使用 `DBPROP_INIT_PROVIDERSTRING`：
    > Server=[server];Database=[database];**Authentication=ActiveDirectoryIntegrated**;Encrypt=yes

### <a name="azure-active-directory-authentication-using-an-access-token"></a>使用存取權杖 Azure Active Directory 驗證

- 使用 `IDataInitialize::GetDataSource`：
    > Provider = 內含 MSOLEDBSQL.H; 資料來源 = [伺服器]; 初始目錄 = [資料庫];**存取權杖 = [存取權杖]** ;針對資料使用加密 = true
- 使用 `DBPROP_INIT_PROVIDERSTRING`：
    > 不支援透過 `DBPROP_INIT_PROVIDERSTRING` 提供存取權杖

### <a name="azure-active-directory-interactive-authentication"></a>Azure Active Directory 互動式驗證

- 使用 `IDataInitialize::GetDataSource`：
    > Provider = 內含 MSOLEDBSQL.H; 資料來源 = [伺服器]; 初始目錄 = [資料庫];**Authentication = ActiveDirectoryInteractive**;使用者識別碼 = [username];針對資料使用加密 = true
- 使用 `DBPROP_INIT_PROVIDERSTRING`：
    > Server = [server];D 資料庫取得 = [Database];**Authentication = ActiveDirectoryInteractive**;UID = [username];Encrypt = 是

### <a name="azure-active-directory-msi-authentication"></a>Azure Active Directory MSI 驗證

- 使用 `IDataInitialize::GetDataSource`：
    - 使用者指派的受控識別：
        > Provider = 內含 MSOLEDBSQL.H; 資料來源 = [伺服器]; 初始目錄 = [資料庫];**Authentication = ActiveDirectoryMSI**;使用者識別碼 = [物件識別碼];針對資料使用加密 = true
    - 系統指派的受控識別：
        > Provider = 內含 MSOLEDBSQL.H; 資料來源 = [伺服器]; 初始目錄 = [資料庫];**Authentication = ActiveDirectoryMSI**;針對資料使用加密 = true
- 使用 `DBPROP_INIT_PROVIDERSTRING`：
    - 使用者指派的受控識別：
        > Server = [server];D 資料庫取得 = [Database];**Authentication = ActiveDirectoryMSI**;UID = [物件識別碼];Encrypt = 是
    - 系統指派的受控識別：
        > Server = [server];D 資料庫取得 = [Database];**Authentication = ActiveDirectoryMSI**;Encrypt = 是

## <a name="code-samples"></a>程式碼範例

下列範例顯示使用連接關鍵字連接到 Azure Active Directory 所需的程式碼。 

### <a name="access-token"></a>存取權杖
```cpp
#include <string>
#include <iostream>
#include <msdasc.h>

int main()
{
    wchar_t azureServer[] = L"server";
    wchar_t azureDatabase[] = L"mydatabase";
    wchar_t accessToken[] = L"eyJ0eXAiOi...";
    IDBInitialize *pIDBInitialize = nullptr;
    IDataInitialize* pIDataInitialize = nullptr;
    HRESULT hr = S_OK;

    CoInitialize(nullptr);

    // Construct the connection string.
    std::wstring connString = L"Provider=MSOLEDBSQL;Data Source=" + std::wstring(azureServer) + L";Initial Catalog=" + 
                              std::wstring(azureDatabase) + L";Access Token=" + accessToken + L";Use Encryption for Data=true;";
    hr = CoCreateInstance(CLSID_MSDAINITIALIZE, nullptr, CLSCTX_INPROC_SERVER, 
                          IID_IDataInitialize, reinterpret_cast<LPVOID*>(&pIDataInitialize));
    if (FAILED(hr))
    {
        std::cout << "Failed to create an IDataInitialize instance." << std::endl;
        goto Cleanup;
    }
    hr = pIDataInitialize->GetDataSource(nullptr, CLSCTX_INPROC_SERVER, connString.c_str(), 
                                         IID_IDBInitialize, reinterpret_cast<IUnknown**>(&pIDBInitialize));
    if (FAILED(hr))
    {
        std::cout << "Failed to get data source object." << std::endl;
        goto Cleanup;
    }
    hr = pIDBInitialize->Initialize();
    if (FAILED(hr))
    {
        std::cout << "Failed to establish connection." << std::endl;
        goto Cleanup;
    }

Cleanup:
    if (pIDBInitialize)
    {
        pIDBInitialize->Uninitialize();
        pIDBInitialize->Release();
    }
    if (pIDataInitialize)
    {
        pIDataInitialize->Release();
    }

    CoUninitialize();
}
```
### <a name="active-directory-integrated"></a>Active Directory 整合式
```cpp
#include <string>
#include <iostream>
#include <msdasc.h>

int main()
{
    wchar_t azureServer[] = L"server";
    wchar_t azureDatabase[] = L"mydatabase";
    IDBInitialize *pIDBInitialize = nullptr;
    IDataInitialize* pIDataInitialize = nullptr;
    HRESULT hr = S_OK;

    CoInitialize(nullptr);

    // Construct the connection string.
    std::wstring connString = L"Provider=MSOLEDBSQL;Data Source=" + std::wstring(azureServer) + L";Initial Catalog=" + 
                              std::wstring(azureDatabase) + L";Authentication=ActiveDirectoryIntegrated;Use Encryption for Data=true;";

    hr = CoCreateInstance(CLSID_MSDAINITIALIZE, nullptr, CLSCTX_INPROC_SERVER, 
                          IID_IDataInitialize, reinterpret_cast<LPVOID*>(&pIDataInitialize));
    if (FAILED(hr)) 
    {
        std::cout << "Failed to create an IDataInitialize instance." << std::endl;
        goto Cleanup;
    }
    hr = pIDataInitialize->GetDataSource(nullptr, CLSCTX_INPROC_SERVER, connString.c_str(), 
                                         IID_IDBInitialize, reinterpret_cast<IUnknown**>(&pIDBInitialize));
    if (FAILED(hr))
    {
        std::cout << "Failed to get data source object." << std::endl;
        goto Cleanup;
    }
    hr = pIDBInitialize->Initialize();
    if (FAILED(hr))
    {
        std::cout << "Failed to establish connection." << std::endl;
        goto Cleanup;
    }

Cleanup:
    if (pIDBInitialize)
    {
        pIDBInitialize->Uninitialize();
        pIDBInitialize->Release();
    }
    if (pIDataInitialize)
    {
        pIDataInitialize->Release();
    }

    CoUninitialize();
}
```

## <a name="next-steps"></a>後續步驟
- [使用 OAuth 2.0 程式碼授與流程，授權存取 Azure Active Directory web 應用程式](https://go.microsoft.com/fwlink/?linkid=2072672)。

- 了解 [Azure Active Directory 驗證](https://go.microsoft.com/fwlink/?linkid=2073783) (到 SQL Server)。

- 使用 OLE DB 驅動程式支援的[連接字串關鍵字](../applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)來設定驅動程式連接。
