---
title: "Postupy: Určení, zda je zablokovatelné zablokováno"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: Freezable objects [WPF], determining if frozen
ms.assetid: 92e58baa-ee12-4a9e-ac3a-ca458807a8b2
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 47fb0a871c3792450386c440629ead1ee3fbecdf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-whether-a-freezable-is-frozen"></a><span data-ttu-id="2ba24-102">Postupy: Určení, zda je zablokovatelné zablokováno</span><span class="sxs-lookup"><span data-stu-id="2ba24-102">How to: Determine Whether a Freezable Is Frozen</span></span>
<span data-ttu-id="2ba24-103">Tento příklad ukazuje, jak zjistit, jestli <xref:System.Windows.Freezable> objekt nereaguje.</span><span class="sxs-lookup"><span data-stu-id="2ba24-103">This example shows how to determine whether a <xref:System.Windows.Freezable> object is frozen.</span></span> <span data-ttu-id="2ba24-104">Pokud se pokusíte změnit ukotvené <xref:System.Windows.Freezable> objektu, vyvolá <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="2ba24-104">If you try to modify a frozen <xref:System.Windows.Freezable> object, it throws an <xref:System.InvalidOperationException>.</span></span> <span data-ttu-id="2ba24-105">Abyste se vyhnuli vyvolání výjimku, použijte <xref:System.Windows.Freezable.IsFrozen%2A> vlastnost <xref:System.Windows.Freezable> objektem pro určení, zda je pozastaveny.</span><span class="sxs-lookup"><span data-stu-id="2ba24-105">To avoid throwing this exception, use the <xref:System.Windows.Freezable.IsFrozen%2A> property of the <xref:System.Windows.Freezable> object to determine whether it is frozen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ba24-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="2ba24-106">Example</span></span>  
 <span data-ttu-id="2ba24-107">V následujícím příkladu se zablokuje <xref:System.Windows.Media.SolidColorBrush> a pak ho testů pomocí <xref:System.Windows.Freezable.IsFrozen%2A> vlastnosti k určení, zda je pozastaveny.</span><span class="sxs-lookup"><span data-stu-id="2ba24-107">The following example freezes a <xref:System.Windows.Media.SolidColorBrush> and then tests it by using the <xref:System.Windows.Freezable.IsFrozen%2A> property to determine whether it is frozen.</span></span>  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 <span data-ttu-id="2ba24-108">Další informace o <xref:System.Windows.Freezable> objekty, najdete [zmrazitelné objekty – přehled](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2ba24-108">For more information about <xref:System.Windows.Freezable> objects, see the [Freezable Objects Overview](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ba24-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="2ba24-109">See Also</span></span>  
 <xref:System.Windows.Freezable>  
 <xref:System.Windows.Freezable.IsFrozen%2A>  
 [<span data-ttu-id="2ba24-110">Zmrazitelné objekty – přehled</span><span class="sxs-lookup"><span data-stu-id="2ba24-110">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [<span data-ttu-id="2ba24-111">Postupy: témata</span><span class="sxs-lookup"><span data-stu-id="2ba24-111">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)