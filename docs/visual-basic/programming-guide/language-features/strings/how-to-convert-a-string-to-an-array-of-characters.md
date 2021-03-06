---
title: 'Postupy: Převod řetězce na pole znaků v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- character arrays [Visual Basic], converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
ms.openlocfilehash: c109143601e304b1ec15a60c71d65fe6bd15aae8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648616"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a>Postupy: Převod řetězce na pole znaků v jazyce Visual Basic
Někdy je užitečné používat data o znaky v řetězec vašeho a pozice z těchto znaků v řetězci, například když analyzujete řetězec. Tento příklad ukazuje, jak můžete získat pole znaky v řetězci voláním řetězec <xref:System.String.ToCharArray%2A> metoda.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak rozdělit řetězec do `Char` pole a jak rozdělit řetězec do `String` pole jeho textových znaků Unicode. Důvody, proč tento rozdíl je, že znaky znakové sady Unicode text může skládat ze dvou nebo více `Char` znaků (například náhradní pár nebo kombinování sekvenci znaků). Další informace najdete v tématu <xref:System.Globalization.TextElementEnumerator> a "Ve standardu Unicode" na http://www.unicode.org.  
  
 [!code-vb[VbVbalrStrings#75](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_1.vb)]  
  
## <a name="example"></a>Příklad  
 Je obtížné rozdělit řetězec na jeho text znaky znakové sady Unicode, ale to je nezbytné, pokud potřebujete informace o vizuální reprezentace řetězec. Tento příklad používá <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> metodu za účelem získání informací o textových znaků Unicode, které tvoří řetězec.  
  
 [!code-vb[VbVbalrStrings#76](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_2.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.String.Chars%2A>  
 <xref:System.Globalization.StringInfo?displayProperty=nameWithType>  
 [Postupy: Přístup ke znakům v řetězcích](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)  
 [Převod mezi řetězci a ostatními typy dat v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)  
 [Řetězce](../../../../visual-basic/programming-guide/language-features/strings/index.md)
