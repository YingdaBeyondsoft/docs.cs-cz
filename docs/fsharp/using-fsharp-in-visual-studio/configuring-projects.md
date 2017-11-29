---
title: "Konfigurace projektů (F #)"
description: "Naučte se používat v Návrháři projektu při práci s projekty F # v sadě Visual Studio."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 8b2ed206-34e4-4256-a6ce-0c2499561165
ms.openlocfilehash: d2a92f725c40443c8dc6af593d28deccd3ee88de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="configuring-projects-in-visual-studio"></a>Konfigurace projektů v sadě Visual Studio

> [!NOTE]
V tomto článku není aktuální pomocí nejnovější sady Visual Studio.  Bude aktualizována.

Toto téma obsahuje informace o tom, jak používat **Návrhář projektu** při práci s projekty F #. Práce s projekty F # není výrazně liší od práce s projekty Visual Basic a C#. Obecné dokumentaci projektu sady Visual Studio můžete často použít jako primární odkaz při použití F #. Toto téma obsahuje odkazy na příslušné informace v dokumentaci k sadě Visual Studio pro nastavení, které jsou sdíleny s jinými jazyky Visual Studio a také popisuje nastavení, které jsou specifické pro F #.

## <a name="project-designer"></a>návrhář projektu
**Návrhář projektu** a jeho obecné použití jsou plně popsané v tématu [Úvod do Návrhář projektu](https://msdn.microsoft.com/library/898dd854-c98d-430c-ba1b-a913ce3c73d7) v dokumentaci sady Visual Studio. **Návrhář projektu** se skládá z několika stránek seskupené podle související funkce. Stránky, které jsou k dispozici pro projekty F # jsou většinou podmnožinu těchto k dispozici pro jiné jazyky. Na stránkách podporované v jazyce F # jsou popsané v následující tabulce. Funkce, které nejsou k dispozici v F # nebo které jsou k dispozici pouze změnou možnosti příkazového řádku se týkají stránek, které nejsou k dispozici. Stránek, které jsou k dispozici v F # vypadat stránky C# nejvíce, takže je k dispozici odkaz na příslušné C# **Návrhář projektu** stránky.

|Stránka Návrhář projektu|Související odkazy|Popis|
|---------------------|-------------|-----------|
|`Application`|[Stránka aplikace, Návrhář projektu &#40; C &#35; &#41;](https://msdn.microsoft.com/library/ms247046.aspx)|Umožňuje zadat nastavení na úrovni aplikace a vlastnosti, například zda vytváříte knihovnu nebo spustitelného souboru, jaká verze rozhraní .NET Framework cílení aplikace a informace o kde prostředek soubory, které aplikace ukládají se používá.|
|`Build`|[Vytvořit stránku, Návrhář projektu &#40; C &#35; &#41;](https://msdn.microsoft.com/library/kb4wyys2.aspx)|Umožňuje řídit, jak je zkompilovat kód.|
|`Build Events`|[Vytvoření stránky události, Návrhář projektu &#40; C &#35; &#41;](https://msdn.microsoft.com/library/kb4wyys2.aspx)|Umožňuje zadat příkazy, pomocí před nebo po kompilace.|
|`Debug`|[Stránka ladění, Návrhář projektu](https://msdn.microsoft.com/library/2wcdezs5.aspx)|Umožňuje řídit, jak je aplikace spuštěná během ladění. To zahrnuje co příkazového řádku mají být použity a co je spouštěcí adresář vaší aplikace a všechny speciální ladění režimy, které chcete povolit, jako je například nativního kódu a SQL.|
|`Reference Paths`|[Správa odkazů v projektu](https://msdn.microsoft.com/library/ez524kew.aspx)|Umožňuje určit, kam k vyhledání sestavení, která kód závisí na.|

## <a name="f-specific-settings"></a>F # – konkrétní nastavení
Následující tabulka shrnuje nastavení, které jsou specifické pro F #:

|Stránka Návrhář projektu|Nastavení|Popis|
|---------------------|-------|-----------|
|`Build`|`Generate tail calls`|Pokud je vybraná, umožňuje použití tail instrukcí (MSIL intermediate language) společnosti Microsoft. To způsobí, že rámce zásobníku znovu použije pro rekurzivní funkce tail. Ekvivalentní `--tailcalls` – možnost kompilátoru.|
|`Build`|`Other flags`|Umožňuje zadat parametry příkazového řádku kompilátoru Další.|

## <a name="see-also"></a>Viz také
 [Začínáme s F # v sadě Visual Studio](../get-started/get-started-visual-studio.md)  
 [Možnosti kompilátoru](../language-reference/compiler-options.md)  
 [Úvod do Návrhář projektu](https://msdn.microsoft.com/library/898dd854-c98d-430c-ba1b-a913ce3c73d7(v=vs.100))