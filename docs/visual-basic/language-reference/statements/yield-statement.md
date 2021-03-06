---
title: Yield – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
ms.openlocfilehash: f938ad29df54ade6722f3de33e931c851ade8c21
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604863"
---
# <a name="yield-statement-visual-basic"></a>Yield – příkaz (Visual Basic)
Na další prvek kolekce, která se odešle `For Each...Next` příkaz.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Yield expression  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Termín|Definice|  
|---|---|  
|`expression`|Požadováno. Výraz, který je implicitně převést na typ funkce iterator nebo `Get` přistupujícího objektu, který obsahuje `Yield` příkaz.|  
  
## <a name="remarks"></a>Poznámky  
 `Yield` Příkaz vrací jeden element v kolekci najednou. `Yield` Příkaz je součástí funkce iterator nebo `Get` přistupujícího objektu, který provádět vlastní iterací v kolekci.  
  
 Využívat funkce iterator pomocí [For Each... Další příkaz](../../../visual-basic/language-reference/statements/for-each-next-statement.md) nebo dotaz LINQ. Každé iteraci `For Each` smyčky volá funkci iterator. Když `Yield` příkaz je dosaženo ve funkci iterator `expression` se vrátí, a se uchovávají aktuální umístění v kódu. Provádění je restartováno ze zmíněného umístění pokaždé, když je zavolána funkce iterátoru.  
  
 Musí existovat implicitní převod z typu `expression` v `Yield` příkaz, který má návratový typ iteraci.  
  
 Můžete použít `Exit Function` nebo `Return` příkaz k ukončení iterace.  
  
 "Výnos" není vyhrazené slovo a má zvláštní význam jenom v případě, že je používán `Iterator` funkce nebo `Get` přistupujícího objektu.  
  
 Další informace o funkcích iterator a `Get` přístupové objekty, najdete v části [iterátory](../../programming-guide/concepts/iterators.md).  
  
## <a name="iterator-functions-and-get-accessors"></a>Iterator funkce a Get přístupové objekty  
 Deklarace funkce iterator nebo `Get` přistupujícího objektu musí splňovat následující požadavky:  
  
-   Musí obsahovat [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md) modifikátor.  
  
-   Návratový typ musí být <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, nebo <xref:System.Collections.Generic.IEnumerator%601>.  
  
-   Nemůže mít žádné `ByRef` parametry.  
  
 Iterator funkce nemohou být v události, konstruktoru instance, statického konstruktoru nebo statické destruktor.  
  
 Iterator funkce může být anonymní funkce. Další informace najdete v tématu [iterátory](../../programming-guide/concepts/iterators.md).  
  
## <a name="exception-handling"></a>Zpracování výjimek  
 A `Yield` příkaz může být uvnitř `Try` blokovat z [zkuste... Catch... Finally – příkaz](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). A `Try` blok, který má `Yield` příkaz může mít `Catch` blokuje a může mít `Finally` bloku.  
  
 A `Yield` příkaz nemůže být uvnitř `Catch` bloku nebo `Finally` bloku.  
  
 Pokud `For Each` textu (mimo funkci iterator) vyvolá výjimku, `Catch` bloku ve funkci iterator není proveden, ale `Finally` bloku ve funkci iterator se spustí. A `Catch` bloku uvnitř funkce iterator zachytí pouze výjimky, které nastat uvnitř funkce iterator.  
  
## <a name="technical-implementation"></a>Technická implementace  
 Následující kód vrátí `IEnumerable (Of String)` z funkce iterator a pak iteruje v rámci prvků `IEnumerable (Of String)`.  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 Volání `MyIteratorFunction` neprovede tělo funkce. Místo toho se volání vrátí `IEnumerable(Of String)` do `elements` proměnné.  
  
 Na iterace `For Each` smyčky, <xref:System.Collections.IEnumerator.MoveNext%2A> metoda je volána pro `elements`. Toto volání provede text `MyIteratorFunction` až do dalšího `Yield` je dosaženo příkaz. `Yield` Příkaz vrací výraz, který určuje, ne jenom hodnotu `element` proměnná pro spotřeba těla smyčky, ale také <xref:System.Collections.Generic.IEnumerator%601.Current%2A> vlastnost elementů, která je `IEnumerable (Of String)`.  
  
 Při každém opakování následné `For Each` cykly, odkud pokračuje v provádění těla iterator bylo přerušeno, znovu zastavit při dosažení `Yield` příkaz. `For Each` Dokončení smyčky, kdy konec iterator funkce nebo `Return` nebo `Exit Function` je dosaženo příkaz.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu má `Yield` příkaz, který je uvnitř [pro... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) smyčky. Každé iteraci [pro každou](../../../visual-basic/language-reference/statements/for-each-next-statement.md) těla příkazu v `Main` vytvoří volání `Power` iterator funkce. Každé volání funkce iterator pokračuje dalším spuštění `Yield` příkaz, který spadá další iterace `For…Next` smyčky.  
  
 Návratový typ metody iterator <xref:System.Collections.Generic.IEnumerable%601>, typu iterator rozhraní. Při volání metody iterátoru je vrácen vyčíslitelný objekt, který obsahuje mocniny čísla.  
  
 [!code-vb[VbVbalrStatements#98](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_1.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje `Get` přistupujícího objektu, který je iterátor. Obsahuje deklarace vlastnosti `Iterator` modifikátor.  
  
 [!code-vb[VbVbalrStatements#99](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_2.vb)]  
  
 Další příklady najdete v tématu [iterátory](../../programming-guide/concepts/iterators.md).  
  
## <a name="see-also"></a>Viz také  
 [Příkazy](../../../visual-basic/language-reference/statements/index.md)
