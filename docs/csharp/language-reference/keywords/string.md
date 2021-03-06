---
title: string (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- string
- string_CSharpKeyword
helpviewer_keywords:
- strings [C#], reference
- '@ string literal'
- string literals [C#]
- string keyword [C#]
ms.assetid: 3037e558-fb22-494d-bca1-a15ade11b11a
ms.openlocfilehash: f92a44283e59bd80421758a63b40bc5289c3628b
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172159"
---
# <a name="string-c-reference"></a>string (Referenční dokumentace jazyka C#)
`string` Typ reprezentuje posloupnosti nula nebo více znaků Unicode. `string` je alias <xref:System.String> v rozhraní .NET.  
  
 I když `string` typem je odkaz, operátory rovnosti (`==` a `!=`) jsou definovány pro porovnání hodnot `string` objekty, není odkazuje. Díky tomu bude testování rovnosti řetězec intuitivnější. Příklad:  
  
```csharp  
string a = "hello";  
string b = "h";  
// Append to contents of 'b'  
b += "ello";  
Console.WriteLine(a == b);  
Console.WriteLine((object)a == (object)b);  
```  
  
 Zobrazí "hodnotu True" a potom "False" vzhledem k tomu, že obsah řetězce jsou ekvivalentní, ale `a` a `b` neměly by konce odkazovat na stejnou instanci řetězec.  
  
 + – Operátor zřetězí řetězec:  
  
```csharp  
string a = "good " + "morning";  
```  
  
 Tím se vytvoří objekt řetězec, který obsahuje "Dobré ráno".  
  
 Řetězce jsou *neměnné*– obsah objektu řetězce nelze změnit po vytvoření objektu, i když je syntaxe se objevit, jako kdyby to provedete. Když píšete tento kód, kompilátor ve skutečnosti vytvoří nový objekt řetězec k uložení nové pořadí znaků a tento nový objekt je přiřazen k b. Řetězec "h" je pak vhodné pro uvolňování paměti.  
  
```csharp
string b = "h";  
b += "ello";  
```  
  
 [] – Operátor lze použít pro přístup jen pro čtení k jednotlivé znaky `string`:  
  
```csharp  
string str = "test";  
char x = str[2];  // x = 's';  
```  
  
 Textové literály jsou typu `string` a může být napsán ve dvou formách, v uvozovkách a @-quoted. V uvozovkách řetězec, který literály jsou uzavřené v uvozovkách ("):  
  
```csharp  
"good morning"  // a string literal  
```  
  
 Textové literály může obsahovat libovolný znak literálu. Řídicí sekvence jsou zahrnuty. Následující příklad používá řídicí sekvence `\\` pro zpětné lomítko, `\u0066` pro písmenem f, a `\n` pro nový řádek.  
  
```csharp  
string a = "\\\u0066\n";  
Console.WriteLine(a);  
```  
  
> [!NOTE]
>  Řídicí kód `\udddd` (kde `dddd` čtyři číslice) představuje znak Unicode U +`dddd`. Kódy řídicí Unicode číslice osm jsou také rozpoznána: `\Udddddddd`.  
  
 Začínat typu verbatim textové literály `@` a jsou také uzavřena v uvozovkách. Příklad:  
  
```csharp  
@"good morning"  // a string literal  
```  
  
 Výhodou typu verbatim řetězce je, že jsou řídicí sekvence *není* zpracovat, což usnadňuje zápisu, například plně kvalifikovaný název souboru:  
  
```csharp  
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"  
```  
  
 Zahrnout uvozovky v @-quoted řetězce, dvakrát ho:  
  
```csharp  
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.  
```  
  
 Pro další použití `@` speciální znak, najdete v části [@ – typu verbatim identifikátor](../tokens/verbatim.md).  
  
 Další informace o řetězcích v jazyce C# najdete v tématu [řetězce](../../../csharp/programming-guide/strings/index.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csrefKeywordsTypes#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/string_1.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Doporučené postupy pro používání řetězců](../../../standard/base-types/best-practices-strings.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Odkazové typy](../../../csharp/language-reference/keywords/reference-types.md)  
 [Typy hodnot](../../../csharp/language-reference/keywords/value-types.md)  
 [Základní operace s řetězci](../../../standard/base-types/basic-string-operations.md)  
 [Vytváření nových řetězců](../../../standard/base-types/creating-new.md)  
 [Tabulka formátování číselných výsledků](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)
