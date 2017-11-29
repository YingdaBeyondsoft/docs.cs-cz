---
title: "Odkaz byl vytvořen pro vložené sestavení vzájemné spolupráce & č. 39; &lt;assembly1&gt;& č. 39; z důvodu nepřímý odkaz na sestavení z sestavení & č. 39;&lt; assembly2&gt;& č. 39;"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40059
- bc40059
helpviewer_keywords:
- VBC40059
- BC40059
ms.assetid: 520e39cb-8ab6-46f5-aa00-08afd51b4b7c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bc2fbb044fc839aa24abf3dc1ea864457efb0653
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="a-reference-was-created-to-embedded-interop-assembly-39ltassembly1gt39-because-of-an-indirect-reference-to-that-assembly-from-assembly-39ltassembly2gt39"></a><span data-ttu-id="533ee-102">Odkaz byl vytvořen pro vložené sestavení vzájemné spolupráce & č. 39; &lt;assembly1&gt;& č. 39; z důvodu nepřímý odkaz na sestavení z sestavení & č. 39;&lt; assembly2&gt;& č. 39;</span><span class="sxs-lookup"><span data-stu-id="533ee-102">A reference was created to embedded interop assembly &#39;&lt;assembly1&gt;&#39; because of an indirect reference to that assembly from assembly &#39;&lt;assembly2&gt;&#39;</span></span>
<span data-ttu-id="533ee-103">Odkaz byl vytvořen pro vložené sestavení vzájemné spolupráce se\<assembly1 > se z důvodu nepřímý odkaz na sestavení ze sestavení '\<assembly2 >'.</span><span class="sxs-lookup"><span data-stu-id="533ee-103">A reference was created to embedded interop assembly '\<assembly1>' because of an indirect reference to that assembly from assembly '\<assembly2>'.</span></span> <span data-ttu-id="533ee-104">Zvažte změnu vlastnost vložit zprostředkovatel komunikace s objekty typy v jednom ze sestavení.</span><span class="sxs-lookup"><span data-stu-id="533ee-104">Consider changing the 'Embed Interop Types' property on either assembly.</span></span>  
  
 <span data-ttu-id="533ee-105">Přidáte odkaz na sestavení (assembly1), který má `Embed Interop Types` vlastnost nastavena na hodnotu `True`.</span><span class="sxs-lookup"><span data-stu-id="533ee-105">You have added a reference to an assembly (assembly1) that has the `Embed Interop Types` property set to `True`.</span></span> <span data-ttu-id="533ee-106">To dává pokyn kompilátoru pro vložení informací o zprostředkovatele komunikace s objekty typu z tohoto sestavení.</span><span class="sxs-lookup"><span data-stu-id="533ee-106">This instructs the compiler to embed interop type information from that assembly.</span></span> <span data-ttu-id="533ee-107">Kompilátor však nemůže vložit spolupráce typ informace z tohoto sestavení, protože jiné sestavení, které se vám (assembly2) také odkazuje dané sestavení (assembly1) a má `Embed Interop Types` vlastnost nastavena na hodnotu `False`.</span><span class="sxs-lookup"><span data-stu-id="533ee-107">However, the compiler cannot embed interop type information from that assembly because another assembly that you have referenced (assembly2) also references that assembly (assembly1) and has the `Embed Interop Types` property set to `False`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="533ee-108">Nastavení `Embed Interop Types` vlastnost na odkaz na sestavení pro `True` je ekvivalentní k odkazování na sestavení s použitím `/link` – možnost kompilátoru příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="533ee-108">Setting the `Embed Interop Types` property on an assembly reference to `True` is equivalent to referencing the assembly by using the `/link` option for the command-line compiler.</span></span>  
  
 <span data-ttu-id="533ee-109">**ID chyby:** BC40059</span><span class="sxs-lookup"><span data-stu-id="533ee-109">**Error ID:** BC40059</span></span>  
  
### <a name="to-address-this-warning"></a><span data-ttu-id="533ee-110">Pro vyřešení tohoto upozornění</span><span class="sxs-lookup"><span data-stu-id="533ee-110">To address this warning</span></span>  
  
-   <span data-ttu-id="533ee-111">Chcete-li vložit informace zprostředkovatele komunikace s objekty typu u obou sestavení, nastavte `Embed Interop Types` vlastnost na všechny odkazy na assembly1 na `True`.</span><span class="sxs-lookup"><span data-stu-id="533ee-111">To embed interop type information for both assemblies, set the `Embed Interop Types` property on all references to assembly1 to `True`.</span></span>  
  
-   <span data-ttu-id="533ee-112">Chcete-li odebrat upozornění, můžete nastavit `Embed Interop Types` vlastnost assembly1 na `False`.</span><span class="sxs-lookup"><span data-stu-id="533ee-112">To remove the warning, you can set the `Embed Interop Types` property of assembly1 to `False`.</span></span> <span data-ttu-id="533ee-113">V takovém případě zprostředkovatele komunikace s objekty typu informace jsou poskytovány primární spolupracující sestavení (PIA).</span><span class="sxs-lookup"><span data-stu-id="533ee-113">In this case, interop type information is provided by a primary interop assembly (PIA).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="533ee-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="533ee-114">See Also</span></span>  
 [<span data-ttu-id="533ee-115">/ Link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="533ee-115">/link (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/link.md)  
 [<span data-ttu-id="533ee-116">Programování s primární spolupráce – sestavení</span><span class="sxs-lookup"><span data-stu-id="533ee-116">Programming with Primary Interop Assemblies</span></span>](http://msdn.microsoft.com/en-us/306fa1d6-0703-4004-9e93-d0a57f1be81e)