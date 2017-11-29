---
title: "Vytváření DataTable z dotazu (LINQ na DataSet)"
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
ms.assetid: 1b97afeb-03f8-41e2-8eb3-58aff65f7d18
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 5be353d76f921edd730d46907096abe8a2a1188f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="creating-a-datatable-from-a-query-linq-to-dataset"></a><span data-ttu-id="861fd-102">Vytváření DataTable z dotazu (LINQ na DataSet)</span><span class="sxs-lookup"><span data-stu-id="861fd-102">Creating a DataTable From a Query (LINQ to DataSet)</span></span>
<span data-ttu-id="861fd-103">Datová vazba se běžně používá z <xref:System.Data.DataTable> objektu.</span><span class="sxs-lookup"><span data-stu-id="861fd-103">Data binding is a common use of <xref:System.Data.DataTable> object.</span></span> <span data-ttu-id="861fd-104"><xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metoda přebírá výsledky dotazu a zkopíruje data do <xref:System.Data.DataTable>, který pak může být použit pro datovou vazbu.</span><span class="sxs-lookup"><span data-stu-id="861fd-104">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method takes the results of a query and copies the data into a <xref:System.Data.DataTable>, which can then be used for data binding.</span></span> <span data-ttu-id="861fd-105">Pokud operace dat prováděly, nové <xref:System.Data.DataTable> je sloučen zpět do zdroje <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="861fd-105">When the data operations have been performed, the new <xref:System.Data.DataTable> is merged back into the source <xref:System.Data.DataTable>.</span></span>  
  
 <span data-ttu-id="861fd-106"><xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metoda používá následující postup k vytvoření <xref:System.Data.DataTable> z dotazu:</span><span class="sxs-lookup"><span data-stu-id="861fd-106">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method uses the following process to create a <xref:System.Data.DataTable> from a query:</span></span>  
  
1.  <span data-ttu-id="861fd-107"><xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metoda klony <xref:System.Data.DataTable> ze zdrojové tabulky ( <xref:System.Data.DataTable> objekt, který implementuje <xref:System.Linq.IQueryable%601> rozhraní).</span><span class="sxs-lookup"><span data-stu-id="861fd-107">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method clones a <xref:System.Data.DataTable> from the source table (a <xref:System.Data.DataTable> object that implements the <xref:System.Linq.IQueryable%601> interface).</span></span> <span data-ttu-id="861fd-108"><xref:System.Collections.IEnumerable> Zdroj je obvykle pochází z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] metoda nebo výraz dotazu.</span><span class="sxs-lookup"><span data-stu-id="861fd-108">The <xref:System.Collections.IEnumerable> source has generally originated from a [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] expression or method query.</span></span>  
  
2.  <span data-ttu-id="861fd-109">Schéma klonované <xref:System.Data.DataTable> je sestaven z prvního sloupce ve výčtu <xref:System.Data.DataRow> objekt ve zdrojové tabulky a název klonovaného tabulky je název zdrojové tabulky slovem "dotaz" k němu připojen.</span><span class="sxs-lookup"><span data-stu-id="861fd-109">The schema of the cloned <xref:System.Data.DataTable> is built from the columns of the first enumerated <xref:System.Data.DataRow> object in the source table and the name of the cloned table is the name of the source table with the word "query" appended to it.</span></span>  
  
3.  <span data-ttu-id="861fd-110">Pro každý řádek ve zdrojové tabulce obsah řádek zkopírován do nového <xref:System.Data.DataRow> objekt, který se pak vloží do klonovaný tabulky.</span><span class="sxs-lookup"><span data-stu-id="861fd-110">For each row in the source table, the content of the row is copied into a new <xref:System.Data.DataRow> object, which is then inserted into the cloned table.</span></span> <span data-ttu-id="861fd-111"><xref:System.Data.DataRow.RowState%2A> a <xref:System.Data.DataRow.RowError%2A> vlastnosti jsou zachovány v operaci kopírování.</span><span class="sxs-lookup"><span data-stu-id="861fd-111">The <xref:System.Data.DataRow.RowState%2A> and <xref:System.Data.DataRow.RowError%2A> properties are preserved across the copy operation.</span></span> <span data-ttu-id="861fd-112"><xref:System.ArgumentException> Je vyvolána, pokud <xref:System.Data.DataRow> objekty ve zdroji jsou z různých tabulek.</span><span class="sxs-lookup"><span data-stu-id="861fd-112">An <xref:System.ArgumentException> is thrown if the <xref:System.Data.DataRow> objects in the source are from different tables.</span></span>  
  
