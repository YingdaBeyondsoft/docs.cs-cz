---
title: 'Postupy: Sbalení a skrytí sekcí kódu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: f6c272b7ac016258d99873512cb789bba6739727
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650852"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a>Postupy: Sbalení a skrytí sekcí kódu (Visual Basic)
`#Region` – Direktiva umožňuje sbalení a skrytí sekcí kódu v souborech jazyka Visual Basic. `#Region` Umožňuje zadat blok kódu, které můžete rozbalit nebo sbalit při použití editoru kódu v sadě Visual Studio. Umožňuje selektivně skrýt kódu umožňuje vaše soubory lépe spravovat a snadněji číst. Další informace najdete v tématu [Osnova](/visualstudio/ide/outlining).  
  
 `#Region` direktivy podporují sémantiku bloku kódu, jako například `#If...#End If`. To znamená, že nelze začít v jeden blok a končit počáteční a koncová musí být ve stejné bloku. `#Region` direktivy nejsou podporovány v rámci funkcí.  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a>Chcete-li sbalení a skrytí části kódu  
  
-   Umístěte části kódu mezi `#Region` a `#End Region` příkazy, jako v následujícím příkladu:  
  
     [!code-vb[VbVbalrConditionalComp#6](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/how-to-collapse-and-hide-sections-of-code_1.vb)]  
  
     `#Region` Bloku můžete použít více než jednou v souboru kódu; proto uživatelé mohou definovat vlastní bloky postupů a třídy, které lze, pak sbalit. `#Region` bloky mohou být také vnořené v jiných `#Region` bloky.  
  
    > [!NOTE]
    >  Skrytí kódu nezabrání z kompiluje a nemá vliv na `#If...#End If` příkazy.  
  
## <a name="see-also"></a>Viz také  
 [Podmíněná kompilace](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [Direktiva #Region](../../../visual-basic/language-reference/directives/region-directive.md)  
 [Direktivy #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [Sbalení](/visualstudio/ide/outlining)
