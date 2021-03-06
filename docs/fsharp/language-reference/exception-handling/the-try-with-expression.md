---
title: 'Výjimky: Výraz try...with (F#)'
description: "Naučte se používat pro zpracovávání výjimek v jazyce F # 'try... with' výraz."
ms.date: 05/16/2016
ms.openlocfilehash: 5e6e16d5fba88841d567512ba7e08a2e8d17bdba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565285"
---
# <a name="exceptions-the-trywith-expression"></a>Výjimky: Výraz try...with

Toto téma popisuje `try...with` výrazu, výraz, který se používá pro zpracování výjimek v jazyce F #.


## <a name="syntax"></a>Syntaxe

```fsharp
try
    expression1
with
| pattern1 -> expression2
| pattern2 -> expression3
...
```

## <a name="remarks"></a>Poznámky
`try...with` Výraz se používá pro zpracování výjimek v jazyce F #. Je podobná `try...catch` příkaz v jazyce C#. V předchozím syntaxi kód v *expression1* může generovat výjimku. `try...with` Vrací hodnotu výrazu. Pokud nedojde k výjimce, celý výraz vrací hodnotu *expression1*. Pokud je vyvolána výjimka, každý *vzor* se pak porovná s výjimkou a pro první odpovídající vzor odpovídající *výraz*, označovaný jako *obslužná rutina výjimky*, je proveden uvedené pobočky a celkové výraz vrací hodnotu výrazu v této obslužné rutiny výjimek. Pokud žádné vzor odpovídá, výjimka šíří zásobníkem volání, dokud nebude nalezen odpovídající obslužná rutina. Typy hodnot vrácených z každého výrazu v obslužné rutiny výjimek musí odpovídat typ vrácený z výrazu v `try` bloku.

Fakt, že došlo k chybě také často, znamená, že je žádné platnou hodnotu, která lze vrátit ze výrazy v každé obslužné rutiny výjimky. Časté vzor je tak, aby měl být typu možnost Typ výrazu. Následující příklad kódu ukazuje tento vzor.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5601.fs)]

Výjimky může být výjimky .NET, nebo mohou být výjimky F #. Můžete taky definovat výjimky F # pomocí `exception` – klíčové slovo.

Řadu vzorů můžete použít k filtrování na typ výjimky a další podmínky; Možnosti jsou shrnuty v následující tabulce.


|Vzor|Popis|
|-------|-----------|
|:? *Typ výjimky*|Odpovídá zadaný typ výjimky .NET.|
|:? *Typ výjimky* jako *identifikátor*|Odpovídá zadaný typ výjimky .NET, ale dává výjimka pojmenované hodnotě.|
|*název výjimky*(*argumenty*)|Odpovídá typ výjimky F # a sváže argumenty.|
|*Identifikátor*|Odpovídá jakékoli výjimky a sváže název objekt výjimky. Ekvivalentní **:? System.Exception jako *** identifikátor*|
|*identifikátor* při *podmínky*|Odpovídá jakékoli výjimky, pokud je podmínka vyhodnocena jako true.|

## <a name="examples"></a>Příklady
Následující příklady kódu ilustrují použití různých vzorů obslužná rutina výjimky.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5602.fs)]
    
>[!NOTE] 
`try...with` Konstrukce je samostatného výrazu z `try...finally` výraz. Proto pokud kódu vyžaduje, aby obě `with` bloku a `finally` bloku, budete muset vnořit dvou výrazů.

>[!NOTE] 
Můžete použít `try...with` v asynchronní pracovní postupy a další výpočetní výrazy, ve kterém případ přizpůsobená verze `try...with` použit výraz. Další informace najdete v tématu [asynchronní pracovní postupy](../asynchronous-workflows.md), a [výpočetní výrazy](../computation-expressions.md).


## <a name="see-also"></a>Viz také
[Zpracování výjimek](index.md)

[Typy výjimek](exception-types.md)

[Výjimky: `try...finally` výraz](the-try-finally-expression.md)