4.  <span data-ttu-id="861fd-113">Klonované <xref:System.Data.DataTable> se vrátí po všech <xref:System.Data.DataRow> objekty ve vstupní tabulce dotazovatelný byly zkopírovány.</span><span class="sxs-lookup"><span data-stu-id="861fd-113">The cloned <xref:System.Data.DataTable> is returned after all <xref:System.Data.DataRow> objects in the input queryable table have been copied.</span></span> <span data-ttu-id="861fd-114">Pokud zdrojové sekvence neobsahuje žádný <xref:System.Data.DataRow> objektů, metoda vrátí prázdnou <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="861fd-114">If the source sequence does not contain any <xref:System.Data.DataRow> objects, the method returns an empty <xref:System.Data.DataTable>.</span></span>  
  
 <span data-ttu-id="861fd-115">Všimněte si, že volání <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> způsobí, že metoda vázán na zdrojové tabulky pro spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="861fd-115">Note that calling the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method will cause the query bound to the source table to execute.</span></span>  
  
 <span data-ttu-id="861fd-116">Když <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metoda zaznamená buď odkazu s hodnotou null, nebo typ s možnou hodnotou Null hodnoty v řádku ve zdrojové tabulce, se nahradí hodnotu s <xref:System.DBNull.Value>.</span><span class="sxs-lookup"><span data-stu-id="861fd-116">When the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method encounters either a null reference or nullable value type in a row in the source table, it replaces the value with <xref:System.DBNull.Value>.</span></span> <span data-ttu-id="861fd-117">Tímto způsobem, hodnoty null zpracovává správně ve vráceném <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="861fd-117">This way, null values are handled correctly in the returned <xref:System.Data.DataTable>.</span></span>  
  
 <span data-ttu-id="861fd-118">Poznámka: <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metoda akceptuje jako vstupní dotaz, který může vrátit řádky z několika <xref:System.Data.DataTable> nebo <xref:System.Data.DataSet> objekty.</span><span class="sxs-lookup"><span data-stu-id="861fd-118">Note: The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method accepts as input a query that can return rows from multiple <xref:System.Data.DataTable> or <xref:System.Data.DataSet> objects.</span></span> <span data-ttu-id="861fd-119"><xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metoda zkopíruje data, ale ne vlastnosti ze zdroje <xref:System.Data.DataTable> nebo <xref:System.Data.DataSet> objektů vrácený <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="861fd-119">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method will copy the data but not the properties from the source <xref:System.Data.DataTable> or <xref:System.Data.DataSet> objects to the returned <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="861fd-120">Je potřeba explicitně nastavit vlastnosti na vrácený <xref:System.Data.DataTable>, jako například <xref:System.Data.DataTable.Locale%2A> a <xref:System.Data.DataTable.TableName%2A>.</span><span class="sxs-lookup"><span data-stu-id="861fd-120">You will need to explicitly set the properties on the returned <xref:System.Data.DataTable>, such as <xref:System.Data.DataTable.Locale%2A> and <xref:System.Data.DataTable.TableName%2A>.</span></span>  
  
 <span data-ttu-id="861fd-121">V následujícím příkladu dotazuje tabulku SalesOrderHeader pro objednávky po 8. srpna 2001 a používá <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metodu pro vytvoření <xref:System.Data.DataTable> z tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="861fd-121">The following example queries the SalesOrderHeader table for orders after August 8, 2001 and uses the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method to create a <xref:System.Data.DataTable> from that query.</span></span> <span data-ttu-id="861fd-122"><xref:System.Data.DataTable> Pak je vázána <xref:System.Windows.Forms.BindingSource>, který funguje jako proxy server pro <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="861fd-122">The <xref:System.Data.DataTable> is then bound to a <xref:System.Windows.Forms.BindingSource>, which acts as proxy for a <xref:System.Windows.Forms.DataGridView>.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CopyToDataTable1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#copytodatatable1)]
 [!code-vb[DP LINQ to DataSet Examples#CopyToDataTable1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#copytodatatable1)]  
  
## <a name="creating-a-custom-copytodatatablet-method"></a><span data-ttu-id="861fd-123">Vytváření vlastních CopyToDataTable\<T > – metoda</span><span class="sxs-lookup"><span data-stu-id="861fd-123">Creating a Custom CopyToDataTable\<T> Method</span></span>  
 <span data-ttu-id="861fd-124">Existující <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metody pracovat pouze v <xref:System.Collections.Generic.IEnumerable%601> zdroje kde obecný parametr `T` je typu <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="861fd-124">The existing <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> methods only operate on an <xref:System.Collections.Generic.IEnumerable%601> source where the generic parameter `T` is of type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="861fd-125">I když to je užitečné, neumožňuje tabulky má být vytvořen z posloupnost Skalární typy, dotazy, které vracejí anonymní typy nebo dotazy, které provádějí spoje tabulky platná.</span><span class="sxs-lookup"><span data-stu-id="861fd-125">Although this is useful, it does not allow tables to be created from a sequence of scalar types, from queries that return anonymous types, or from queries that perform table joins.</span></span> <span data-ttu-id="861fd-126">Příklad toho, jak implementovat dvě vlastní `CopyToDataTable` metody, které načíst tabulku z řady typů skalární nebo anonymní, najdete v části [postupy: implementace CopyToDataTable\<T > kde the obecný typ T Is Not DataRow](../../../../docs/framework/data/adonet/implement-copytodatatable-where-type-not-a-datarow.md)s.</span><span class="sxs-lookup"><span data-stu-id="861fd-126">For an example of how to implement two custom `CopyToDataTable` methods that load a table from a sequence of scalar or anonymous types, see [How to: Implement CopyToDataTable\<T> Where the Generic Type T Is Not a DataRow](../../../../docs/framework/data/adonet/implement-copytodatatable-where-type-not-a-datarow.md)s.</span></span>  
  
 <span data-ttu-id="861fd-127">Příklady v této části použijte následující vlastní typy:</span><span class="sxs-lookup"><span data-stu-id="861fd-127">The examples in this section use the following custom types:</span></span>  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#ItemClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#itemclass)]
 [!code-vb[DP Custom CopyToDataTable Examples#ItemClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#itemclass)]  
  
### <a name="example"></a><span data-ttu-id="861fd-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="861fd-128">Example</span></span>  
 <span data-ttu-id="861fd-129">Tento příklad spojí přes `SalesOrderHeader` a `SalesOrderDetail` tabulky, chcete-li získat online objednávky z srpnu a vytvoří tabulku z dotazu.</span><span class="sxs-lookup"><span data-stu-id="861fd-129">This example performs a join over the `SalesOrderHeader` and `SalesOrderDetail` tables to get online orders from the month of August and creates a table from the query.</span></span>  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#join)]
 [!code-vb[DP Custom CopyToDataTable Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#join)]  
  
### <a name="example"></a><span data-ttu-id="861fd-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="861fd-130">Example</span></span>  
 <span data-ttu-id="861fd-131">V následujícím příkladu dotazuje kolekci pro ceny, které jsou větší než $9.99 a vytvoří tabulku z výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="861fd-131">The following example queries a collection for items of price greater than $9.99 and creates a table from the query results.</span></span>  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsIntoTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsintotable)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsIntoTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsintotable)]  
  
### <a name="example"></a><span data-ttu-id="861fd-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="861fd-132">Example</span></span>  
 <span data-ttu-id="861fd-133">V následujícím příkladu dotazuje kolekci pro větší než 9.99 ceny a projekty výsledky.</span><span class="sxs-lookup"><span data-stu-id="861fd-133">The following example queries a collection for items of price greater than 9.99 and projects the results.</span></span> <span data-ttu-id="861fd-134">Vrácený pořadí anonymní typy je načten do existující tabulky.</span><span class="sxs-lookup"><span data-stu-id="861fd-134">The returned sequence of anonymous types is loaded into an existing table.</span></span>  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsIntoExistingTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsintoexistingtable)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsIntoExistingTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsintoexistingtable)]  
  
