---
title: stackalloc (Referenční dokumentace jazyka C#)
ms.date: 04/12/2018
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords:
- stackalloc keyword [C#]
ms.openlocfilehash: 905873cf7f576ff35a9bc1c182ce7ebe17920288
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269165"
---
# <a name="stackalloc-c-reference"></a>stackalloc (Referenční dokumentace jazyka C#)
`stackalloc` – Klíčové slovo se používá v kontextu nezabezpečený kód přidělit blok paměti v zásobníku.

```csharp
int* block = stackalloc int[100];
```

## <a name="remarks"></a>Poznámky

Klíčové slovo je platný jenom v místní proměnné inicializátory. Následující kód způsobí, že chyby kompilátoru.

```csharp
int* block;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
block = stackalloc int[100];
```

Počínaje 7.3 C#, můžete pomocí syntaxe inicializátoru pole pro `stackalloc` pole. Všechny následující deklarace deklarovat pole s tři elementy, jejichž hodnoty jsou celá čísla `1`, `2`, a `3`:

```csharp
// Valid starting with C# 7.3
int* first = stackalloc int[3] { 1, 2, 3 };
int* second = stackalloc int[] { 1, 2, 3 };
int* third = stackalloc[] { 1, 2, 3 };
```

Protože se jedná o typy ukazatelů `stackalloc` vyžaduje [unsafe](unsafe.md) kontextu. Další informace najdete v tématu [nezabezpečený kód a ukazatele](../../programming-guide/unsafe-code-pointers/index.md) 

`stackalloc` je třeba [_alloca –](/cpp/c-runtime-library/reference/alloca) v běhové knihovny jazyka C.

## <a name="examples"></a>Příklady

Následující příklad vypočítá a zobrazuje prvních 20 čísla v pořadí Fibonacciho. Všechna čísla je součet hodnot předchozích dvou čísel. V kódu bloku paměti dostatečná velikost tak, aby obsahovala 20 elementy typu `int` je přidělená v zásobníku, není haldě. Adresu bloku je uložen v ukazatele `fib`. Tuto paměť nevztahují uvolňování paměti a proto nemusí být připnutý (pomocí [pevné](fixed-statement.md)). Životnost bloku paměti je omezeno na dobu životnosti metody, která ho definuje. Nelze uvolnit paměť, než metoda vrátí.

[!code-csharp[csrefKeywordsOperator#15](../../../../samples/snippets/csharp/keywords/StackAllocExamples.cs#1)]

Tento příklad inicializuje `stackalloc` pole celých čísel na bitová maska s jeden bit nastavit v jednotlivých prvků. Tento příklad ukazuje nové syntaxe inicializátoru, která je k dispozici od 7.3 C#:

[!code-csharp[csrefKeywordsOperator#15](../../../../samples/snippets/csharp/keywords/StackAllocExamples.cs#2)]

## <a name="security"></a>Zabezpečení

Nezabezpečený kód je méně bezpečné než bezpečné alternativy. Ale použití `stackalloc` automaticky povolí funkce zjišťování přetečení vyrovnávací paměti v common language runtime (CLR). Pokud je zjištěn přetečení vyrovnávací paměti, co nejrychleji, chcete-li minimalizovat riziko, že se spustí škodlivý kód ukončení procesu.

## <a name="c-language-specification"></a>Specifikace jazyka C#
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Klíčová slova operátorů](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [Nebezpečný kód a ukazatele](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
