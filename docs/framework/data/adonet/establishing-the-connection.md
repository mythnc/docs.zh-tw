---
title: "建立連接 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3af512f3-87d9-4005-9e2f-abb1060ff43f
caps.latest.revision: 7
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# 建立連接
若要連接至 Microsoft SQL Server，請使用 .NET Framework Data Provider for SQL Server 的 <xref:System.Data.SqlClient.SqlConnection> 物件。  若要連接至 OLE DB 資料來源，請使用 .NET Framework Data Provider for OLE DB 的 <xref:System.Data.OleDb.OleDbConnection> 物件。  若要連接至 ODBC 資料來源，請使用 ODBC 的 .NET Framework 資料提供者的 <xref:System.Data.Odbc.OdbcConnection> 物件。  若要連接至 Oracle 資料來源，請使用 Oracle 的 .NET Framework 資料提供者的 <xref:System.Data.OracleClient.OracleConnection> 物件。  若要安全地儲存及擷取連接字串，請參閱[保護連接資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)。  
  
## 關閉連接  
 建議您在使用完連接後一律關閉該連接，以便將連接傳回集區。  即使有未處理的例外狀況，Visual Basic 或 C\# 中的 `Using` 區塊也會在程式碼結束該區塊時自動處理連接。  如需詳細資訊，請參閱 [Using 陳述式](../Topic/using%20Statement%20\(C%23%20Reference\).md) 和 [Using Statement](../Topic/Using%20Statement%20\(Visual%20Basic\).md)。  
  
 您也可針對使用的提供者，使用連接物件的 `Close` 或 `Dispose` 方法。  可能不會將未明確關閉的連接加入或傳回集區。  例如，已離開範圍但尚未明確關閉的連接僅會在已達到最大集區大小，且連接仍然有效時，才會回到連接集區。  如需詳細資訊，請參閱[OLE DB、ODBC 和 Oracle 連接共用](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)。  
  
> [!NOTE]
>  請不要在您類別之 `Finalize` 方法中的 **Connection**、**DataReader** 或任何其他 Managed 物件上呼叫 `Close` 或 `Dispose`。  在完成項中，只需釋放類別直接擁有的 Unmanaged 資源。  如果類別未擁有任何 Unmanaged 資源，請不要在類別定義中包含 `Finalize` 方法。  如需詳細資訊，請參閱[Garbage Collection](../../../../docs/standard/garbage-collection/index.md)。  
  
> [!NOTE]
>  從連接集區中擷取連接或將連接傳回連接集區時，系統不會在伺服器上引發登入和登出事件，因為當連接傳回連接集區時，連接實際上並未關閉。  如需詳細資訊，請參閱[SQL Server 連接共用 \(ADO.NET\)](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md)。  
  
