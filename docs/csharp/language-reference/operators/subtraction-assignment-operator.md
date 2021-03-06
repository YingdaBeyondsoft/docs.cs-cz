---
title: -= – operátor (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction assignment operator (-=) [C#]
- -= operator (subtraction assignment ) [C#]
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
ms.openlocfilehash: 2f37bfa303fb523840b15e896ee3b4a967eb5b2b
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171452"
---
# <a name="--operator-c-reference"></a>-= – operátor (Referenční dokumentace jazyka C#)
Operátor přiřazení odčítání.  
  
## <a name="remarks"></a>Poznámky  
 K pomocí výrazu `-=` operátor přiřazení, jako například  
  
```csharp  
x -= y  
```  
  
 je ekvivalentem  
  
```csharp  
x = x - y  
```  
  
 Kromě toho, že `x` je Vyhodnocená jenom jednou. Význam [– operátor](../../../csharp/language-reference/operators/subtraction-operator.md) závisí na typech `x` a `y` (odčítání pro číselné operandy delegovat odebrání pro operandy delegáta a tak dále).  
  
 `-=` Operátor nemohou být přetíženy přímo, ale může přetížit uživatelem definované typy [– operátor](../../../csharp/language-reference/operators/subtraction-operator.md) (najdete v části [operátor](../../../csharp/language-reference/keywords/operator.md)).  
  
 -= – Operátor používá taky v jazyce C# k odhlášení odběru událostí. Další informace najdete v tématu [postupy: přihlášení a odhlášení odběru událostí](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#6](codesnippet/CSharp/subtraction-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
