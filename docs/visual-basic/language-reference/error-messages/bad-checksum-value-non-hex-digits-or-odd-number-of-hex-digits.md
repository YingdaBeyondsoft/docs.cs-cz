---
title: Nesprávná hodnota kontrolního součtu. Číslice nejsou v šestnáctkové soustavě nebo je zadán lichý počet číslic v šestnáctkové soustavě.
ms.date: 07/20/2015
f1_keywords:
- bc42033
- vbc42033
helpviewer_keywords:
- BC42033
ms.assetid: 4575554d-3615-46e4-9c6a-18e9c338e4ed
ms.openlocfilehash: 5c01e918e1f607febc10be89c3d27c50870c401a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589248"
---
# <a name="bad-checksum-value-non-hex-digits-or-odd-number-of-hex-digits"></a>Nesprávná hodnota kontrolního součtu. Číslice nejsou v šestnáctkové soustavě nebo je zadán lichý počet číslic v šestnáctkové soustavě.
Hodnota kontrolního součtu obsahuje neplatný šestnáctkové číslice nebo má lichý počet číslic.  
  
 Když ASP.NET generuje zdrojového souboru jazyka Visual Basic (VB rozšíření), vypočítá kontrolní součet a umístí jej do skryté zdrojového souboru identifikovaný `#externalchecksum`. Je možné pro uživatele generování souboru VB k tomu taky, ale tento proces je nejlepší vlevo na interní použití.  
  
 Ve výchozím nastavení je tato zpráva upozornění. Informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC42033  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Vytváří-li ASP.NET zdrojový soubor jazyka Visual Basic, restartujte sestavení projektu.  
  
2.  Pokud toto upozornění přetrvává po restartování, přeinstalujte ASP.NET a opakujte sestavení.  
  
3.  Pokud toto upozornění dál, nebo pokud nepoužíváte technologii ASP.NET, shromažďovat informace o okolnostech a upozornění služby Microsoft Product Support Services.  
  
## <a name="see-also"></a>Viz také  
 [Přehled technologie ASP.NET](https://msdn.microsoft.com/library/4w3ex9c2.aspx)  
 [Kontaktujte nás](/visualstudio/ide/talk-to-us)
