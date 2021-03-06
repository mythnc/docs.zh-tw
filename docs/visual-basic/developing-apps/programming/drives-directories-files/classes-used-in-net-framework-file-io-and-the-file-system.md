---
title: "用於 .NET Framework 檔案 I/O 和檔案系統的類別 (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- file I/O classes
ms.assetid: 4a5ca924-eea8-4a95-a5f0-6ac10de276a3
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: ca1ecff264734c16369c9a7d28fbb388bb2f1ccc
ms.contentlocale: zh-tw
ms.lasthandoff: 05/22/2017

---
# <a name="classes-used-in-net-framework-file-io-and-the-file-system-visual-basic"></a>用於 .NET Framework 檔案 I/O 和檔案系統的類別 (Visual Basic)
下列各表列出 .NET Framework 檔案 I/O 的常用類別、分類為檔案 I/O 類別的檔案、用於建立資料流的類別，以及用來讀取和寫入至資料流的類別。  
  
 若要輸入 [!INCLUDE[dnprdnlong](../../../../csharp/programming-guide/events/includes/dnprdnlong_md.md)] 文件，並尋找更完整的清單，請參閱[類別庫概觀](https://msdn.microsoft.com/library/hfa3fa08)。  
  
## <a name="basic-io-classes-for-files-drives-and-directories"></a>檔案、磁碟機和目錄的基本 I/O 類別  
 下表列出並描述用於檔案 I/O 的主要類別。  
  
|類別|說明|  
|-----------|-----------------|  
|<xref:System.IO.Directory?displayProperty=fullName>|提供建立、移動和列舉目錄和子目錄的靜態方法。|  
|<xref:System.IO.DirectoryInfo?displayProperty=fullName>|提供建立、移動和列舉目錄和子目錄的執行個體方法。|  
|<xref:System.IO.DriveInfo?displayProperty=fullName>|提供建立、移動和列舉磁碟機的執行個體方法。|  
|<xref:System.IO.File?displayProperty=fullName>|提供建立、複製、刪除、移動和開啟檔案的靜態方法，並協助建立 `FileStream`。|  
|<xref:System.IO.FileAccess?displayProperty=fullName>|定義檔案讀取、寫入或讀取/寫入存取的常數。|  
|<xref:System.IO.FileAttributes?displayProperty=fullName>|提供檔案和目錄的屬性，例如 `Archive`、`Hidden` 和 `ReadOnly`。|  
|<xref:System.IO.FileInfo?displayProperty=fullName>|提供建立、複製、刪除、移動和開啟檔案的靜態方法，並協助建立 `FileStream`。|  
|<xref:System.IO.FileMode?displayProperty=fullName>|控制檔案的開啟方式。 這個參數於針對 `FileStream` 和 `IsolatedStorageFileStream`，以及針對 <xref:System.IO.File> 和 <xref:System.IO.FileInfo> 之 `Open` 方法的許多建構函式中指定。|  
|<xref:System.IO.FileShare?displayProperty=fullName>|定義常數，用來控制其他檔案資料流對相同檔案可以擁有的存取類型。|  
|<xref:System.IO.Path?displayProperty=fullName>|提供處理目錄字串的方法和屬性。|  
|<xref:System.Security.Permissions.FileIOPermission?displayProperty=fullName>|透過定義 <xref:System.Security.Permissions.FileIOPermissionAttribute.Read%2A>、<xref:System.Security.Permissions.FileIOPermissionAttribute.Write%2A>、<xref:System.Security.Permissions.FileIOPermissionAttribute.Append%2A>，以及 <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> 權限，來控制檔案和資料夾的存取。|  
  
## <a name="classes-used-to-create-streams"></a>用來建立資料流的類別  
 下表列出並描述用來建立資料流的主要類別。  
  
|類別|說明|  
|-----------|-----------------|  
|<xref:System.IO.BufferedStream?displayProperty=fullName>|新增另一個資料流上讀取和寫入作業的緩衝層。|  
|<xref:System.IO.FileStream?displayProperty=fullName>|透過類別的 <xref:System.IO.FileStream.Seek%2A> 方法，支援對檔案的隨機存取。 <xref:System.IO.FileStream> 預設會以同步的方式開啟檔案，但也支援非同步作業。|  
|<xref:System.IO.MemoryStream?displayProperty=fullName>|建立支援的存放區為記憶體而非檔案的資料流。|  
|<xref:System.Net.Sockets.NetworkStream?displayProperty=fullName>|提供基礎資料流以進行網路存取。|  
|<xref:System.Security.Cryptography.CryptoStream?displayProperty=fullName>|定義連結資料流與密碼編譯轉換的資料流。|  
  
## <a name="classes-used-to-read-from-and-write-to-streams"></a>用來讀取和寫入至資料流的類別  
 下表顯示用於讀取和寫入至具有資料流之檔案的特定類別。  
  
|**類別**|**說明**|  
|---------------|---------------------|  
|<xref:System.IO.BinaryReader?displayProperty=fullName>|從 <xref:System.IO.FileStream> 讀取編碼字串和基本資料類型。|  
|<xref:System.IO.BinaryWriter?displayProperty=fullName>|將編碼字串和基本資料類型寫入 <xref:System.IO.FileStream>。|  
|<xref:System.IO.StreamReader?displayProperty=fullName>|從 <xref:System.IO.FileStream> 讀取字元，使用 <xref:System.IO.StreamReader.CurrentEncoding%2A> 來在字元與位元組之間進行轉換。 <xref:System.IO.StreamReader> 具有會根據 <xref:System.IO.StreamReader.CurrentEncoding%2A> 特定的前序 (例如位元組順序標記) 是否存在，來嘗試針對特定資料流確認正確 <xref:System.IO.StreamReader.CurrentEncoding%2A> 的建構函式。|  
|<xref:System.IO.StreamWriter?displayProperty=fullName>|將字元寫入 `FileStream`，使用 <xref:System.IO.StreamWriter.Encoding%2A> 將字元轉換成位元組。|  
|<xref:System.IO.StringReader?displayProperty=fullName>|從 `String` 讀取字元。 輸出可以是任何編碼的資料流或 `String`。|  
|<xref:System.IO.StringWriter?displayProperty=fullName>|將字元寫入至 `String`。 輸出可以是任何編碼的資料流或 `String`。|  
  
## <a name="see-also"></a>另請參閱  
 [撰寫資料流](https://msdn.microsoft.com/library/e4y2dch9)   
 [檔案和資料流 I/O](https://msdn.microsoft.com/library/k3352a4t)   
 [非同步檔案 I/O](https://msdn.microsoft.com/library/kztecsys)   
 [.NET Framework 檔案 I/O 和檔案系統基本概念 (Visual Basic)](../../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)
