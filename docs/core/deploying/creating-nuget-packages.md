---
title: "使用跨平台工具建立 NuGet 套件 | Microsoft Docs"
description: "使用跨平台工具建立 NuGet 封裝"
keywords: ".NET、.NET Core、NuGet"
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 2f0415c1-110b-433d-87c1-ae3d543a8844
ms.translationtype: Human Translation
ms.sourcegitcommit: 4437ce5d344cf06d30e31911def6287999fc6ffc
ms.openlocfilehash: 2b2081bce1725fb4a019881521604e4171b85028
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017

---

# 如何使用跨平台工具建立 NuGet 封裝
<a id="how-to-create-a-nuget-package-with-cross-platform-tools" class="xliff"></a>

> [!NOTE]
> 下圖顯示使用 Unix 的命令列範例。  此處顯示的 `dotnet pack` 命令，運作運作方式與在 Windows 上如出一轍。

在 .NET Core 1.0，程式庫預期以 NuGet 封裝方式散發。  實際上，所有的 .NET 標準程式庫都是以這種方式散發及取用。  `dotnet pack` 命令最容易完成此作業。

假設您剛寫完酷炫的新程式庫，希望透過 NuGet 散發。  您可以使用跨平台工具建立 NuGet 封裝，絲毫不差地完成此作業！  下例假設 **SuperAwesomeLibrary** 程式庫以 `netstandard1.0` 為目標。

如果您有可轉移的相依性，也就是相依於另一個專案的專案，您必須先使用 `dotnet restore` 命令確保還原整個解決方案的封裝，再建立 NuGet 封裝。  未完成這項操作，會導致 `dotnet pack` 命令無法正常運作。

在確定封裝還原後，您可以瀏覽至程式庫所在的目錄︰

`$ cd src/SuperAwesomeLibrary`

然後，只要從命令列發出單一命令︰
    
`$ dotnet pack`

您的 `/bin/Debug` 資料夾現在看起來像這樣︰

```
$ ls bin/Debug

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

請注意，這會產生能夠被偵錯的封裝。  如果想要建置具有版本二進位檔案的 NuGet 套件，您只需要新增 `-c`/`--configuration` 參數，並使用 `release` 作為引數。

`$ dotnet pack --configuration release`

您的 `/bin` 資料夾就會有 `release` 資料夾，包含二進位版的 NuGet 封裝︰

```
$ ls bin/release

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

現在您有發行 NuGet 封裝所需的檔案！

## 請勿混淆 `dotnet pack` 與 `dotnet publish`
<a id="dont-confuse-dotnet-pack-with-dotnet-publish" class="xliff"></a>

請務必注意，和 `dotnet publish` 命令一點關係都沒有。  `dotnet publish` 命令是要使用相同組合中的所有相依性來部署應用程式，不是用來產生要透過 NuGet 散發及使用的 NuGet 封裝。

