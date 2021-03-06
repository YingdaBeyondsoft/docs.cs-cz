---
title: '-target: winmdobj (možnosti kompilátoru C#)'
ms.date: 07/20/2015
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
ms.openlocfilehash: b0b1ec0bed174484e9ed7b9ecddbe82b0c705325
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218655"
---
# <a name="-targetwinmdobj-c-compiler-options"></a>-target: winmdobj (možnosti kompilátoru C#)
Pokud použijete **-target: winmdobj** – možnost kompilátoru, kompilátor vytvoří zprostředkující .winmdobj soubor, který můžete převést do prostředí Windows Runtime binárního souboru (.winmd) souboru. Soubor .winmd mohou být spotřebovávána pak JavaScript a C++ programy, kromě spravované jazyk programy.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-target:winmdobj  
```  
  
## <a name="remarks"></a>Poznámky  
 **Winmdobj** nastavení signály pro kompilátor, že modul zprostředkující je vyžadována. Visual Studio v odpovědi, zkompiluje jako soubor .winmdobj knihovny tříd jazyka C#. Soubor .winmdobj můžete pak dodáni prostřednictvím <xref:Microsoft.Build.Tasks.WinMDExp> exportovat nástroj k vytvoření souboru metadat (.winmd) systému Windows. Soubor .winmd obsahuje kód z původní knihovna a WinMD metadata, která se používá JavaScript nebo C++ a prostředí Windows Runtime.  
  
 Výstup tohoto souboru, který se zkompiluje pomocí **-target: winmdobj** – možnost kompilátoru je určen k použití pouze jako vstup pro nástroj pro export WimMDExp; samotný soubor .winmdobj neodkazuje přímo.  
  
 Pokud nechcete použít [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) možnost, název výstupního souboru využívá název prvního vstupního souboru. A [hlavní](../../../csharp/programming-guide/main-and-command-args/index.md) metoda není povinné.  
  
 Pokud zadáte-target: winmdobj možnost příkazového řádku, všechny soubory, dokud Další **-out** nebo [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) možnost slouží k vytvoření programu systému Windows.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a>Nastavení této možnosti kompilátoru v integrovaném vývojovém prostředí sady Visual Studio pro aplikaci pro Windows Store  
  
1.  V **Průzkumníku řešení**, otevřete místní nabídku pro svůj projekt a potom zvolte **vlastnosti**.  
  
2.  Vyberte **aplikace** kartě.  
  
3.  V **výstupní typ** vyberte **souboru WinMD**.  
  
     **Souboru WinMD** možnost je dostupná pouze pro [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] šablony aplikace.  
  
 Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Příklad  
 Následující příkaz zkompiluje `filename.cs` do souboru zprostředkující .winmdobj.  
  
```console  
csc -target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a>Viz také  
 [-target (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)
