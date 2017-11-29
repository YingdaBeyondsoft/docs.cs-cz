---
title: "Načítání dat do datové sady"
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
ms.assetid: a53e5dc1-9669-49d4-828d-efa633237066
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: afb05055d67a4430909a657fc0ee90c97d3ebfb0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="loading-data-into-a-dataset"></a><span data-ttu-id="31613-102">Načítání dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="31613-102">Loading Data Into a DataSet</span></span>
<span data-ttu-id="31613-103">A <xref:System.Data.DataSet> objekt musí být před můžete dotazovat přes její naplněn [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="31613-103">A <xref:System.Data.DataSet> object must first be populated before you can query over it with [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="31613-104">Existuje několik různých způsobů k naplnění <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="31613-104">There are several different ways to populate the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="31613-105">Například můžete použít [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] pro dotazování databáze a načte výsledky do <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="31613-105">For example, you can use [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] to query the database and load the results into the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="31613-106">Další informace najdete v tématu [technologie LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="31613-106">For more information, see [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).</span></span>  
  
 <span data-ttu-id="31613-107">Další běžné způsob, jak načíst data do <xref:System.Data.DataSet> je použití <xref:System.Data.Common.DataAdapter> třídy k načtení dat z databáze.</span><span class="sxs-lookup"><span data-stu-id="31613-107">Another common way to load data into a <xref:System.Data.DataSet> is to use the <xref:System.Data.Common.DataAdapter> class to retrieve data from the database.</span></span> <span data-ttu-id="31613-108">To je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="31613-108">This is illustrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31613-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="31613-109">Example</span></span>  
 <span data-ttu-id="31613-110">Tento příklad používá <xref:System.Data.Common.DataAdapter> dotazu databázi AdventureWorks prodeje informace z roku 2002 a načte výsledky do <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="31613-110">This example uses a <xref:System.Data.Common.DataAdapter> to query the AdventureWorks database for sales information from the year 2002, and loads the results into a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="31613-111">Po <xref:System.Data.DataSet> naplněné, můžete psát dotazy proti ho pomocí [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="31613-111">After the <xref:System.Data.DataSet> has been populated, you can write queries against it by using [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="31613-112">`FillDataSet` Metoda v tomto příkladu se používá v příkladů dotazů v [LINQ na DataSet příklady](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md).</span><span class="sxs-lookup"><span data-stu-id="31613-112">The `FillDataSet` method in this example is used in the example queries in [LINQ to DataSet Examples](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md).</span></span> <span data-ttu-id="31613-113">Další informace najdete v tématu [dotazování datové sady](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="31613-113">For more information, see [Querying DataSets](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md).</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a><span data-ttu-id="31613-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="31613-114">See Also</span></span>  
 [<span data-ttu-id="31613-115">LINQ na DataSet přehled</span><span class="sxs-lookup"><span data-stu-id="31613-115">LINQ to DataSet Overview</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-overview.md)  
 [<span data-ttu-id="31613-116">Dotazování datové sady</span><span class="sxs-lookup"><span data-stu-id="31613-116">Querying DataSets</span></span>](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [<span data-ttu-id="31613-117">LINQ na DataSet příklady</span><span class="sxs-lookup"><span data-stu-id="31613-117">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)