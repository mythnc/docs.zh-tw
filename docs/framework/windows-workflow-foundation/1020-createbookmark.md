---
title: "1020 - CreateBookmark | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4bee948d-816f-4803-85cc-3883b5e23d10
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 1020 - CreateBookmark
## 屬性  
  
|||  
|-|-|  
|ID|1020|  
|關鍵字|WFRuntime|  
|層級|詳細資訊|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 描述  
 表示已經為活動建立書籤。  
  
## 訊息  
 已建立活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的書籤。BookmarkName：%4、BookmarkScope：%5。  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|活動|xs:string|活動的型別名稱。|  
|DisplayName|xs:string|活動的顯示名稱。|  
|InstanceId|xs:string|活動的執行個體 ID。|  
|BookmarkName|xs:string|書籤的名稱。|  
|BookmarkScope|xs:string|書籤的範圍。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|