## 連接至 SQL Server  
 SQL Server 的 .NET Framework 資料提供者支援與 OLE DB \(ADO\) 連接字串格式類似的連接字串格式。  如需有效的字串格式名稱及值，請參閱 <xref:System.Data.SqlClient.SqlConnection> 物件的 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> 屬性。  您也可以使用 <xref:System.Data.SqlClient.SqlConnectionStringBuilder> 類別在執行階段建立語法有效的連接字串。  如需詳細資訊，請參閱[連接字串產生器](../../../../docs/framework/data/adonet/connection-string-builders.md)。  
  
 下列程式碼範例示範如何建立及開啟與 SQL Server 資料庫的連接。  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New SqlConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (SqlConnection connection = new SqlConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
### 整合安全性與 ASP.NET  
 SQL Server 整合安全性 \(也稱為信任連接\) 可在連接至 SQL Server 時，協助提供保護，因為它不會在連接字串中公開使用者 ID 及密碼，因此建議在驗證連接時使用。  整合安全性會使用執行中處理序的目前安全性識別或語彙基元。  對於桌面應用程式，這通常是目前已登入使用者的識別。  
  
 ASP.NET 應用程式的安全性識別可設為數個不同的選項之一。  若要更了解 ASP.NET 應用程式在連接至 SQL Server 時使用的安全性識別，請參閱 [ASP.NET Impersonation](../Topic/ASP.NET%20Impersonation.md)、[ASP.NET Authentication](../Topic/ASP.NET%20Authentication.md) 及 [How to: Access SQL Server Using Windows Integrated Security](../Topic/How%20to:%20Access%20SQL%20Server%20Using%20Windows%20Integrated%20Security.md)。  
  
## 連接至 OLE DB 資料來源  
 .NET Framework Data Provider for OLE DB 會使用 **OleDbConnection** 物件，與使用 OLE DB \(透過 SQLOLEDB，即 OLE DB Provider for SQL Server\) 公開的資料來源連接。  
  
 對於 OLE DB 的 .NET Framework 資料提供者，連接字串格式與 ADO 中使用的連接字串格式相同，但下列情況例外：  
  
-   需要 **Provider** 關鍵字。  
  
-   不支援 **URL**、**Remote Provider** 及 **Remote Server** 關鍵字。  
  
 如需 OLE DB 連接字串的詳細資訊，請參閱 <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> 主題。  您也可以使用 <xref:System.Data.OleDb.OleDbConnectionStringBuilder> 在執行階段建立連接字串。  
  
> [!NOTE]
>  **OleDbConnection** 物件不支援設定或擷取 OLE DB 提供者特定的動態屬性。  僅支援 OLE DB 提供者之連接字串中可傳遞的屬性。  
  
 下列程式碼範例說明如何建立及開啟與 OLE DB 資料來源的連接。  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OleDbConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OleDbConnection connection =   
  new OleDbConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
## 不使用通用資料連結檔  
 您可以在「通用資料連結」\(UDL\) 檔中提供 **OleDbConnection** 的連接資訊；但請不要這麼做。  UDL 檔並未加密，並且會以純文字的格式公開連接字串資訊。  因為對您的應用程式而言，UDL 檔是外部的檔案型資源，所以您無法使用 .NET Framework 來保護該檔案。  
  
## 連接至 ODBC 資料來源  
 ODBC 的 .NET Framework 資料提供者會使用 **OdbcConnection** 物件，提供與使用 ODBC 公開之資料來源的連接。  
  
 對於 ODBC 的 .NET Framework 資料提供者，會將連接字串格式設計為儘可能與 ODBC 連接字串格式相符。  您也可以提供 ODBC 資料來源名稱 \(DSN\)。  如需 **OdbcConnection** 的詳細資訊，請參閱 [OdbcConnection 類別](frlrfSystemDataOdbcOdbcConnectionClassTopic)。  
  
 下列程式碼範例說明如何建立及開啟與 ODBC 資料來源的連接。  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OdbcConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OdbcConnection connection =   
  new OdbcConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
## 連接至 Oracle 資料來源  
 Oracle 的 .NET Framework 資料提供者會使用 **OracleConnection** 物件，提供與 Oracle 資料來源的連接。  
  
 對於 Oracle 的 .NET Framework 資料提供者，會將連接字串格式設計為儘可能與 Oracle OLE DB 提供者 \(MSDAORA\) 連接字串格式相符。  如需 **OracleConnection** 的詳細資訊，請參閱 [OracleConnection 類別](frlrfSystemDataOracleClientOracleConnectionClassTopic)。  
  
 下列程式碼範例說明如何建立及開啟與 Oracle 資料來源的連接。  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OracleConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OracleConnection connection =   
  new OracleConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
OracleConnection nwindConn = new OracleConnection("Data Source=MyOracleServer;Integrated Security=yes;");  
nwindConn.Open();  
```  
  
## 請參閱  
 [連接資料來源](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)   
 [連接字串](../../../../docs/framework/data/adonet/connection-strings.md)   
 [OLE DB、ODBC 和 Oracle 連接共用](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)