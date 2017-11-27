---
title: "-target: appcontainerexe (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9ab407f14483bbb5abaf3dc23b0cf204091b74ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="targetappcontainerexe-c-compiler-options"></a><span data-ttu-id="b8dbd-102">/target:appcontainerexe (Možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="b8dbd-102">/target:appcontainerexe (C# Compiler Options)</span></span>
<span data-ttu-id="b8dbd-103">Pokud použijete **/target: appcontainerexe** – možnost kompilátoru, kompilátor vytvoří spustitelný soubor (.exe) soubor systému Windows, který musí být spuštěn v kontejnerem aplikace.</span><span class="sxs-lookup"><span data-stu-id="b8dbd-103">If you use the **/target:appcontainerexe** compiler option, the compiler creates a Windows executable (.exe) file that must be run in an app container.</span></span> <span data-ttu-id="b8dbd-104">Tato možnost je ekvivalentní [/target: winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) , ale je určená pro [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="b8dbd-104">This option is equivalent to [/target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) but is designed for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] apps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8dbd-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8dbd-105">Syntax</span></span>  
  
```console  
/target:appcontainerexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="b8dbd-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b8dbd-106">Remarks</span></span>  
 <span data-ttu-id="b8dbd-107">Pokud chcete vyžadovat aplikaci spustit v kontejnerem aplikace, tento parametr nastaví trochu v [přenosné spustitelný soubor](http://go.microsoft.com/fwlink/p/?LinkId=236960) souboru (PE).</span><span class="sxs-lookup"><span data-stu-id="b8dbd-107">To require the app to run in an app container, this option sets a bit in the [Portable Executable](http://go.microsoft.com/fwlink/p/?LinkId=236960) (PE) file.</span></span> <span data-ttu-id="b8dbd-108">Pokud je nastaven daný bit, dojde k chybě, pokud se pokusí spustit spustitelný soubor mimo kontejnerem aplikace CreateProcess – metoda.</span><span class="sxs-lookup"><span data-stu-id="b8dbd-108">When that bit is set, an error occurs if the CreateProcess method tries to launch the executable file outside an app container.</span></span>  
  
 <span data-ttu-id="b8dbd-109">Pokud nechcete použít [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) možnost, název výstupního souboru využívá název souboru vstupního souboru, který obsahuje [hlavní](../../../csharp/programming-guide/main-and-command-args/index.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="b8dbd-109">Unless you use the [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="b8dbd-110">Pokud tuto možnost na příkazovém řádku zadáte, všechny soubory až do dalšího **/out** nebo **/target** možnost slouží k vytváření spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="b8dbd-110">When you specify this option at a command prompt, all files until the next **/out** or **/target** option are used to create the executable file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a><span data-ttu-id="b8dbd-111">Nastavení této možnosti kompilátoru v integrovaném vývojovém prostředí</span><span class="sxs-lookup"><span data-stu-id="b8dbd-111">To set this compiler option in the IDE</span></span>  
  
1.  <span data-ttu-id="b8dbd-112">V **Průzkumníku řešení**, otevřete místní nabídku pro svůj projekt a potom zvolte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="b8dbd-112">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="b8dbd-113">Na **aplikace** ve **výstupní typ** vyberte **aplikace pro Windows Store**.</span><span class="sxs-lookup"><span data-stu-id="b8dbd-113">On the **Application** tab, in the **Output type** list, choose **Windows Store App**.</span></span>  
  
     <span data-ttu-id="b8dbd-114">Tato možnost je dostupná pouze pro [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] šablony aplikace.</span><span class="sxs-lookup"><span data-stu-id="b8dbd-114">This option is available only for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] app templates.</span></span>  
  
 <span data-ttu-id="b8dbd-115">Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="b8dbd-115">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8dbd-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="b8dbd-116">Example</span></span>  
 <span data-ttu-id="b8dbd-117">Následující příkaz zkompiluje `filename.cs` do Windows spustitelný soubor, který lze spustit pouze v kontejnerem aplikace.</span><span class="sxs-lookup"><span data-stu-id="b8dbd-117">The following command compiles `filename.cs` into a Windows executable file that can be run only in an app container.</span></span>  
  
```console  
csc /target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="b8dbd-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="b8dbd-118">See Also</span></span>  
 [<span data-ttu-id="b8dbd-119">/ target (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="b8dbd-119">/target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [<span data-ttu-id="b8dbd-120">/ target: winexe (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="b8dbd-120">/target:winexe (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
 [<span data-ttu-id="b8dbd-121">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="b8dbd-121">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)