---
title: 'Výjimky: Funkce raise (F#)'
description: "Zjistěte, jak F # 'vyvolat' funkce slouží k označení, že došlo k chybě nebo výjimečně vysoké počty podmínku."
ms.date: 05/16/2016
ms.openlocfilehash: bad18bfbccd738a12e16a0e026ade22e96d4cfcb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564742"
---
# <a name="exceptions-the-raise-function"></a>Výjimky: Funkce raise

`raise` Funkce slouží k označení, že došlo k chybě nebo výjimečně vysoké počty podmínku. Informace o této chybě se zaznamená v objektu výjimky.


## <a name="syntax"></a>Syntaxe

```fsharp
raise (expression)
```

## <a name="remarks"></a>Poznámky
`raise` Funkce generuje objekt výjimky a zahájí unwinding proces zásobníku. Proces unwinding zásobníku je spravovaný modul CLR (CLR), takže chování tohoto procesu je stejný, jako je v kterémkoli jazyce platformy .NET. Proces unwinding zásobníku je vyhledávání pro obslužnou rutinu výjimky odpovídající generovaného výjimka. Spustí vyhledávání v aktuální `try...with` výrazu, jestliže existuje. Každý vzor v `with` bloku je zaškrtnuto, v pořadí. Když se najde odpovídající obslužná rutina výjimky, výjimka považuje za zpracovává; jinak je oddělen zásobníku a `with` bloky řetězem volání jsou zaškrtnutá políčka, dokud nebude nalezen odpovídající obslužná rutina. Všechny `finally` bloky, které se vyskytují v řetězu volání jsou také provést v pořadí, protože unwinds zásobníku.

`raise` Funkce je ekvivalentem `throw` v C# nebo C++. Použití `reraise` v obslužné rutině catch potřebný k šíření bude stejná výjimka řetězem volání.

Následující příklady kódu ilustrují použití `raise` funkce, která se vygeneruje výjimka.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

`raise` Funkce mohou sloužit také pro vyvolání výjimky .NET, jak je znázorněno v následujícím příkladu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]
    
## <a name="see-also"></a>Viz také
[Zpracování výjimek](index.md)

[Typy výjimek](exception-types.md)

[Výjimky: `try...with` výraz](the-try-with-expression.md)

[Výjimky: `try...finally` výraz](the-try-finally-expression.md)

[Výjimky: `failwith` – funkce](the-failwith-function.md)

[Výjimky: `invalidArg` – funkce](the-invalidArg-function.md)
