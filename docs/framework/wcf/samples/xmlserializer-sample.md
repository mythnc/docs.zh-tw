---
title: "XMLSerializer 範例 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7d134453-9a35-4202-ba77-9ca3a65babc3
caps.latest.revision: 23
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 23
---
# XMLSerializer 範例
這個範例會示範如何序列化和還原序列化與 <xref:System.Xml.Serialization.XmlSerializer> 相容的型別。預設的 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 格式器為 <xref:System.Runtime.Serialization.DataContractSerializer> 類別。當無法使用 <xref:System.Runtime.Serialization.DataContractSerializer> 類別時，<xref:System.Xml.Serialization.XmlSerializer> 類別可以用來序列化與還原序列化型別。這時通常需要精確控制 XML，例如，當資料片段必須是 XML 屬性而且不是 XML 項目的情況下。當建立非 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務的用戶端時，通常也會自動選取 <xref:System.Xml.Serialization.XmlSerializer>。  
  
 在這個範例中，用戶端是主控台應用程式 \(.exe\)，而服務則是由網際網路資訊服務 \(IIS\) 所裝載。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 <xref:System.ServiceModel.ServiceContractAttribute> 和 <xref:System.ServiceModel.XmlSerializerFormatAttribute> 必須套用至介面，如下列範例程式碼所示。  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"), XmlSerializerFormat]  
public interface IXmlSerializerCalculator  
{  
    [OperationContract]  
    ComplexNumber Add(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Subtract(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Multiply(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Divide(ComplexNumber n1, ComplexNumber n2);  
}  
  
```  
  
 `ComplexNumber` 類別的 Public 成員會由 <xref:System.Xml.Serialization.XmlSerializer> 序列化成 XML 屬性。<xref:System.Runtime.Serialization.DataContractSerializer> 無法用來建立這類 XML 執行個體。  
  
```  
public class ComplexNumber  
{  
    private double real;  
    private double imaginary;  
  
    [XmlAttribute]  
    public double Real  
    {  
        get { return real; }  
        set { real = value; }  
    }  
  
    [XmlAttribute]  
    public double Imaginary  
    {  
        get { return imaginary; }  
        set { imaginary = value; }  
    }  
  
    public ComplexNumber(double real, double imaginary)  
    {  
        this.Real = real;  
        this.Imaginary = imaginary;  
    }  
    public ComplexNumber()  
    {  
        this.Real = 0;  
        this.Imaginary = 0;  
    }  
  
}  
```  
  
 服務實作會計算並傳回適當的結果，即接受並傳回 `ComplexNumber` 型別的值。  
  
```  
public class XmlSerializerCalculatorService : IXmlSerializerCalculator  
{  
    public ComplexNumber Add(ComplexNumber n1, ComplexNumber n2)  
    {  
        return new ComplexNumber(n1.Real + n2.Real, n1.Imaginary +  
                                                      n2.Imaginary);  
    }  
    …  
}  
  
```  
  
 用戶端實作也會使用複數。服務合約與資料型別都會定義於 generatedClient.cs 原始程式檔中，而這個檔案是[ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 從服務中繼資料所產生的。在這個範例中，Svcutil.exe 能夠偵測合約何時無法由 <xref:System.Runtime.Serialization.DataContractSerializer> 序列化，而還原成發出 `XmlSerializable` 型別。如果要強制使用 <xref:System.Xml.Serialization.XmlSerializer>，您可以將 \/serializer:XmlSerializer \(使用 XmlSerializer\) 命令選項傳遞至 Svcutil.exe 工具。  
  
```  
// Create a client.  
XmlSerializerCalculatorClient client = new  
                         XmlSerializerCalculatorClient();  
  
// Call the Add service operation.  
ComplexNumber value1 = new ComplexNumber();  
value1.Real = 1;  
value1.Imaginary = 2;  
ComplexNumber value2 = new ComplexNumber();  
value2.Real = 3;  
value2.Imaginary = 4;  
ComplexNumber result = client.Add(value1, value2);  
Console.WriteLine("Add({0} + {1}i, {2} + {3}i) = {4} + {5}i",  
    value1.Real, value1.Imaginary, value2.Real, value2.Imaginary,   
    result.Real, result.Imaginary);  
    …  
}  
  
```  
  
 當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。  
  
```  
Add(1 + 2i, 3 + 4i) = 4 + 6i  
Subtract(1 + 2i, 3 + 4i) = -2 + -2i  
Multiply(2 + 3i, 4 + 7i) = -13 + 26i  
Divide(3 + 7i, 5 + -2i) = 0.0344827586206897 + 1.41379310344828i  
  
Press <ENTER> to terminate client.  
```  
  
### 若要設定、建置及執行範例  
  
1.  請確定您已執行 [Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案的 C\# 或 Visual Basic .NET 版本，請遵循[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3.  若要在單一或跨機器的組態中執行本範例，請遵循[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示進行。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\Interop\XmlSerializer`  
  
## 請參閱