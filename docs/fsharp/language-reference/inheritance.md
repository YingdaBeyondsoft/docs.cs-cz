---
title: Dědičnost (F#)
description: "Zjistěte, jak určit vztahy F # dědičnosti pomocí klíčového slova 'inherit'."
ms.date: 05/16/2016
ms.openlocfilehash: 3d0c0785fc595315a8283979b99d0ec4fc5cbc0d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564762"
---
# <a name="inheritance"></a>Dědičnost

Dědičnost je použita k modelování relace "je a", nebo vytvoření podtypů v objektově orientované programování.


## <a name="specifying-inheritance-relationships"></a>Určení relace dědičnosti
Zadejte vztahy dědičnosti pomocí `inherit` – klíčové slovo v deklaraci třídy. Základní syntaktické formuláře je vidět v následujícím příkladu.

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

Třída může mít maximálně jeden přímé základní třídy. Pokud nezadáte základní třídu pomocí `inherit` – klíčové slovo, třída implicitně dědí z `System.Object`.


## <a name="inherited-members"></a>Zděděné členy
Pokud třídy dědí z jiné třídy, jsou k dispozici uživatelům odvozené třídy, jako kdyby byly přímé členy odvozené třídy metody a členy základní třídy.

Žádné let – vazby a konstruktor parametry jsou soukromá na třídu a proto nelze získat přístup z odvozené třídy.

Klíčové slovo `base` je k dispozici v odvozených třídách a odkazuje na instance základní třídy. Používá se jako vlastní identifikátor.


## <a name="virtual-methods-and-overrides"></a>Virtuální metody a přepsání
Virtuální metody (a vlastnosti) fungují trochu jinak F # porovnání s jinými jazyky rozhraní .NET. Pokud chcete deklarovat nového člena virtuální, použijte `abstract` – klíčové slovo. Můžete to udělat bez ohledu na to, jestli je zadat výchozí implementace této metody. Dokončení definice virtuální metodu v základní třídě tedy dodržuje tento vzor:

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

A v odvozené třídě, přepsání této virtuální metody, následuje tento vzor:

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

Pokud vynecháte výchozí implementace v základní třídě, základní třídy se změní na abstraktní třídu.

Následující příklad kódu ukazuje deklaraci nové virtuální metody `function1` ve základní třídu, jak k přepsání v odvozené třídě.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]
    
## <a name="constructors-and-inheritance"></a>Konstruktory a dědičnost
V konstruktoru pro základní třídy musí být voláno v odvozené třídě. Argumenty pro konstruktor základní třídy se zobrazí v seznamu argument `inherit` klauzule. Zadané argumenty konstruktoru odvozené třídy musí určit hodnoty, které se používají.

Následující kód ukazuje základní a odvozené třídy, kde odvozené třídě volá konstruktor základní třídy v klauzuli inherit:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

V případě více konstruktory můžete použít následující kód. První řádek z konstruktorů odvozené třídě je `inherit` klauzule a pole se zobrazí jako explicitní pole, které jsou deklarovány s `val` – klíčové slovo. Další informace najdete v tématu [explicitní pole: `val` – klíčové slovo](members/explicit-fields-the-val-keyword.md).

```fsharp
type BaseClass =
    val string1 : string
    new (str) = { string1 = str }
    new () = { string1 = "" }

type DerivedClass =
    inherit BaseClass

    val string2 : string
    new (str1, str2) = { inherit BaseClass(str1); string2 = str2 }
    new (str2) = { inherit BaseClass(); string2 = str2 }

let obj1 = DerivedClass("A", "B")
let obj2 = DerivedClass("A")
```

## <a name="alternatives-to-inheritance"></a>Alternativy k dědičnosti
V případech, kdy je potřeba méně závažné změny typu zvažte použití výraz objektu jako alternativu k dědičnosti. Následující příklad ukazuje použití výraz objektu jako alternativu k vytvoření nového typu odvozené:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

Další informace o objektové výrazy najdete v tématu [objektové výrazy](object-expressions.md).

Při vytváření objektu hierarchií, zvažte použití rozlišovaná sjednocení místo dědičnosti. Rozlišovaná sjednocení může taky modelu nejrůznější chování různých objektů, které sdílejí společný typ celkové. Jeden rozlišovaná sjednocení často eliminovat potřebu počet odvozené třídy, které jsou malým změnám. Informace o rozlišovaná sjednocení najdete v tématu [Rozlišované sjednocení](discriminated-unions.md).


## <a name="see-also"></a>Viz také
[Objektové výrazy](object-expressions.md)

[Referenční dokumentace jazyka F#](index.md)
