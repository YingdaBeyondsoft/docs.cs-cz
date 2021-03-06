---
title: -target (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- target compiler options [Visual Basic]
- -target compiler options [Visual Basic]
- /target compiler options [Visual Basic]
ms.assetid: e0954147-548b-461f-9c4b-a8f88845616c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4097d82772c24bb0416bcb3f6d48bd1c7f101b95
ms.sourcegitcommit: 2ad7d06f4f469b5d8a5280ac0e0289a81867fc8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2018
ms.locfileid: "35231434"
---
# <a name="-target-visual-basic"></a>-target (Visual Basic)
Určuje formát výstupu kompilátoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-target:{exe | library | module | winexe | appcontainerexe | winmdobj}  
```  
  
## <a name="remarks"></a>Poznámky  
 Následující tabulka shrnuje účinku `-target` možnost.  
  
|**Možnost**|**Chování**|  
|----------------|------------------|  
|`-target:exe`|Způsobí, že kompilátor vytvoření aplikace konzoly spustitelný soubor.<br /><br /> Toto je výchozí možnost, pokud žádné `-target` je zadána možnost. Spustitelný soubor je vytvořen s příponou .exe.<br /><br /> Pokud není uvedeno jinak s `/out` možnost, název výstupního souboru využívá název souboru vstupního souboru, který obsahuje `Sub Main` postupu.<br /><br /> Pouze jeden `Sub Main` postup je požadován v soubory zdrojového kódu, které jsou zkompilovány do souboru s příponou .exe. Použití `-main` – možnost kompilátoru k určení, která třída obsahuje `Sub Main` postupu.|  
|`-target:library`|Způsobí, že kompilátor vytvořit dynamická knihovna (DLL).<br /><br /> Soubor knihovny DLL je vytvořen s příponou .dll.<br /><br /> Pokud není uvedeno jinak s `-out` možnost, název výstupního souboru využívá název prvního vstupního souboru.<br /><br /> Při vytváření knihovny DLL, `Sub Main` postup není nutný.|  
|`-target:module`|Způsobí, že kompilátor generovat modul, který lze přidat do sestavení.<br /><br /> Výstupní soubor je vytvořen s příponou .netmodule.<br /><br /> Modul common language runtime rozhraní .NET nelze načíst soubor, který nemá sestavení. Takový soubor je však můžete začlenit do manifestu sestavení pomocí `-reference`.<br /><br /> Pokud kód jednoho modulu odkazuje na vnitřní typy v jiný modul, i moduly musí být součástí manifest sestavení pomocí `-reference`.<br /><br /> [- Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) možnost Importuje metadata z modulu.|  
|`-target:winexe`|Způsobí, že kompilátor vytvoření spustitelného souboru aplikace systému Windows.<br /><br /> Spustitelný soubor je vytvořen s příponou .exe. Aplikace systému Windows je ten, který poskytuje uživatelské rozhraní z buď [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] knihovny tříd nebo s rozhraními API Win32.<br /><br /> Pokud není uvedeno jinak s `-out` možnost, název výstupního souboru využívá název souboru vstupního souboru, který obsahuje `Sub Main` postupu.<br /><br /> Pouze jeden `Sub Main` postup je požadován v soubory zdrojového kódu, které jsou zkompilovány do souboru s příponou .exe. V případech, kdy váš kód obsahuje více než jednu třídu, která má `Sub Main` postup, použijte `-main` – možnost kompilátoru k určení, která třída obsahuje `Sub Main` postup|  
|`-target:appcontainerexe`|Způsobí, že kompilátor vytvářet spustitelná aplikace systému Windows, který se musí spustit v kontejnerem aplikace. Toto nastavení je určen k použití pro [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] aplikace.<br /><br /> **Appcontainerexe** nastavení nastaví trochu v poli vlastnosti [přenosné spustitelný soubor](https://msdn.microsoft.com/library/windows/desktop/ms680547(v=vs.85).aspx?id=19509) souboru. Tento bit určuje, že musí být aplikace spuštěna v kontejnerem aplikace. Pokud je tento bit nastavená, pokud dojde k chybě `CreateProcess` metoda pokusí o spuštění aplikace mimo kontejnerem aplikace. Kromě zajištění dostatečného toto bit nastavení **-target: appcontainerexe** je ekvivalentní **-target: winexe**.<br /><br /> Spustitelný soubor je vytvořen s příponou .exe.<br /><br /> Pokud neurčíte jinak pomocí `-out` možnost, název výstupního souboru využívá název souboru vstupního souboru, který obsahuje `Sub Main` postupu.<br /><br /> Pouze jeden `Sub Main` postup je požadován v soubory zdrojového kódu, které jsou zkompilovány do souboru s příponou .exe. Pokud váš kód obsahuje více než jednu třídu, která má `Sub Main` postup, použijte `-main` – možnost kompilátoru k určení, která třída obsahuje `Sub Main` postup|  
|`-target:winmdobj`|Způsobí, že kompilátor vytvořit pomocný soubor, který můžete převést do prostředí Windows Runtime binárního souboru (.winmd) souboru. Soubor .winmd mohou být spotřebovávána JavaScript a C++ programy, kromě spravované jazyk programy.<br /><br /> Pomocný soubor je vytvořen s příponou .winmdobj.<br /><br /> Pokud neurčíte jinak pomocí `-out` možnost, název výstupního souboru využívá název prvního vstupního souboru. A `Sub Main` postup není povinné.<br /><br /> Soubor .winmdobj je určen k použití jako vstup pro <xref:Microsoft.Build.Tasks.WinMDExp> exportovat nástroj k vytvoření souboru metadat (WinMD) systému Windows. WinMD soubor s příponou .winmd a obsahuje i kód z původní knihovna a definice WinMD tohoto jazyka JavaScript, C++ a použití prostředí Windows Runtime.|  
  
 Pokud nezadáte `-target:module`, `-target` způsobí, že [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] manifest sestavení, které mají být přidány do výstupního souboru.  
  
 Každá instance Vbc.exe vytvořil, maximálně jednu výstupní soubor. Pokud například zadáte možnost kompilátoru `-out` nebo `-target` více než jednou, naposledy procesy kompilátoru uvedeno v platnost. Informace o všechny soubory v kompilaci se přidá k manifestu. Všechny soubory kromě těch vytvořené pomocí výstup `-target:module` obsahovat metadata sestavení v manifestu. Použití [Ildasm.exe (IL Disassembler)](https://msdn.microsoft.com/library/f7dy01k1) zobrazíte metadata ve výstupním souboru.  
  
 Zkratka pro `-target` je `-t`.  
  
### <a name="to-set--target-in-the-visual-studio-ide"></a>Chcete-li nastavit - target v prostředí Visual Studio IDE  
  
1.  Máte projekt vybraný v **Průzkumníku řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.   
  
2.  Klikněte **aplikace** kartě.  
  
3.  Změňte hodnotu v **typ aplikace** pole.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `in.vb`, vytváření `in.dll`:  
  
```console
vbc -target:library in.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-main](../../../visual-basic/reference/command-line-compiler/main.md)  
 [-out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)  
 [-reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)  
 [-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)  
 [Sestavení a globální mezipaměť sestavení (GAC)](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
