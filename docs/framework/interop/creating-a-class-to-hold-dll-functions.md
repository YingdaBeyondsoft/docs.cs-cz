---
title: Vytvoření třídy k umístění funkcí DLL
ms.date: 03/30/2017
helpviewer_keywords:
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, creating class for functions
- DLL functions
ms.assetid: e08e4c34-0223-45f7-aa55-a3d8dd979b0f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 09088d1ac0a8312ee5832a5f3bc0547e6654de93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33387059"
---
# <a name="creating-a-class-to-hold-dll-functions"></a>Vytvoření třídy k umístění funkcí DLL
Zabalení často používané funkce DLL v třídě spravované je efektivní přístup k zapouzdření funkce platformy. Přestože není povinný Uděláte to tak v každém případě, za předpokladu, že třída obálky je vhodné, protože definice funkcí knihovny DLL může být pracné a k chybám. Pokud programujete v jazyce Visual Basic nebo C#, je potřeba deklarovat funkcí knihovny DLL v rámci třídy nebo modulu Visual Basic.  
  
 V rámci třídy zadejte statickou metodu pro každou funkci knihovny DLL, kterou chcete volat. Definice může obsahovat další informace, jako je znaková sada nebo konvence volání, které jsou používány předání argumentů metoda; Díky vynechání tyto informace, vyberte výchozí nastavení. Úplný seznam možností deklarace a výchozí nastavení, najdete v části [vytváření prototypů ve spravovaného kódu](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).  
  
 Jakmile zabalená, jak můžete volat metody pro třídu volat statické metody pro jiná třída. Vyvolání platformy zpracovává základní exportované funkce automaticky.  
  
 Při navrhování spravované třídy pro platformu vyvolání, zvažte vztahy mezi třídami a funkcí knihovny DLL. Například můžete:  
  
-   Deklarace funkcí knihovny DLL v rámci existující třídy.  
  
-   Vytvořte jednotlivých tříd pro jednotlivé funkce DLL zachování funkce izolované a snadno najít.  
  
-   Vytvořte jednu třídu pro sadu souvisejících funkcí knihovny DLL na formuláři logické seskupení a snížit režii.  
  
 Třída a její metody, jako je můžete prosím název. Příklady, které ukazují, jak vytvořit. Na základě NET deklarace, který se má použít s platformou vyvolání najdete v tématu [zařazování dat s vyvolání platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).  
  
## <a name="see-also"></a>Viz také  
 [Používání nespravovaných funkcí DLL](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 [Identifikace funkcí ve knihovnách DLL](../../../docs/framework/interop/identifying-functions-in-dlls.md)  
 [Vytváření prototypů ve spravovaném kódu](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [Volání funkce DLL](../../../docs/framework/interop/calling-a-dll-function.md)
