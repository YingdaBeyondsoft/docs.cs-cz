---
title: "Příklady syntaxe dotazů metoda: Operátory převodu (LINQ na DataSet)"
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
ms.assetid: a084c16b-9b55-4690-aefd-f8e0810a92c3
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 65f583bf7aaa223107d9ae23ede8660d2b6804ea
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="method-based-query-syntax-examples-conversion-operators-linq-to-dataset"></a><span data-ttu-id="2a635-102">Příklady syntaxe dotazů metoda: Operátory převodu (LINQ na DataSet)</span><span class="sxs-lookup"><span data-stu-id="2a635-102">Method-Based Query Syntax Examples: Conversion Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="2a635-103">V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A>, a <xref:System.Linq.Enumerable.ToList%2A> metody okamžitě provést výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="2a635-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A>, and <xref:System.Linq.Enumerable.ToList%2A> methods to immediately execute a query expression.</span></span>  
  
 <span data-ttu-id="2a635-104">`FillDataSet` Metodu použitou v těchto příkladech je uveden v [načítání dat do datové sady](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="2a635-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="2a635-105">V příkladech v tomto tématu použijte kontaktu, adresu, produktu, SalesOrderHeader a podrobnosti prodejní objednávky tabulky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="2a635-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="2a635-106">V příkladech v tomto tématu použijte následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="2a635-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="2a635-107">Další informace najdete v tématu [postupy: vytvoření LINQ na DataSet projekt v sadě Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="2a635-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="toarray"></a><span data-ttu-id="2a635-108">ToArray</span><span class="sxs-lookup"><span data-stu-id="2a635-108">ToArray</span></span>  
  
### <a name="example"></a><span data-ttu-id="2a635-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="2a635-109">Example</span></span>  
 <span data-ttu-id="2a635-110">Tento příklad používá <xref:System.Linq.Enumerable.ToArray%2A> metoda okamžitě vyhodnotit posloupnost do pole.</span><span class="sxs-lookup"><span data-stu-id="2a635-110">This example uses the <xref:System.Linq.Enumerable.ToArray%2A> method to immediately evaluate a sequence into an array.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToArray](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#toarray)]
 [!code-vb[DP LINQ to DataSet Examples#ToArray](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#toarray)]  
  
## <a name="todictionary"></a><span data-ttu-id="2a635-111">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="2a635-111">ToDictionary</span></span>  
  
### <a name="example"></a><span data-ttu-id="2a635-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="2a635-112">Example</span></span>  
 <span data-ttu-id="2a635-113">Tento příklad používá <xref:System.Linq.Enumerable.ToDictionary%2A> metoda okamžitě vyhodnocení sekvenci a související výrazu klíče do slovníku.</span><span class="sxs-lookup"><span data-stu-id="2a635-113">This example uses the <xref:System.Linq.Enumerable.ToDictionary%2A> method to immediately evaluate a sequence and a related key expression into a dictionary.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToDictionary](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#todictionary)]
 [!code-vb[DP LINQ to DataSet Examples#ToDictionary](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#todictionary)]  
  
## <a name="tolist"></a><span data-ttu-id="2a635-114">ToList</span><span class="sxs-lookup"><span data-stu-id="2a635-114">ToList</span></span>  
  
### <a name="example"></a><span data-ttu-id="2a635-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="2a635-115">Example</span></span>  
 <span data-ttu-id="2a635-116">Tento příklad používá <xref:System.Linq.Enumerable.ToList%2A> metoda okamžitě vyhodnotit pořadí do <xref:System.Collections.Generic.List%601>, kde `T` je typu <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="2a635-116">This example uses the <xref:System.Linq.Enumerable.ToList%2A> method to immediately evaluate a sequence into a <xref:System.Collections.Generic.List%601>, where `T` is of type <xref:System.Data.DataRow>.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToList](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#tolist)]
 [!code-vb[DP LINQ to DataSet Examples#ToList](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#tolist)]  
  
## <a name="see-also"></a><span data-ttu-id="2a635-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="2a635-117">See Also</span></span>  
 [<span data-ttu-id="2a635-118">Načítání dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="2a635-118">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="2a635-119">LINQ na DataSet příklady</span><span class="sxs-lookup"><span data-stu-id="2a635-119">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="2a635-120">Přehled standardních operátorů dotazu</span><span class="sxs-lookup"><span data-stu-id="2a635-120">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)