---
title: "如何：從 XmlReader 串流 XML 片段 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: 06e2cf4b350fecf8e8310519c573ac140f05267a
ms.contentlocale: zh-tw
ms.lasthandoff: 03/24/2017

---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a>如何：從 XmlReader 串流 XML 片段 (C#)
當您必須處理大型 XML 檔案時，可能無法將整個 XML 樹狀載入記憶體中。 這個主題示範如何使用 <xref:System.Xml.XmlReader> 串流片段。  
  
 使用 <xref:System.Xml.XmlReader> 讀取 <xref:System.Xml.Linq.XElement> 物件的其中一個最有效方式，就是撰寫您自己的自訂座標軸方法。 座標軸方法通常會傳回集合，例如 <xref:System.Xml.Linq.XElement> 的 <xref:System.Collections.Generic.IEnumerable%601>，如本主題的範例中所示。 在自訂座標軸方法中，呼叫 <xref:System.Xml.Linq.XNode.ReadFrom%2A> 方法來建立 XML 片段後，使用 `yield return` 傳回集合。 這會將延後執行語意 (Semantics) 提供給您自訂的座標軸方法。  
  
 當您從 <xref:System.Xml.XmlReader> 物件建立 XML 樹狀結構時，<xref:System.Xml.XmlReader> 必須置放在某個項目上。 <xref:System.Xml.Linq.XNode.ReadFrom%2A> 方法在讀取項目的結尾標記前不會傳回。  
  
 如果您想要建立部分樹狀結構，您可以具現化 <xref:System.Xml.XmlReader>、將讀取器置放在您要轉換成 <xref:System.Xml.Linq.XElement> 樹狀結構的節點上，然後建立 <xref:System.Xml.Linq.XElement> 物件。  
  
 [如何：串流 XML 片段並存取標頭資訊 (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) 主題包含如何串流更複雜文件的資訊與範例。  
  
 [如何：執行大型 XML 文件的串流轉換 (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) 主題包含使用 LINQ to XML 轉換非常大的 XML 文件，同時維護小的記憶體使用量的範例。  
  
## <a name="example"></a>範例  
 這個範例會建立自訂座標軸方法。 您可以使用 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 查詢進行查詢。 自訂座標軸方法  `StreamRootChildDoc` 是一種方法，特別針對讀取具有重複 `Child` 項目的文件而設計。  
  
```csharp  
static IEnumerable<XElement> StreamRootChildDoc(StringReader stringReader)  
{  
    using (XmlReader reader = XmlReader.Create(stringReader))  
    {  
        reader.MoveToContent();  
        // Parse the file and display each of the nodes.  
        while (reader.Read())  
        {  
            switch (reader.NodeType)  
            {  
                case XmlNodeType.Element:  
                    if (reader.Name == "Child") {  
                        XElement el = XElement.ReadFrom(reader) as XElement;  
                        if (el != null)  
                            yield return el;  
                    }  
                    break;  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    string markup = @"<Root>  
      <Child Key=""01"">  
        <GrandChild>aaa</GrandChild>  
      </Child>  
      <Child Key=""02"">  
        <GrandChild>bbb</GrandChild>  
      </Child>  
      <Child Key=""03"">  
        <GrandChild>ccc</GrandChild>  
      </Child>  
    </Root>";  
  
    IEnumerable<string> grandChildData =  
        from el in StreamRootChildDoc(new StringReader(markup))  
        where (int)el.Attribute("Key") > 1  
        select (string)el.Element("GrandChild");  
  
    foreach (string str in grandChildData) {  
        Console.WriteLine(str);  
    }  
}  
```  
  
 這個範例會產生下列輸出：  
  
```  
bbb  
ccc  
```  
  
 在此範例中，來源文件很小。 但是，即使有數百萬的 `Child` 元素，此範例的記憶體使用量還是很小。  
  
## <a name="see-also"></a>另請參閱  
 [剖析 XML (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
