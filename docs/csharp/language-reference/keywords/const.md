---
title: const (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- const_CSharpKeyword
- const
helpviewer_keywords:
- const keyword [C#]
ms.assetid: 79eb447c-117b-4418-933f-97c50aa472db
ms.openlocfilehash: 0038c1472964e618ee52ded9731fcb3e1e3ca204
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216243"
---
# <a name="const-c-reference"></a>const (Referenční dokumentace jazyka C#)
Můžete použít `const` – klíčové slovo deklarace konstantní pole nebo konstantní místní. Konstantní pole a místní hodnoty nejsou proměnné a nejde ho upravit. Konstanty mohou obsahovat čísla, logické hodnoty, řetězce nebo odkaz s hodnotou null. Nevytvářejte konstanta představují informace, které byste měli kdykoli změnit. Například nepoužívejte konstantní pole k uložení ceny služby, číslo verze produktu nebo název značky společnosti. Tyto hodnoty můžete změnit v čase, a protože kompilátory rozšířit konstanty, jiný kód, kompilovat s vaší knihovny bude muset být překompilovat, aby se změny projevily. Viz také [jen pro čtení](../../../csharp/language-reference/keywords/readonly.md) – klíčové slovo. Příklad:  
  
```csharp
const int x = 0;  
public const double gravitationalConstant = 6.673e-11;  
private const string productName = "Visual C#";  
```  
  
## <a name="remarks"></a>Poznámky  
 Typ deklarace konstanty Určuje typ členy, kteří zavádí deklaraci. Inicializátor konstanta místní nebo konstantní pole musí být konstantní výraz, který lze implicitně převést na typ cíle.  
  
 Konstantní výraz je výraz, který může být plně vyhodnocen v době kompilace. Proto možné pouze hodnoty pro konstanty odkazové typy jsou `string` a odkaz s hodnotou null.  
  
 Deklarace konstanty můžou deklarovat několik konstanty, jako například:  
  
```csharp
public const double x = 1.0, y = 2.0, z = 3.0;  
```  
  
 `static` Modifikátor není povolen v deklaraci konstantní.  
  
 Konstanta mohl účastnit konstantní výraz, následujícím způsobem:  
  
```csharp
public const int c1 = 5;  
public const int c2 = c1 + 100;  
```  
  
> [!NOTE]
>  [Jen pro čtení](../../../csharp/language-reference/keywords/readonly.md) – klíčové slovo se liší od `const` – klíčové slovo. A `const` pole lze inicializovat pouze na deklaraci pole. A `readonly` pole jde inicializovat na deklaraci nebo v konstruktoru. Proto `readonly` pole může mít různé hodnoty v závislosti na konstruktoru použít. Také i když `const` pole je argumentem konstanta kompilaci `readonly` pole lze použít pro spuštění konstanty, stejně jako tento řádek: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csrefKeywordsModifiers#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/const_1.cs)]  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak používat konstanty jako místní proměnné.  
  
 [!code-csharp[csrefKeywordsModifiers#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/const_2.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Modifikátory](../../../csharp/language-reference/keywords/modifiers.md)  
 [readonly](../../../csharp/language-reference/keywords/readonly.md)
