---
title: "public (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- public
- public_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
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
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e2d6350b6c7c2490d42d08ebd169a35b40d20900
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="public-c-reference"></a>public (C# 參考)
`public` 關鍵字是類型和類型成員的存取修飾詞。 公用存取是最寬鬆的存取層級。 不會限制存取公用成員，如此範例所示︰  
  
```  
class SampleClass  
{  
    public int x; // No access restrictions.  
}  
```  
  
 如需詳細資訊，請參閱[存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)和[存取範圍層級](../../../csharp/language-reference/keywords/accessibility-levels.md)。  
  
## <a name="example"></a>範例  
 在下列範例中，宣告兩個類別：`PointTest` 和 `MainClass`。 `PointTest`的公用成員 `x` 和 `y` 直接存取自 `MainClass`。  
  
 [!code-cs[csrefKeywordsModifiers#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/public_1.cs)]  
  
 如果您將 `public` 存取層級變更為 [private](../../../csharp/language-reference/keywords/private.md) 或 [protected](../../../csharp/language-reference/keywords/protected.md)，則會收到錯誤訊息：  
  
 'PointTest.y' 的保護層級導致無法對其進行存取。  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [存取修飾詞](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [存取範圍層級](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [修飾詞](../../../csharp/language-reference/keywords/modifiers.md)   
 [private](../../../csharp/language-reference/keywords/private.md)   
 [protected](../../../csharp/language-reference/keywords/protected.md)   
 [internal](../../../csharp/language-reference/keywords/internal.md)
