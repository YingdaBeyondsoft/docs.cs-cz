---
title: struct (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: ddea59e76835ccccd07c299f819796336cddada8
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172146"
---
# <a name="struct-c-reference"></a>struct (Referenční dokumentace jazyka C#)
A `struct` typ je typ hodnoty, které se obvykle používá k zapouzdření malé skupiny související proměnných, například souřadnice obdélníku nebo charakteristiky položky v inventář. Následující příklad ukazuje deklaraci jednoduchá struktura:  
  
```csharp  
public struct Book  
{  
    public decimal price;  
    public string title;  
    public string author;  
}  
```  
  
## <a name="remarks"></a>Poznámky  
 Struktury může také obsahovat [konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md), [konstanty](../../../csharp/programming-guide/classes-and-structs/constants.md), [pole](../../../csharp/programming-guide/classes-and-structs/fields.md), [metody](../../../csharp/programming-guide/classes-and-structs/methods.md), [vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md), [indexery](../../../csharp/programming-guide/indexers/index.md), [operátory](../../../csharp/programming-guide/statements-expressions-operators/operators.md), [události](../../../csharp/programming-guide/events/index.md), a [vnořené typy](../../../csharp/programming-guide/classes-and-structs/nested-types.md), i když je-li několik tito členové jsou povinné, můžete Zvažte, Příprava vašeho typu třídy místo.  
  
 Příklady najdete v tématu [pomocí struktury](../../../csharp/programming-guide/classes-and-structs/using-structs.md).  
  
 Struktury můžete implementovat rozhraní, ale nemohou dědit z jiné struktury. Z tohoto důvodu členy struktury nelze deklarovat jako `protected`.  
  
 Další informace najdete v tématu [struktury](../../../csharp/programming-guide/classes-and-structs/structs.md).  
  
## <a name="examples"></a>Příklady  
 Příklady a další informace najdete v tématu [pomocí struktury](../../../csharp/programming-guide/classes-and-structs/using-structs.md).  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 Příklady najdete v tématu [pomocí struktury](../../../csharp/programming-guide/classes-and-structs/using-structs.md).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Tabulka výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md)  
 [Tabulka předdefinovaných typů](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Typy](../../../csharp/language-reference/keywords/types.md)  
 [Typy hodnot](../../../csharp/language-reference/keywords/value-types.md)  
 [class](../../../csharp/language-reference/keywords/class.md)  
 [interface](../../../csharp/language-reference/keywords/interface.md)  
 [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
