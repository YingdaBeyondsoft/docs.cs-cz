---
title: "Postupy: Zadejte, když nastanou výjimky souběžnosti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 344ae068-ff63-4a2e-8b00-af22e143675f
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8af833574544410977b9f881f9b2db4e6d88aa73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-when-concurrency-exceptions-are-thrown"></a><span data-ttu-id="4b176-102">Postupy: Zadejte, když nastanou výjimky souběžnosti</span><span class="sxs-lookup"><span data-stu-id="4b176-102">How to: Specify When Concurrency Exceptions are Thrown</span></span>
<span data-ttu-id="4b176-103">V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Data.Linq.ChangeConflictException> při objekty nelze aktualizovat z důvodu konfliktu optimistickou metodu souběžného je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="4b176-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when objects do not update because of optimistic concurrency conflicts.</span></span> <span data-ttu-id="4b176-104">Další informace najdete v tématu [optimistickou metodu souběžného: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="4b176-104">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
 <span data-ttu-id="4b176-105">Před odesláním změny do databáze, můžete zadat, když by měl být vyvolány souběžného zpracování výjimky:</span><span class="sxs-lookup"><span data-stu-id="4b176-105">Before you submit your changes to the database, you can specify when concurrency exceptions should be thrown:</span></span>  
  
-   <span data-ttu-id="4b176-106">Throw – výjimka v prvním selhání (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).</span><span class="sxs-lookup"><span data-stu-id="4b176-106">Throw the exception at the first failure (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).</span></span>  
  
-   <span data-ttu-id="4b176-107">Dokončit všechny aktualizace pokusů hromadit všechny chyby a sestavy Akumulovaná selhání v výjimce (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).</span><span class="sxs-lookup"><span data-stu-id="4b176-107">Finish all update tries, accumulate all failures, and report the accumulated failures in the exception (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).</span></span>  
  
 <span data-ttu-id="4b176-108">Při vyvolání, <xref:System.Data.Linq.ChangeConflictException> výjimka poskytuje přístup k <xref:System.Data.Linq.ChangeConflictCollection> kolekce.</span><span class="sxs-lookup"><span data-stu-id="4b176-108">When thrown, the <xref:System.Data.Linq.ChangeConflictException> exception provides access to a <xref:System.Data.Linq.ChangeConflictCollection> collection.</span></span> <span data-ttu-id="4b176-109">Tato kolekce obsahuje podrobné informace pro každý konflikt (namapované na zkuste jeden Chyba aktualizace), včetně přístupu ke <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="4b176-109">This collection provides details for each conflict (mapped to a single failed update try), including access to the <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> collection.</span></span> <span data-ttu-id="4b176-110">Každý člen konflikt mapuje jednoho člena v aktualizaci, která se nezdařila kontrola souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="4b176-110">Each member conflict maps to a single member in the update that failed the concurrency check.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b176-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="4b176-111">Example</span></span>  
 <span data-ttu-id="4b176-112">Následující kód ukazuje příklady obě hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4b176-112">The following code shows examples of both values.</span></span>  
  
 [!code-csharp[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="4b176-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="4b176-113">See Also</span></span>  
 [<span data-ttu-id="4b176-114">Postupy: Správa je v konfliktu změn</span><span class="sxs-lookup"><span data-stu-id="4b176-114">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [<span data-ttu-id="4b176-115">Vytvoření a odeslání změn dat</span><span class="sxs-lookup"><span data-stu-id="4b176-115">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)