---
title: "&lt;peerAuthentication&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ad545e6f-f06e-4549-ac92-09d758d5c636
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# &lt;peerAuthentication&gt;
指定等節點使用之對等憑證的驗證設定。  
  
## 語法  
  
```  
  
<peerAuthentication  
      customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
      certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
      revocationMode="NoCheck/Online/Offline"  
      trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`certificateValidationMode`|選擇性列舉。  指定用來驗證認證之三個模式的其中一個。  此屬性的型別為 <xref:System.ServiceModel.Security.X509CertificateValidationMode>。  如果設定為 `Custom`，也必須提供 `customCertificateValidator`。|  
|`customCertificateValidatorType`|選擇性字串。  指定用來驗證自訂型別的型別和組件。  當 `certificateValidationMode` 設定為 `Custom` 時，必須設定這個屬性。  此屬性的型別為 <xref:System.IdentityModel.Selectors.X509CertificateValidator>。  [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 會提供預設的對等憑證驗證程式，針對受信任人的存放區驗證對等憑證。  它也會驗證憑證鏈結直到有效根憑證。  您可以實作自訂的驗證程式以指定不同的行為，並使用這個屬性指向自訂的驗證程式。|  
|`revocationMode`|選擇性列舉。  指定憑證撤銷模式。  此屬性的型別為 <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>。  系統會在撤銷憑證清單中查詢，以確認對等憑證尚未被撤銷。  這項檢查可以藉由線上檢查或是針對快取的撤銷清單來執行。  將此屬性設定為 NoCheck 可以關閉撤銷檢查。|  
|`trustedStoreLocation`|選擇性列舉。  指定信任之存放區的位置，[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 安全性系統會在此位置驗證對等憑證。  此屬性的型別為 <xref:System.Security.Cryptography.X509Certificates.StoreLocation>。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<peer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|指定對等節點的目前認證。|  
  
## 備註  
 `<authentication>` 項目對應至 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> 類別。  這個項目會指定驗證程式，當網狀結構中進行鄰居對鄰居驗證時，就會叫用此驗證程式。  當新對等嘗試建立鄰居連線時，它會將自己的認證傳遞至對應的對等。  會叫用回應程式的驗證器來驗證遠端方的認證。  每次在網狀結構中建立對等連線時，對等的兩方會互相驗證，亦即會叫用兩端的驗證程式。  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>   
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>   
 <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>   
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>   
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>   
 [使用憑證](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)   
 [對等網路](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)   
 [Peer Channel Message Authentication](http://msdn.microsoft.com/zh-tw/80e73386-514e-4c30-9e4a-b9ca8c173a95)   
 [Peer Channel Custom Authentication](http://msdn.microsoft.com/zh-tw/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)   
 [確保對等通道應用程式安全](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)