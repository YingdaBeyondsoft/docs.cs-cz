---
title: Zásady vytváření názvů jazyka Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- names [Visual Basic], Visual Basic rules
- naming conventions
- naming conventions [Visual Basic], Visual Basic
- Visual Basic code, naming conventions
- conventions [Visual Basic], Visual Basic coding
- names [Visual Basic], naming conventions
- naming conventions [Visual Basic], classes
ms.assetid: 164949a4-2a7c-4736-9d82-9c3078e2e56c
ms.openlocfilehash: cb7e9f2a577e95e09fde885df1a78aea4e7fa466
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651915"
---
# <a name="visual-basic-naming-conventions"></a>Zásady vytváření názvů jazyka Visual Basic
Pokud zadáte název elementu v aplikaci Visual Basic, musí být první znak tohoto názvu znakem abecedy nebo podtržítkem. Upozorňujeme však, že nejsou kompatibilní s názvy počínaje podtržítkem [jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS).  
  
 Následující návrhy se vztahují na názvy.  
  
-   Začněte všech samostatných slov v názvu s velkým písmenem, jako v `FindLastRecord` a `RedrawMyForm`.  
  
-   Začněte funkce a metoda názvy s operaci, jako v `InitNameArray` nebo `CloseDialog`.  
  
-   Begin – třída, struktura, modulu a názvy vlastností s podstatné jméno, jako v `EmployeeName` nebo `CarAccessory`.  
  
-   Začněte názvy rozhraní s předponou "I", za nímž následuje spojení podstatného jména nebo frázi podstatné jméno, jako je třeba `IComponent`, nebo s přídavné jméno popisující chování rozhraní, jako je třeba `IPersistable`. Podtržítko a nepoužíváte zkratky používejte opatrně, protože zkratky může způsobit nejasnostem.  
  
-   Názvy obslužné rutiny událostí začínat spojení podstatného jména popisující typ události, za nímž následuje "`EventHandler`"v přípona"`MouseEventHandler`".  
  
-   V názvech třídy argument události, zahrnout "`EventArgs`" příponu.  
  
-   Pokud událost obsahuje koncept "před" nebo "po", použijte příponu v současné době nebo minulost, jako v "`ControlAdd`"nebo"`ControlAdded`".  
  
-   Dlouhá nebo často používaných podmínky použijte zkratky zachovat název délky rozumné řešení, například "HTML", místo "Jazyk HTML". Větší než 32 znaků názvy proměnných jsou obecně obtížné číst na nízkou rozlišení monitoru. Taky se ujistěte, že vaše zkratky jsou konzistentní v celé aplikaci. Náhodně přepínání v projektu mezi "HTML" a "Jazyk HTML" může vést k nejasnostem.  
  
-   Nepoužívejte názvy v informacích o vnitřní oboru, které jsou stejné jako názvy ve vnějším oboru. Chyby může způsobit Pokud proměnnou nesprávný přistupuje. Pokud dojde ke konfliktu mezi proměnnou a klíčového slova se stejným názvem, musí identifikovat klíčové slovo tak, že před s knihovnou příslušného typu. Například, pokud máte proměnnou s názvem `Date`, můžete použít vnitřní `Date` funkce pouze voláním <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova jako názvy elementů v kódu](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 [Me, My, MyBase a MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [Deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Struktura programu a zásady týkající se kódu](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [Referenční dokumentace jazyka Visual Basic](../../../visual-basic/language-reference/index.md)