### <a name="example"></a><span data-ttu-id="861fd-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="861fd-135">Example</span></span>  
 <span data-ttu-id="861fd-136">V následujícím příkladu dotazuje kolekci pro ceny, které jsou větší než $9.99 a projekty výsledky.</span><span class="sxs-lookup"><span data-stu-id="861fd-136">The following example queries a collection for items of price greater than $9.99 and projects the results.</span></span> <span data-ttu-id="861fd-137">Vrácený pořadí anonymní typy je načten do existující tabulky.</span><span class="sxs-lookup"><span data-stu-id="861fd-137">The returned sequence of anonymous types is loaded into an existing table.</span></span> <span data-ttu-id="861fd-138">Schéma tabulky je automaticky rozšířena, protože `Book` a `Movies` typy jsou odvozeny od `Item` typu.</span><span class="sxs-lookup"><span data-stu-id="861fd-138">The table schema is automatically expanded because the `Book` and `Movies` types are derived from the `Item` type.</span></span>  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsExpandSchema](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsexpandschema)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsExpandSchema](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsexpandschema)]  
  
### <a name="example"></a><span data-ttu-id="861fd-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="861fd-139">Example</span></span>  
 <span data-ttu-id="861fd-140">V následujícím příkladu dotazuje kolekci pro ceny, které jsou větší než $9.99 a vrátí posloupnost <xref:System.Double>, který je načten do nové tabulky.</span><span class="sxs-lookup"><span data-stu-id="861fd-140">The following example queries a collection for items of price greater than $9.99 and returns a sequence of <xref:System.Double>, which is loaded into a new table.</span></span>  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadScalarSequence](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loadscalarsequence)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadScalarSequence](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loadscalarsequence)]  
  
## <a name="see-also"></a><span data-ttu-id="861fd-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="861fd-141">See Also</span></span>  
 [<span data-ttu-id="861fd-142">Průvodce programováním</span><span class="sxs-lookup"><span data-stu-id="861fd-142">Programming Guide</span></span>](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
 [<span data-ttu-id="861fd-143">Obecné pole a SetField metody</span><span class="sxs-lookup"><span data-stu-id="861fd-143">Generic Field and SetField Methods</span></span>](../../../../docs/framework/data/adonet/generic-field-and-setfield-methods-linq-to-dataset.md)  
 [<span data-ttu-id="861fd-144">LINQ na DataSet příklady</span><span class="sxs-lookup"><span data-stu-id="861fd-144">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)