---
title: "global.json 參考 | Microsoft Docs"
description: "global.json 參考"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 04/05/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 96102f96-d403-4385-8ef6-5d80e406eb0c
ms.translationtype: Human Translation
ms.sourcegitcommit: ec7028d43e7236056e5a53160f6017edadfec8c2
ms.openlocfilehash: a35938d355cb86205e9c822736862298508cf861
ms.contentlocale: zh-tw
ms.lasthandoff: 04/06/2017

---

# <a name="globaljson-reference"></a>global.json 參考

*global.json* 檔案允許透過 `sdk` 屬性使用選取的 .NET Core 工具版本。

.NET Core CLI 工具會在目前工作目錄 (這不一定與專案目錄相同) 或它的其中一個上層目錄中尋找此檔案。

## <a name="sdk"></a>SDK
類型：Object

指定 SDK 相關資訊。

### <a name="version"></a>version
類型：String

要使用的 SDK 版本。

例如：

```json
{
  "sdk": {
    "version": "1.0.0-preview2-003121"
  }
}
```

