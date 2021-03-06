---
title: 'Postupy: Odstranění neplatných znaků z řetězce'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, examples
- cleaning input
- user input, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- Regex.Replace method
- stripping invalid characters
- Replace method
- validating user input
ms.assetid: b4319c8a-9032-4129-a9d5-6f6fc28e7f32
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 66fe5dd1da148e8afd07ae69cec960438b53536a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567351"
---
# <a name="how-to-strip-invalid-characters-from-a-string"></a>Postupy: Odstranění neplatných znaků z řetězce
Následující příklad používá statické <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metoda pro odstranění neplatných znaků z řetězce.  
  
## <a name="example"></a>Příklad  
 Můžete použít `CleanInput` metoda definované v tomto příkladu pro odstranění potenciálně škodlivých znaků, které byly zadány do textového pole, které přijímá vstup uživatele. V takovém případě `CleanInput` odstraní všechny nealfanumerické znaky s výjimkou tečky (.) a symboly (@), pomlčky (-) a vrátí zbývající řetězec. Regulární výraz však můžete upravit tak, aby se odstraní všechny znaky, které by neměly být obsažené ve vstupní řetězec.  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 Regulární výraz `[^\w\.@-]` odpovídá jakémukoliv znaku, který není písmenem, tečky, @ symbol nebo pomlčky. Jakékoli písmeno, číslici desítkové soustavy nebo interpunkce konektoru třeba podtržítko je znak aplikace word. Libovolný znak, který odpovídá tomuto vzoru nahrazuje <xref:System.String.Empty?displayProperty=nameWithType>, což je řetězec definované vzor nahrazení. Povolit další znaky ve vstupu uživatele, přidejte do třídy znaků v regulární výraz tyto znaky. Například vzor regulárního výrazu `[^\w\.@-\\%]` také umožňuje symbol procenta a zpětné lomítko ve vstupním řetězci.  
  
## <a name="see-also"></a>Viz také  
 [Regulární výrazy rozhraní .NET](../../../docs/standard/base-types/regular-expressions.md)
