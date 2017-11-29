---
title: "Postupy: Zobrazení obsahu globální mezipaměti sestavení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, viewing contents
- viewing assemblies in global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- GAC (global assembly cache), viewing contents
- list of assemblies in global assembly cache
- Global Assembly Cache tool
ms.assetid: c5f786a0-969b-4f14-9f02-e77c3384d9af
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: db5714c6669ac5fbdfd81656aa7659fdde05922a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a><span data-ttu-id="9e0c1-102">Postupy: Zobrazení obsahu globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="9e0c1-102">How to: View the Contents of the Global Assembly Cache</span></span>
<span data-ttu-id="9e0c1-103">Použití [nástroj globální mezipaměti sestavení (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) zobrazení obsahu globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="9e0c1-103">Use the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to view the contents of the global assembly cache.</span></span>  
  
### <a name="to-view-a-list-of-the-assemblies-in-the-global-assembly-cache"></a><span data-ttu-id="9e0c1-104">Chcete-li zobrazit seznam sestavení v globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="9e0c1-104">To view a list of the assemblies in the global assembly cache</span></span>  
  
1.  <span data-ttu-id="9e0c1-105">Na [příkazového řádku Visual Studia](../../../docs/framework/tools/developer-command-prompt-for-vs.md), zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="9e0c1-105">At the [Visual Studio command prompt](../../../docs/framework/tools/developer-command-prompt-for-vs.md), type the following command:</span></span>  
  
     <span data-ttu-id="9e0c1-106">**Gacutil -l** </span><span class="sxs-lookup"><span data-stu-id="9e0c1-106">**gacutil -l** </span></span>  
     <span data-ttu-id="9e0c1-107">-nebo-</span><span class="sxs-lookup"><span data-stu-id="9e0c1-107">-or-</span></span>  
    <span data-ttu-id="9e0c1-108">**Gacutil /l**</span><span class="sxs-lookup"><span data-stu-id="9e0c1-108">**gacutil /l**</span></span>  
  
 <span data-ttu-id="9e0c1-109">V dřívějších verzích rozhraní .NET Framework [Shfusion.dll](http://msdn.microsoft.com/en-us/0d9464cf-ddba-4ca9-bbec-f678fb58f380) rozšíření prostředí systému Windows umožňuje zobrazit v Průzkumníku souborů do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="9e0c1-109">In earlier versions of the .NET Framework, the [Shfusion.dll](http://msdn.microsoft.com/en-us/0d9464cf-ddba-4ca9-bbec-f678fb58f380) Windows shell extension enabled you to view the global assembly cache in File Explorer.</span></span> <span data-ttu-id="9e0c1-110">Od verze [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll je zastaralý.</span><span class="sxs-lookup"><span data-stu-id="9e0c1-110">Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll is obsolete.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e0c1-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e0c1-111">See Also</span></span>  
 [<span data-ttu-id="9e0c1-112">Práce se sestaveními a globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="9e0c1-112">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="9e0c1-113">Gacutil.exe (nástroj globální mezipaměti sestavení)</span><span class="sxs-lookup"><span data-stu-id="9e0c1-113">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)