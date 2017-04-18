---
title: "COM+ 服務模型組態工具 (ComSvcConfig.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "WCF, COM+ 整合"
  - "Windows Communication Foundation, COM+ 整合"
ms.assetid: 7717c6c2-85fc-418b-a8ed-bad8e61cec5c
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# COM+ 服務模型組態工具 (ComSvcConfig.exe)
COM\+ 服務模型組態命令列工具 \(ComSvcConfig.exe\) 可讓您設定要公開為 Web 服務的 COM\+ 介面。  
  
## 語法  
  
```  
  
ComSvcConfig.exe /install | /uninstall | /list [/application:<ApplicationID | ApplicationName>] [/contract:<ClassID | ProgID | *,InterfaceID | InterfaceName | *>] [/hosting:<complus | was>] [/webSite:<WebsiteName>] [/webDirectory:<WebDirectoryName>] [/mex] [/id] [/nologo] [/verbose] [/help] [/partial]  
```  
  
## 備註  
  
> [!NOTE]
>  您必須是本機電腦的系統管理員，才能使用 ComSvcConfig.exe。  
  
 您可以在下列位置找到這個工具  
  
 %SystemRoot%\\Microsoft.Net\\Framework\\v3.0\\Windows Communication Foundation\\  
  
 如需 ComSvcConfig.exe 的詳細資訊，請參閱 [HOW TO：使用 COM\+ 服務模型組態工具](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)。  
  
 下表說明可以和 ComSvcConfig.exe 搭配使用的模式。  
  
|選項|描述|  
|--------|--------|  
|`install`|安裝服務模型整合的 COM\+ 介面組態。<br /><br /> 簡短形式：`/i`。|  
|`uninstall`|解除安裝服務模型整合的 COM\+ 介面組態。<br /><br /> 簡短形式：`/u`。|  
|`list`|列出 COM\+ 應用程式和元件的相關資訊，這些應用程式和元件具有針對服務模型整合設定的介面。<br /><br /> 簡短形式：`/l`。|  
  
 下表說明可以和 ComSvcConfig.exe 搭配使用的旗標。  
  
|選項|說明|  
|--------|--------|  
|`/application:<` *ApplicationID*  `&#124;`  *ApplicationName* `>`|指定要設定的 COM\+ 應用程式。<br /><br /> 簡短形式：`/a`。|  
|`/contract:<` *ClassID*  `&#124;`  *ProgID*  `&#124; *,` *InterfaceID*  `&#124;`  *InterfaceName*  `&#124; *` `>`|指定要設定為服務合約的 COM\+ 元件和介面。<br /><br /> 簡短形式：`/c`。<br /><br /> 雖然在指定元件和介面名稱時可以使用萬用字元 \(\*\)，但是這麼做可能會公開您不想公開的介面，因此建議您不要使用萬用字元。|  
|`/hosting:<` *complus*  `&#124;`  *was* `>`|指定使用 COM\+ 主控模式或 Web 主控模式。<br /><br /> 簡短形式：`/h`。<br /><br /> 使用 COM\+ 主控模式必須明確啟動 COM\+ 應用程式。使用 Web 主控模式可讓 COM\+ 應用程式視需要自動啟動。如果 COM\+ 應用程式是程式庫應用程式，它會在網際網路資訊服務 \(IIS\) 處理序中執行。如果 COM\+ 應用程式是伺服器應用程式，它會在 Dllhost.exe 處理序中執行。|  
|`/webSite:<` *WebsiteName* `>`|指定使用 Web 主控模式時用於主控的網站 \(請參閱 `/hosting` 旗標\)。<br /><br /> 簡短形式：`/w`。<br /><br /> 如果未指定網站，則會使用預設網站。|  
|`/webDirectory:<` *WebDirectoryName* `>`|指定使用 Web 主控模式時用於主控的虛擬目錄 \(請參閱 `/hosting` 旗標\)。<br /><br /> 簡短形式：`/d`。|  
|`/mex`|將 Metadata Exchange \(MEX\) 服務端點新增至預設服務組態，以支援要從服務擷取合約定義的用戶端。<br /><br /> 簡短形式：`/x`。|  
|`/id`|以 ID 的方式顯示應用程式、元件和介面資訊。<br /><br /> 簡短形式：`/k`。|  
|`/nologo`|防止 ComSvcConfig.exe 顯示其標誌。<br /><br /> 簡短形式：`/n`。|  
|`/verbose`|除了發生的任何錯誤之外，也輸出所有的警告或資訊文字。<br /><br /> 簡短形式：`/v`。|  
|`/help`|顯示使用方式訊息。<br /><br /> 簡短形式：`/?`。|  
|`/partial`|當指定的介面包含一或多個可公開的方法簽章時，產生服務組態。在服務初始化階段，相容的方法會顯示為服務合約上的作業，不相容的方法會被忽略，且不會出現在服務合約中。<br /><br /> 如果缺少這個旗標，當指定的介面包含一或多個不相容的方法時，工具不會產生服務組態。|  
  
## 範例  
  
### 說明  
 下列範例說明使用 COM\+ 主控模式，將 `ItemOrders.IFinancial` 元件的 \(取自 OnlineStore COM\+ 應用程式\) `IFinances` 介面新增至公開為 Web 服務的介面組。除了發生的任何錯誤之外，也輸出所有的警告訊息。  
  
### 程式碼  
  
```  
ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
```  
  
### 說明  
 下列範例說明使用 Web 主控模式，將 `ItemInventory.Warehouse` 元件的 \(取自 OnlineWarehouse COM\+ 應用程式\) `IStockLevels` 介面新增至公開為 Web 服務的介面組。Web 服務是由 IIS 的 OnlineWarehouse 虛擬目錄進行 Web 主控。  
  
### 程式碼  
  
```  
ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse  
```  
  
### 說明  
 下列範例說明從公開為 Web 服務的介面組中移除 `ItemOrders.Financial` 元件的 \(取自 OnlineStore COM\+ 應用程式\) `IFinances` 介面。  
  
### 程式碼  
  
```  
ComSvcConfig.exe /uninstall /application:OnlineStore /interface:ItemOrders.Financial,IFinances /hosting:complus  
```  
  
### 說明  
 下列範例列出本機電腦上 OnlineStore COM\+ 應用程式目前公開的 COM\+ 主控介面，以及對應的位址與繫結詳細資訊。  
  
### 程式碼  
  
```  
ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
```  
  
## 請參閱  
 [HOW TO：使用 COM\+ 服務模型組態工具](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)