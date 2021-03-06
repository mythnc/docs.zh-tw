---
title: "&lt;issuedToken&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# &lt;issuedToken&gt;
指定用來向服務驗證用戶端的自訂權杖。  
  
## 語法  
  
```  
  
<issuedToken   
   cacheIssuedTokens="Boolean"  
   defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"  
   issuedTokenRenewalThresholdPercentage = "0 to 100"  
   issuerChannelBehaviors="String"  
      localIssuerChannelBehaviors="String"  
   maxIssuedTokenCachingTime="TimeSpan"  
</issuedToken>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`cacheIssuedTokens`|選用性的布林值屬性，指定是否快取權杖。  預設為 `true`。|  
|`defaultKeyEntropyMode`|選用性字串屬性，這個屬性會指定交握作業要使用的亂數值 \(Entropy\)。  值包括 `ClientEntropy`、`ServerEntropy` 與 `CombinedEntropy`，預設為 `CombinedEntropy`。  此屬性的型別為 <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>。|  
|`issuedTokenRenewalThresholdPercentage`|選用性的整數屬性，這個屬性會指定權杖更新前，可通過的有效時間範圍 \(由權杖簽發者提供\) 百分比。  值為 0 到 100。  預設為 60，表示嘗試更新前有 60% 的時間通過。|  
|`issuerChannelBehaviors`|選用性屬性，這個屬性會指定與簽發者通訊時所用的通道行為。|  
|`localIssuerChannelBehaviors`|選用性屬性，這個屬性會指定與本機簽發者通訊時所用的通道行為。|  
|`maxIssuedTokenCachingTime`|選用性的 Timespan 屬性，當權杖簽發者 \(STS\) 沒有指定時間時，指定快取發行的權杖之期間。  預設為 “10675199.02:48:05.4775807”。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<localIssuer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|指定權杖的本機簽發者位址，與用來與端點通訊的繫結。|  
|[\<issuerChannelBehaviors\>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|指定連絡本機簽發者時要使用的端點行為。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<clientCredentials\>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|指定用來對服務驗證用戶端的認證。|  
  
## 備註  
 發行的權杖會在某些情況下當做自訂認證型別使用，例如在聯合案例中與安全權杖服務 \(STS\) 進行驗證時。  根據預設，這個權杖是 SAML 權杖。  如需詳細資訊，請參閱[聯合與發行的權杖](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)。  和 [聯合與發行的權杖](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)。  
  
 這個區段包含用以設定權杖之本機簽發者的項目，或搭配安全性權杖服務使用的行為。  如需將用戶端設定為使用本機簽發者的指示，請參閱 [HOW TO：設定本機簽發者](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)。  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>   
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>   
 <xref:System.ServiceModel.Description.ClientCredentials>   
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>   
 <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>   
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>   
 [安全性行為](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)   
 [確保服務與用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [聯合與發行的權杖](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)   
 [確保用戶端的安全](../../../../../docs/framework/wcf/securing-clients.md)   
 [HOW TO：建立聯合用戶端](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)   
 [HOW TO：設定本機簽發者](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)   
 [聯合與發行的權杖](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)