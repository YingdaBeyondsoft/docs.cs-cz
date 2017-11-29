---
title: "Prvky skupiny v pořadí"
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
ms.assetid: 1d50c8b4-f550-4775-bbb6-eab6e874cb43
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9a398bb7b951fcf2dd2449b6468a19d39a134a4a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="group-elements-in-a-sequence"></a><span data-ttu-id="d75ce-102">Prvky skupiny v pořadí</span><span class="sxs-lookup"><span data-stu-id="d75ce-102">Group Elements in a Sequence</span></span>
<span data-ttu-id="d75ce-103"><xref:System.Linq.Enumerable.GroupBy%2A> Operátor skupiny elementy pořadí.</span><span class="sxs-lookup"><span data-stu-id="d75ce-103">The <xref:System.Linq.Enumerable.GroupBy%2A> operator groups the elements of a sequence.</span></span> <span data-ttu-id="d75ce-104">Následující příklady použít databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="d75ce-104">The following examples use the Northwind database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d75ce-105">Hodnota Null, hodnot sloupce v <xref:System.Linq.Enumerable.GroupBy%2A> dotazy můžete někdy throw <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="d75ce-105">Null column values in <xref:System.Linq.Enumerable.GroupBy%2A> queries can sometimes throw an <xref:System.InvalidOperationException>.</span></span> <span data-ttu-id="d75ce-106">Další informace najdete v části "GroupBy InvalidOperationException" [Poradce při potížích s](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="d75ce-106">For more information, see the "GroupBy InvalidOperationException" section of [Troubleshooting](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d75ce-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="d75ce-107">Example</span></span>  
 <span data-ttu-id="d75ce-108">Následující příklad oddíly `Products` podle `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="d75ce-108">The following example partitions `Products` by `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#27](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#27)]
 [!code-vb[DLinqQueryExamples#27](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#27)]  
  
## <a name="example"></a><span data-ttu-id="d75ce-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="d75ce-109">Example</span></span>  
 <span data-ttu-id="d75ce-110">Následující příklad používá <xref:System.Linq.Enumerable.Max%2A> najít maximální jednotkové ceny pro každou `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="d75ce-110">The following example uses <xref:System.Linq.Enumerable.Max%2A> to find the maximum unit price for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#28](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#28)]
 [!code-vb[DLinqQueryExamples#28](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#28)]  
  
## <a name="example"></a><span data-ttu-id="d75ce-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="d75ce-111">Example</span></span>  
 <span data-ttu-id="d75ce-112">Následující příklad používá k nalezení průměr průměr `UnitPrice` pro každou `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="d75ce-112">The following example uses Average to find the average `UnitPrice` for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#29](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#29)]
 [!code-vb[DLinqQueryExamples#29](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="d75ce-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="d75ce-113">Example</span></span>  
 <span data-ttu-id="d75ce-114">Následující příklad používá <xref:System.Linq.Queryable.Sum%2A> najít celkový počet `UnitPrice` pro každou `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="d75ce-114">The following example uses <xref:System.Linq.Queryable.Sum%2A> to find the total `UnitPrice` for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#30](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#30)]
 [!code-vb[DLinqQueryExamples#30](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="d75ce-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="d75ce-115">Example</span></span>  
 <span data-ttu-id="d75ce-116">Následující příklad používá <xref:System.Linq.Queryable.Count%2A> najít počet zastaví `Products` v každé `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="d75ce-116">The following example uses <xref:System.Linq.Queryable.Count%2A> to find the number of discontinued `Products` in each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#31](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#31)]
 [!code-vb[DLinqQueryExamples#31](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#31)]  
  
## <a name="example"></a><span data-ttu-id="d75ce-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="d75ce-117">Example</span></span>  
 <span data-ttu-id="d75ce-118">Následující příklad používá následující `where` klauzule najít všechny kategorie, které má alespoň 10 produkty.</span><span class="sxs-lookup"><span data-stu-id="d75ce-118">The following example uses a following `where` clause to find all categories that have at least 10 products.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#32](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#32)]
 [!code-vb[DLinqQueryExamples#32](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#32)]  
  
## <a name="example"></a><span data-ttu-id="d75ce-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="d75ce-119">Example</span></span>  
 <span data-ttu-id="d75ce-120">Následující příklad skupiny produkty od `CategoryID` a `SupplierID`.</span><span class="sxs-lookup"><span data-stu-id="d75ce-120">The following example groups products by `CategoryID` and `SupplierID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#33](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#33)]
 [!code-vb[DLinqQueryExamples#33](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#33)]  
  
## <a name="example"></a><span data-ttu-id="d75ce-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="d75ce-121">Example</span></span>  
 <span data-ttu-id="d75ce-122">Následující příklad vrátí dvě pořadí produktů.</span><span class="sxs-lookup"><span data-stu-id="d75ce-122">The following example returns two sequences of products.</span></span> <span data-ttu-id="d75ce-123">První pořadí obsahuje produkty s jednotkové ceny menší než nebo rovna 10.</span><span class="sxs-lookup"><span data-stu-id="d75ce-123">The first sequence contains products with unit price less than or equal to 10.</span></span> <span data-ttu-id="d75ce-124">Druhé pořadí obsahuje produkty s jednotkové ceny, které jsou větší než 10.</span><span class="sxs-lookup"><span data-stu-id="d75ce-124">The second sequence contains products with unit price greater than 10.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#34](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#34)]
 [!code-vb[DLinqQueryExamples#34](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#34)]  
  
## <a name="example"></a><span data-ttu-id="d75ce-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="d75ce-125">Example</span></span>  
 <span data-ttu-id="d75ce-126"><xref:System.Linq.Queryable.GroupBy%2A> Operátor může trvat jenom jeden argument klíče.</span><span class="sxs-lookup"><span data-stu-id="d75ce-126">The <xref:System.Linq.Queryable.GroupBy%2A> operator can take only a single key argument.</span></span> <span data-ttu-id="d75ce-127">Pokud potřebujete seskupit více než jeden klíč, je nutné vytvořit anonymní typ, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="d75ce-127">If you need to group by more than one key, you must create an anonymous type, as in the following example:</span></span>  
  
 [!code-csharp[DLinqQueryExamples#35](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#35)]
 [!code-vb[DLinqQueryExamples#35](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#35)]  
  
## <a name="see-also"></a><span data-ttu-id="d75ce-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="d75ce-128">See Also</span></span>  
 [<span data-ttu-id="d75ce-129">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="d75ce-129">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="d75ce-130">Stažení ukázkové databáze</span><span class="sxs-lookup"><span data-stu-id="d75ce-130">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)