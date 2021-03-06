---
title: 'Postupy: Vytvoření nové metody pro výčet (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 8de44cbddf26af45245709d0e28d2d157256ce59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33313030"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a>Postupy: Vytvoření nové metody pro výčet (Průvodce programováním v C#)
Rozšiřující metody můžete přidat funkce specifické pro konkrétní výčtu typu.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Grades` výčtu představuje možné známky které student mohou zobrazit v třídě. Metody rozšíření s názvem `Passing` je přidán do `Grades` zadejte tak, aby každá instance tohoto typu teď "ví" zda představuje úrovni předávání nebo ne.  
  
 [!code-csharp[csProgGuideExtensionMethods#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-create-a-new-method-for-an-enumeration_1.cs)]  
  
 Všimněte si, že `Extensions` třída také obsahuje statické proměnné, která se dynamicky aktualizuje a že návratovou hodnotu metody rozšíření odráží aktuální hodnotu této proměnné. To znamená, že na pozadí jsou rozšiřující metody volána přímo na statické třídy, ve kterém jsou definovány.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Pokud chcete spustit tento kód, zkopírujte a vložte jej do Visual C# projektu konzolové aplikace vytvořené v sadě Visual Studio. Ve výchozím nastavení, tento projekt zaměřen na verzi 3.5 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], a obsahuje odkaz na System.Core.dll a `using` direktivy pro System.Linq. Pokud z projektu chybí jeden nebo více z těchto požadavků, můžete je přidat ručně.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Rozšiřující metody](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
