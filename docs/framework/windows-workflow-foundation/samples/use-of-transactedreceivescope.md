---
title: "TransactedReceiveScope 的使用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d455f1dc-bfc5-43d6-8ae9-bc3b3a3ea08a
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# TransactedReceiveScope 的使用
這個範例示範如何將交易從用戶端流送至伺服器，方式是使用 <xref:System.Activities.Statements.TransactionScope> 在用戶端建立新交易，以及在伺服器上使用 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 接收有流動交易之訊息並設定交易存留期範圍。這個範例包含兩個專案，可扮演用戶端和伺服器的角色。  
  
## 用戶端應用程式  
 用戶端應用程式會執行一個工作流程，此工作流程會列印分散式交易識別碼、傳送訊息給伺服器、讓交易流動、接收回應、再次列印分散式交易識別碼，然後完成。當分散式交易識別碼最初列印時，它是空的 GUID 因為交易仍然在本機。  
  
## 伺服器應用程式  
 伺服器專案很類似，但是工作流程會在 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 中裝載，因為它必須接聽端點，取得來自用戶端的訊息。此工作流程會集中在 <xref:System.ServiceModel.Activities.TransactedReceiveScope>，它會接收來自用戶端的流動交易、列印已傳送的訊息、列印分散式交易識別碼，然後回覆給用戶端。分散式交易識別碼現在不是空的 GUID，而且如果可感知交易的活動已加入至 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 的主體，它會在流動交易之下執行。  
  
#### 若要執行範例  
  
1.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 TransactedReceiveScope.sln 方案。  
  
2.  若要建置方案，請按 CTRL\+SHIFT\+B 或選取 \[**建置**\] 功能表中的 \[**建置方案**\]。  
  
3.  成功建置後，以滑鼠右鍵按一下方案，並選取 \[**設定啟始專案**\]。從對話方塊選取 \[**多個啟始專案**\]，並確認兩個專案的動作都是 \[**開始**\]。  
  
4.  按 F5 或選取 \[**偵錯**\] 功能表中的 \[**開始偵錯**\]。或者，您可以按 CTRL\+F5 或選取 \[**偵錯**\] 功能表中的 \[**啟動但不偵錯**\]，執行但不偵錯。  
  
    > [!NOTE]
    >  啟動用戶端之前，伺服器必須在執行中。裝載服務的主控台視窗中會顯示輸出，表示已啟動服務的時間。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\TransactedReceiveScope`  
  
## 請參閱