---
title: Rozhraní (F#)
description: 'Zjistěte, jak zadat F # rozhraní sady souvisejících členů, které implementují jiné třídy.'
ms.date: 05/16/2016
ms.openlocfilehash: 54ae8a2840ce26814be25f08c3ed02e12df6b7c0
ms.sourcegitcommit: ff1d40507b3eb6e2185478e37c66c66be6de46f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/11/2018
ms.locfileid: "34058894"
---
# <a name="interfaces"></a>Rozhraní

*Rozhraní* zadejte sady souvisejících členů, které implementují jiné třídy.

## <a name="syntax"></a>Syntaxe

```fsharp
// Interface declaration:
[ attributes ]
type [accessibility-modifier] interface-name =
    [ interface ]     [ inherit base-interface-name ...]
    abstract member1 : [ argument-types1 -> ] return-type1
    abstract member2 : [ argument-types2 -> ] return-type2
    ...
[ end ]

// Implementing, inside a class type definition:
interface interface-name with
    member self-identifier.member1argument-list = method-body1
    member self-identifier.member2argument-list = method-body2

// Implementing, by using an object expression:
[ attributes ]
let class-name (argument-list) =
    { new interface-name with
        member self-identifier.member1argument-list = method-body1
        member self-identifier.member2argument-list = method-body2
        [ base-interface-definitions ]
    }
    member-list
```

## <a name="remarks"></a>Poznámky
Deklarace rozhraní vypadat podobně jako deklarace tříd s tím rozdílem, že jsou implementované žádní členové. Místo toho jsou všechny členy abstraktní, jak je uvedeno klíčovým slovem `abstract`. Pro abstraktní metody nezadáte těla metody. Výchozí implementace však můžete zadat také zahrnutím samostatné definice člena jako metodu společně s `default` – klíčové slovo. Díky tomu je ekvivalentní k vytvoření virtuální metodu v základní třídě v jinými jazyky rozhraní .NET. Virtuální metoda může být přepsána nastaveními v třídy, které implementují rozhraní.

Je výchozí usnadnění pro rozhraní `public`.

Můžete volitelně zadejte každý parametr metody název pomocí normální F # – syntaxe:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

Ve výše `ISprintable` například `Print` metoda má jeden parametr typu `string` s názvem `format`.

Existují dva způsoby, jak implementovat rozhraní: pomocí objektové výrazy a pomocí typy tříd. V obou případech výraz typu nebo objektu třídy poskytuje těla metodu pro abstraktní metody rozhraní. Implementace jsou specifické pro každý typ, který implementuje rozhraní. Proto může být metody rozhraní na různé typy liší od sebe navzájem.

Klíčová slova `interface` a `end`, který označit počáteční a koncová definice, jsou volitelné, pokud použijete prostá syntaxe. Pokud nepoužijete tato klíčová slova, pokusí se kompilátor odvození, zda je typ třídy nebo rozhraní analýzou konstrukce, které používáte. Pokud definovat člena nebo použijte jiné třídy syntaxi, typ interpretována jako třída.

Kódování styl .NET je začít všech rozhraní s velkým `I`.


## <a name="implementing-interfaces-by-using-class-types"></a>Implementace rozhraní pomocí typy tříd
V typu třídy můžete implementovat jednu nebo více rozhraní pomocí `interface` – klíčové slovo, název rozhraní a `with` – klíčové slovo, za nímž následuje člen definice rozhraní, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

Implementace rozhraní jsou zděděné, takže není nutné je přeimplementovat všechny odvozené třídy.


## <a name="calling-interface-methods"></a>Volání metody rozhraní
Metody rozhraní lze volat pouze přes rozhraní, nikoli pomocí libovolného objektu typu, který implementuje rozhraní. Proto může být nutné přetypování nahoru na typ rozhraní pomocí `:>` operátor nebo `upcast` operátor k volání těchto metod.

K volání metody rozhraní, když máte objekt typu `SomeClass`, musíte přetypování nahoru objekt, který má typ rozhraní, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

Alternativou je deklarujte metodu pro objekt, že upcasts a volá metodu rozhraní, jako v následujícím příkladu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]
    
## <a name="implementing-interfaces-by-using-object-expressions"></a>Implementace rozhraní pomocí objektové výrazy
Objektové výrazy zadejte krátký způsob, jak implementovat rozhraní. Jsou užitečné v případě, že nemáte k vytvoření pojmenovaného typu, a chcete objekt, který podporuje metody rozhraní, bez jakékoli další metody. Výraz objektu je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]
    
## <a name="interface-inheritance"></a>Rozhraní dědičnosti
Rozhraní může dědit vlastnosti z jednoho nebo více základní rozhraní.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]
    
## <a name="see-also"></a>Viz také
[Referenční dokumentace jazyka F#](index.md)

[Objektové výrazy](object-expressions.md)

[Třídy](classes.md)
