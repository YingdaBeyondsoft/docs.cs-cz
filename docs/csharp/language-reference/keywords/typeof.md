---
title: typeof (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- typeof
- typeof_CSharpKeyword
helpviewer_keywords:
- typeof keyword [C#]
ms.assetid: 0c08d880-515e-46bb-8cd2-48b8dd62c08d
ms.openlocfilehash: 4203b597d7045a13ffed9e61ddbbde57e2113c23
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171938"
---
# <a name="typeof-c-reference"></a>typeof (Referenční dokumentace jazyka C#)
Použít k získání `System.Type` objektu pro typ. A `typeof` výraz má následující podobu:  
  
```csharp  
System.Type type = typeof(int);  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud chcete získat běhového typu výrazu, můžete použít metodu rozhraní .NET Framework <xref:System.Object.GetType%2A>, jako v následujícím příkladu:  
  
```csharp  
int i = 0;  
System.Type type = i.GetType();  
```  
  
 `typeof` Operátor nemohou být přetíženy.  
  
 `typeof` Operátor můžete použít taky u otevřete obecné typy. Typy s více než jeden parametr typu musí mít odpovídající počet čárky ve specifikaci. Následující příklad ukazuje, jak určit, zda je návratový typ metody obecný <xref:System.Collections.Generic.IEnumerable%601>. Předpokládejme, že metoda instance typu MethodInfo:  
  
```csharp  
string s = method.ReturnType.GetInterface  
    (typeof(System.Collections.Generic.IEnumerable<>).FullName);  
```  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csrefKeywordsOperator#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_1.cs)]  
  
## <a name="example"></a>Příklad  
 V tomto příkladu <xref:System.Object.GetType%2A> metoda určit typ, který se používá pro jiné výsledek číselný výpočet. To závisí na požadavky na úložiště výsledné číslo.  
  
 [!code-csharp[csrefKeywordsOperator#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_2.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Type?displayProperty=nameWithType>  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [is](../../../csharp/language-reference/keywords/is.md)  
 [Klíčová slova operátorů](../../../csharp/language-reference/keywords/operator-keywords.md)
