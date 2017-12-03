---
title: DiffGrams
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 037f3991-7bbc-424b-b52e-8b03585d3e34
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ff43b9279130ed710d9d88cbf2ba5ead4a6f0ebc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="diffgrams"></a><span data-ttu-id="4efd7-102">DiffGrams</span><span class="sxs-lookup"><span data-stu-id="4efd7-102">DiffGrams</span></span>
<span data-ttu-id="4efd7-103">Prvek formátu DiffGram je formátu XML, který identifikuje aktuální a původní verze datové prvky.</span><span class="sxs-lookup"><span data-stu-id="4efd7-103">A DiffGram is an XML format that identifies current and original versions of data elements.</span></span> <span data-ttu-id="4efd7-104"><xref:System.Data.DataSet> Používá formát DiffGram formát pro načtení a zachovat její obsah a k serializaci její obsah pro přenos přes síťové připojení.</span><span class="sxs-lookup"><span data-stu-id="4efd7-104">The <xref:System.Data.DataSet> uses the DiffGram format to load and persist its contents, and to serialize its contents for transport across a network connection.</span></span> <span data-ttu-id="4efd7-105">Když <xref:System.Data.DataSet> je zapsána jako formát DiffGram, vyplní formát DiffGram všechny potřebné informace přesně znovu vytvořit obsah, když není schéma služby <xref:System.Data.DataSet>, včetně hodnoty ve sloupcích i **původní** a **aktuální** verze řádku, řádku informace o chybě a pořadí řádků.</span><span class="sxs-lookup"><span data-stu-id="4efd7-105">When a <xref:System.Data.DataSet> is written as a DiffGram, it populates the DiffGram with all the necessary information to accurately recreate the contents, though not the schema, of the <xref:System.Data.DataSet>, including column values from both the **Original** and **Current** row versions, row error information, and row order.</span></span>  
  
 <span data-ttu-id="4efd7-106">Při odesílání a načítání <xref:System.Data.DataSet> z webové služby XML, je implicitně použít formát DiffGram formát.</span><span class="sxs-lookup"><span data-stu-id="4efd7-106">When sending and retrieving a <xref:System.Data.DataSet> from an XML Web service, the DiffGram format is implicitly used.</span></span> <span data-ttu-id="4efd7-107">Kromě toho při načítání obsahu <xref:System.Data.DataSet> pomocí XML **ReadXml** metoda, nebo při zápisu obsahu <xref:System.Data.DataSet> v XML pomocí **WriteXml** metodu, můžete zadat aby se obsah lze číst nebo zapisovat jako prvek formátu DiffGram.</span><span class="sxs-lookup"><span data-stu-id="4efd7-107">Additionally, when loading the contents of a <xref:System.Data.DataSet> from XML using the **ReadXml** method, or when writing the contents of a <xref:System.Data.DataSet> in XML using the **WriteXml** method, you can specify that the contents be read or written as a DiffGram.</span></span> <span data-ttu-id="4efd7-108">Další informace najdete v tématu [načítání datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md) a [zápis obsah datovou sadu jako XML Data](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).</span><span class="sxs-lookup"><span data-stu-id="4efd7-108">For more information, see [Loading a DataSet from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md) and [Writing DataSet Contents as XML Data](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).</span></span>  
  
 <span data-ttu-id="4efd7-109">Zatímco formát formát DiffGram slouží především rozhraní .NET Framework jako formát serializace pro obsah <xref:System.Data.DataSet>, DiffGrams můžete také použít k úpravě data v tabulkách v databázi Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4efd7-109">While the DiffGram format is primarily used by the .NET Framework as a serialization format for the contents of a <xref:System.Data.DataSet>, you can also use DiffGrams to modify data in tables in a Microsoft SQL Server database.</span></span>  
  
 <span data-ttu-id="4efd7-110">Prvek formátu Diffgram je generován zápisu obsahu pro všechny tabulky  **\<formát diffgram >** element.</span><span class="sxs-lookup"><span data-stu-id="4efd7-110">A Diffgram is generated by writing the contents of all tables to a **\<diffgram>** element.</span></span>  
  
### <a name="to-generate-a-diffgram"></a><span data-ttu-id="4efd7-111">Chcete-li generovat formát Diffgram</span><span class="sxs-lookup"><span data-stu-id="4efd7-111">To generate a Diffgram</span></span>  
  
1.  <span data-ttu-id="4efd7-112">Vygenerujte seznam tabulek kořenové (tedy tabulky bez některé z nadřazených).</span><span class="sxs-lookup"><span data-stu-id="4efd7-112">Generate a list of Root tables (that is, tables without any parent).</span></span>  
  
2.  <span data-ttu-id="4efd7-113">Pro každou tabulku a jeho následníky v seznamu vypsat aktuální verze všech řádků v první části formát Diffgram.</span><span class="sxs-lookup"><span data-stu-id="4efd7-113">For each table and its descendants in the list, write out the current version of all rows in the first Diffgram section.</span></span>  
  
3.  <span data-ttu-id="4efd7-114">Pro každou tabulku v <xref:System.Data.DataSet>, vypsat původní verzi všechny řádky, pokud existuje v  **\<před >** oddílu formát Diffgram.</span><span class="sxs-lookup"><span data-stu-id="4efd7-114">For each table in the <xref:System.Data.DataSet>, write out the original version of all rows, if any, in the **\<before>** section of the Diffgram.</span></span>  
  
4.  <span data-ttu-id="4efd7-115">Pro řádků s chybami, zapisovat chyby obsah  **\<chyby >** oddílu formát Diffgram.</span><span class="sxs-lookup"><span data-stu-id="4efd7-115">For rows that have errors, write the error content in the **\<errors>** section of the Diffgram.</span></span>  
  
 <span data-ttu-id="4efd7-116">Prvek formátu Diffgram je zpracovávána v pořadí od začátku souboru XML na konec.</span><span class="sxs-lookup"><span data-stu-id="4efd7-116">A Diffgram is processed in order from beginning of the XML file to the end.</span></span>  
  
### <a name="to-process-a-diffgram"></a><span data-ttu-id="4efd7-117">Při zpracování prvek formátu Diffgram</span><span class="sxs-lookup"><span data-stu-id="4efd7-117">To process a Diffgram</span></span>  
  
1.  <span data-ttu-id="4efd7-118">Proces v první části formát Diffgram, který obsahuje aktuální verze řádků.</span><span class="sxs-lookup"><span data-stu-id="4efd7-118">Process the first section of the Diffgram that contains the current version of the rows.</span></span>  
  
2.  <span data-ttu-id="4efd7-119">Zpracování druhý nebo  **\<před >** oddíl, který obsahuje původní verze řádku upravit a odstranit řádky.</span><span class="sxs-lookup"><span data-stu-id="4efd7-119">Process the second or the **\<before>** section that contains the original row version of modified and deleted rows.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4efd7-120">Pokud řádek je označen jako odstraněný, operace odstranění odstranit řádku následníky také, v závislosti na `Cascade` vlastnost aktuálního <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="4efd7-120">If a row is marked deleted, the delete operation can delete the row's descendants as well, depending on the `Cascade` property of the current <xref:System.Data.DataSet>.</span></span>  
  
3.  <span data-ttu-id="4efd7-121">Proces  **\<chyby >** části.</span><span class="sxs-lookup"><span data-stu-id="4efd7-121">Process the **\<errors>** section.</span></span> <span data-ttu-id="4efd7-122">Nastavte informace o chybě pro zadaný řádků a sloupců pro každou položku v této části.</span><span class="sxs-lookup"><span data-stu-id="4efd7-122">Set the error information for the specified row and column for each item in this section.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4efd7-123">Pokud nastavíte <xref:System.Data.XmlWriteMode> do formátu Diffgram, obsah cíle <xref:System.Data.DataSet> a původní <xref:System.Data.DataSet> se můžou lišit.</span><span class="sxs-lookup"><span data-stu-id="4efd7-123">If you set the <xref:System.Data.XmlWriteMode> to Diffgram, the content of the target <xref:System.Data.DataSet> and the original <xref:System.Data.DataSet> may differ.</span></span>  
  
## <a name="diffgram-format"></a><span data-ttu-id="4efd7-124">Formát DiffGram formátu</span><span class="sxs-lookup"><span data-stu-id="4efd7-124">DiffGram Format</span></span>  
 <span data-ttu-id="4efd7-125">Formát DiffGram formát je rozdělené do tří částí: aktuálních dat, původní (nebo "před") dat a chyby části, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="4efd7-125">The DiffGram format is divided into three sections: the current data, the original (or "before") data, and an errors section, as shown in the following example.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<diffgr:diffgram   
         xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"  
         xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1"  
         xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  
   <DataInstance>  
   </DataInstance>  
  
  <diffgr:before>  
  </diffgr:before>  
  
  <diffgr:errors>  
  </diffgr:errors>  
</diffgr:diffgram>  
```  
  
 <span data-ttu-id="4efd7-126">Formát formát DiffGram zahrnuje následující bloky dat:</span><span class="sxs-lookup"><span data-stu-id="4efd7-126">The DiffGram format consists of the following blocks of data:</span></span>  
  
 <span data-ttu-id="4efd7-127">**\<**  ***DataInstance***  **>**</span><span class="sxs-lookup"><span data-stu-id="4efd7-127">**\<**  ***DataInstance***  **>**</span></span>  
 <span data-ttu-id="4efd7-128">Název tohoto elementu, ***DataInstance***, se používá pro účely vysvětlení v této dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="4efd7-128">The name of this element, ***DataInstance***, is used for explanation purposes in this documentation.</span></span> <span data-ttu-id="4efd7-129">A ***DataInstance*** reprezentuje element <xref:System.Data.DataSet> nebo řádek <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="4efd7-129">A ***DataInstance*** element represents a <xref:System.Data.DataSet> or a row of a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="4efd7-130">Místo *DataInstance*, element by obsahovat název <xref:System.Data.DataSet> nebo <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="4efd7-130">Instead of *DataInstance*, the element would contain the name of the <xref:System.Data.DataSet> or <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="4efd7-131">Tento blok formátu formát DiffGram obsahuje aktuální data, zda byl upraven, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="4efd7-131">This block of the DiffGram format contains the current data, whether it has been modified or not.</span></span> <span data-ttu-id="4efd7-132">Je označeny prvek, nebo řádek, který byl změněn **diffgr:hasChanges** poznámky.</span><span class="sxs-lookup"><span data-stu-id="4efd7-132">An element, or row, that has been modified is identified with the **diffgr:hasChanges** annotation.</span></span>  
  
 <span data-ttu-id="4efd7-133">**\<diffgr: před >**</span><span class="sxs-lookup"><span data-stu-id="4efd7-133">**\<diffgr:before>**</span></span>  
 <span data-ttu-id="4efd7-134">Tento blok formátu formát DiffGram obsahuje původní verzi řádek.</span><span class="sxs-lookup"><span data-stu-id="4efd7-134">This block of the DiffGram format contains the original version of a row.</span></span> <span data-ttu-id="4efd7-135">Elementy v tomto bloku se shodují se elementů v ***DataInstance*** blokovat, s využitím **diffgr:id** poznámky.</span><span class="sxs-lookup"><span data-stu-id="4efd7-135">Elements in this block are matched to elements in the ***DataInstance*** block using the **diffgr:id** annotation.</span></span>  
  
 <span data-ttu-id="4efd7-136">**\<diffgr:Errors >**</span><span class="sxs-lookup"><span data-stu-id="4efd7-136">**\<diffgr:errors>**</span></span>  
 <span data-ttu-id="4efd7-137">Tento blok formátu formát DiffGram obsahuje informace o chybě pro konkrétního řádku ***DataInstance*** bloku.</span><span class="sxs-lookup"><span data-stu-id="4efd7-137">This block of the DiffGram format contains error information for a particular row in the ***DataInstance*** block.</span></span> <span data-ttu-id="4efd7-138">Elementy v tomto bloku se shodují se elementů v ***DataInstance*** blokovat, s využitím **diffgr:id** poznámky.</span><span class="sxs-lookup"><span data-stu-id="4efd7-138">Elements in this block are matched to elements in the ***DataInstance*** block using the **diffgr:id** annotation.</span></span>  
  
## <a name="diffgram-annotations"></a><span data-ttu-id="4efd7-139">Formát DiffGram poznámky</span><span class="sxs-lookup"><span data-stu-id="4efd7-139">DiffGram Annotations</span></span>  
 <span data-ttu-id="4efd7-140">DiffGrams se týkají elementy ze jiný formát DiffGram bloků, které představují různé řádek verze nebo informace o chybě v pomocí jsme několik poznámek <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="4efd7-140">DiffGrams use several annotations to relate elements from the different DiffGram blocks that represent different row versions or error information in the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="4efd7-141">Následující tabulka popisuje formát DiffGram poznámky, které jsou definovány v oboru názvů formátu DiffGram **urn: schémata-microsoft-com: XML-formát diffgram-v1**.</span><span class="sxs-lookup"><span data-stu-id="4efd7-141">The following table describes the DiffGram annotations that are defined in the DiffGram namespace **urn:schemas-microsoft-com:xml-diffgram-v1**.</span></span>  
  
|<span data-ttu-id="4efd7-142">Poznámka</span><span class="sxs-lookup"><span data-stu-id="4efd7-142">Annotation</span></span>|<span data-ttu-id="4efd7-143">Popis</span><span class="sxs-lookup"><span data-stu-id="4efd7-143">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="4efd7-144">**ID**</span><span class="sxs-lookup"><span data-stu-id="4efd7-144">**id**</span></span>|<span data-ttu-id="4efd7-145">Použít spárovat elementů v  **\<diffgr: před >** a  **\<diffgr:errors >** bloky elementům ve  **\<**  ***DataInstance***  **>**  bloku.</span><span class="sxs-lookup"><span data-stu-id="4efd7-145">Used to pair the elements in the **\<diffgr:before>** and **\<diffgr:errors>** blocks to elements in the **\<** ***DataInstance*** **>** block.</span></span> <span data-ttu-id="4efd7-146">Hodnoty s **diffgr:id** poznámky jsou ve tvaru *[TableName] [RowIdentifier]*.</span><span class="sxs-lookup"><span data-stu-id="4efd7-146">Values with the **diffgr:id** annotation are in the form *[TableName][RowIdentifier]*.</span></span> <span data-ttu-id="4efd7-147">Příklad: `<Customers diffgr:id="Customers1">`.</span><span class="sxs-lookup"><span data-stu-id="4efd7-147">For example: `<Customers diffgr:id="Customers1">`.</span></span>|  
|<span data-ttu-id="4efd7-148">**identifikátor parentId**</span><span class="sxs-lookup"><span data-stu-id="4efd7-148">**parentId**</span></span>|<span data-ttu-id="4efd7-149">Identifikuje které element z  **\<**  ***DataInstance***  **>**  blok je nadřazeného elementu aktuálního elementu.</span><span class="sxs-lookup"><span data-stu-id="4efd7-149">Identifies which element from the **\<** ***DataInstance*** **>** block is the parent element of the current element.</span></span> <span data-ttu-id="4efd7-150">Hodnoty s **diffgr:parentId** poznámky jsou ve tvaru *[TableName] [RowIdentifier]*.</span><span class="sxs-lookup"><span data-stu-id="4efd7-150">Values with the **diffgr:parentId** annotation are in the form *[TableName][RowIdentifier]*.</span></span> <span data-ttu-id="4efd7-151">Příklad: `<Orders diffgr:parentId="Customers1">`.</span><span class="sxs-lookup"><span data-stu-id="4efd7-151">For example: `<Orders diffgr:parentId="Customers1">`.</span></span>|  
|<span data-ttu-id="4efd7-152">**haschanges –**</span><span class="sxs-lookup"><span data-stu-id="4efd7-152">**hasChanges**</span></span>|<span data-ttu-id="4efd7-153">Identifikuje řádek  **\<**  ***DataInstance***  **>**  blokovat jako upravená.</span><span class="sxs-lookup"><span data-stu-id="4efd7-153">Identifies a row in the **\<** ***DataInstance*** **>** block as modified.</span></span> <span data-ttu-id="4efd7-154">**Haschanges –** poznámky může mít jednu z následujících dvou hodnot:</span><span class="sxs-lookup"><span data-stu-id="4efd7-154">The **hasChanges** annotation can have one of the following two values:</span></span><br /><br /> <span data-ttu-id="4efd7-155">**Vložit**</span><span class="sxs-lookup"><span data-stu-id="4efd7-155">**inserted**</span></span><br /> <span data-ttu-id="4efd7-156">Identifikuje **Added** řádek.</span><span class="sxs-lookup"><span data-stu-id="4efd7-156">Identifies an **Added** row.</span></span><br /><br /> <span data-ttu-id="4efd7-157">**Upravit**</span><span class="sxs-lookup"><span data-stu-id="4efd7-157">**modified**</span></span><br /> <span data-ttu-id="4efd7-158">Identifikuje **změněné** řádek, který obsahuje **původní** verze řádku v  **\<diffgr: před >** bloku.</span><span class="sxs-lookup"><span data-stu-id="4efd7-158">Identifies a **Modified** row that contains an **Original** row version in the **\<diffgr:before>** block.</span></span> <span data-ttu-id="4efd7-159">Všimněte si, že **odstraněné** řádky budou mít **původní** verze řádku v  **\<diffgr: před >** bloku, ale zde bude žádný element s poznámkami ve  **\<**  ***DataInstance***  **>**  bloku.</span><span class="sxs-lookup"><span data-stu-id="4efd7-159">Note that **Deleted** rows will have an **Original** row version in the **\<diffgr:before>** block, but there will be no annotated element in the **\<** ***DataInstance*** **>** block.</span></span>|  
|<span data-ttu-id="4efd7-160">**hasErrors**</span><span class="sxs-lookup"><span data-stu-id="4efd7-160">**hasErrors**</span></span>|<span data-ttu-id="4efd7-161">Identifikuje řádek  **\<**  ***DataInstance***  **>**  blokovat s **RowError**.</span><span class="sxs-lookup"><span data-stu-id="4efd7-161">Identifies a row in the **\<** ***DataInstance*** **>** block with a **RowError**.</span></span> <span data-ttu-id="4efd7-162">Chyba prvek je umístěn v  **\<diffgr:errors >** bloku.</span><span class="sxs-lookup"><span data-stu-id="4efd7-162">The error element is placed in the **\<diffgr:errors>** block.</span></span>|  
|<span data-ttu-id="4efd7-163">**Chyba**</span><span class="sxs-lookup"><span data-stu-id="4efd7-163">**Error**</span></span>|<span data-ttu-id="4efd7-164">Obsahuje text **RowError** pro konkrétní prvek,  **\<diffgr:errors >** bloku.</span><span class="sxs-lookup"><span data-stu-id="4efd7-164">Contains the text of the **RowError** for a particular element in the **\<diffgr:errors>** block.</span></span>|  
  
 <span data-ttu-id="4efd7-165"><xref:System.Data.DataSet> Zahrnuje další poznámky při čtení nebo zápisu jako prvek formátu DiffGram její obsah.</span><span class="sxs-lookup"><span data-stu-id="4efd7-165">The <xref:System.Data.DataSet> includes additional annotations when reading or writing its contents as a DiffGram.</span></span> <span data-ttu-id="4efd7-166">Následující tabulka popisuje tyto další poznámky, které jsou definovány v oboru názvů **urn: schémata-microsoft-com: XML-msdata**.</span><span class="sxs-lookup"><span data-stu-id="4efd7-166">The following table describes these additional annotations, which are defined in the namespace **urn:schemas-microsoft-com:xml-msdata**.</span></span>  
  
|<span data-ttu-id="4efd7-167">Poznámka</span><span class="sxs-lookup"><span data-stu-id="4efd7-167">Annotation</span></span>|<span data-ttu-id="4efd7-168">Popis</span><span class="sxs-lookup"><span data-stu-id="4efd7-168">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="4efd7-169">**Atributu RowOrder**</span><span class="sxs-lookup"><span data-stu-id="4efd7-169">**RowOrder**</span></span>|<span data-ttu-id="4efd7-170">Zachová řádek pořadí původní data a identifikuje index v řádku v konkrétní <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="4efd7-170">Preserves the row order of the original data and identifies the index of a row in a particular <xref:System.Data.DataTable>.</span></span>|  
|<span data-ttu-id="4efd7-171">**Skryté**</span><span class="sxs-lookup"><span data-stu-id="4efd7-171">**Hidden**</span></span>|<span data-ttu-id="4efd7-172">Určuje sloupec tak, že má **ColumnMapping** vlastnost nastavena na hodnotu **MappingType.Hidden**.</span><span class="sxs-lookup"><span data-stu-id="4efd7-172">Identifies a column as having a **ColumnMapping** property set to **MappingType.Hidden**.</span></span> <span data-ttu-id="4efd7-173">Atribut je zapsaný ve formátu **msdata: Skrytá** *[ColumnName]*= "*hodnotu*".</span><span class="sxs-lookup"><span data-stu-id="4efd7-173">The attribute is written in the format **msdata:hidden** *[ColumnName]*="*value*".</span></span> <span data-ttu-id="4efd7-174">Příklad: `<Customers diffgr:id="Customers1" msdata:hiddenContactTitle="Owner">`.</span><span class="sxs-lookup"><span data-stu-id="4efd7-174">For example: `<Customers diffgr:id="Customers1" msdata:hiddenContactTitle="Owner">`.</span></span><br /><br /> <span data-ttu-id="4efd7-175">Všimněte si, že skrytých sloupců zapíšou jenom jako atribut formátu DiffGram pokud obsahují data.</span><span class="sxs-lookup"><span data-stu-id="4efd7-175">Note that hidden columns are only written as a DiffGram attribute if they contain data.</span></span> <span data-ttu-id="4efd7-176">Jinak jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="4efd7-176">Otherwise, they are ignored.</span></span>|  
  
## <a name="sample-diffgram"></a><span data-ttu-id="4efd7-177">Formát DiffGram ukázka</span><span class="sxs-lookup"><span data-stu-id="4efd7-177">Sample DiffGram</span></span>  
 <span data-ttu-id="4efd7-178">Níže je uveden příklad formátu DiffGram formátu.</span><span class="sxs-lookup"><span data-stu-id="4efd7-178">An example of the DiffGram format is shown below.</span></span> <span data-ttu-id="4efd7-179">Tento příklad ukazuje výsledek aktualizace na řádek v tabulce, než změny byly potvrzeny.</span><span class="sxs-lookup"><span data-stu-id="4efd7-179">This example shows the result of an update to a row in a table before the changes have been committed.</span></span> <span data-ttu-id="4efd7-180">Řádek s CustomerID "ALFKI" byla upravena, ale neaktualizuje.</span><span class="sxs-lookup"><span data-stu-id="4efd7-180">The row with a CustomerID of "ALFKI" has been modified, but not updated.</span></span> <span data-ttu-id="4efd7-181">V důsledku toho je **aktuální** řádek s **diffgr:id** z označena "jako Zákazníci1" v  **\<**  ***DataInstance***  **>**  bloku a **původní** řádek s **diffgr:id** z označena "jako Zákazníci1" v  **\<diffgr: před >**bloku.</span><span class="sxs-lookup"><span data-stu-id="4efd7-181">As a result, there is a **Current** row with a **diffgr:id** of "Customers1" in the **\<** ***DataInstance*** **>** block, and an **Original** row with a **diffgr:id** of "Customers1" in the **\<diffgr:before>** block.</span></span> <span data-ttu-id="4efd7-182">Obsahuje řádek s CustomerID "ANATR" **RowError**, takže je opatřen poznámkou `diffgr:hasErrors="true"` a související prvek,  **\<diffgr:errors >** bloku.</span><span class="sxs-lookup"><span data-stu-id="4efd7-182">The row with a CustomerID of "ANATR" includes a **RowError**, so it is annotated with `diffgr:hasErrors="true"` and there is a related element in the **\<diffgr:errors>** block.</span></span>  
  
```xml  
<diffgr:diffgram xmlns:msdata="urn:schemas-microsoft-com:xml-msdata" xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
  <CustomerDataSet>  
    <Customers diffgr:id="Customers1" msdata:rowOrder="0" diffgr:hasChanges="modified">  
      <CustomerID>ALFKI</CustomerID>  
      <CompanyName>New Company</CompanyName>  
    </Customers>  
    <Customers diffgr:id="Customers2" msdata:rowOrder="1" diffgram:hasErrors="true">  
      <CustomerID>ANATR</CustomerID>  
      <CompanyName>Ana Trujillo Emparedados y Helados</CompanyName>  
    </Customers>  
    <Customers diffgr:id="Customers3" msdata:rowOrder="2">  
      <CustomerID>ANTON</CustomerID>  
      <CompanyName>Antonio Moreno Taquera</CompanyName>  
    </Customers>  
    <Customers diffgr:id="Customers4" msdata:rowOrder="3">  
      <CustomerID>AROUT</CustomerID>  
      <CompanyName>Around the Horn</CompanyName>  
    </Customers>  
  </CustomerDataSet>  
  <diffgr:before>  
    <Customers diffgr:id="Customers1" msdata:rowOrder="0">  
      <CustomerID>ALFKI</CustomerID>  
      <CompanyName>Alfreds Futterkiste</CompanyName>  
    </Customers>  
  </diffgr:before>  
  <diffgr:errors>  
    <Customers diffgr:id="Customers2" diffgr:Error="An optimistic concurrency violation has occurred for this row."/>  
  </diffgr:errors>  
</diffgr:diffgram>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4efd7-183">Viz také</span><span class="sxs-lookup"><span data-stu-id="4efd7-183">See Also</span></span>  
 [<span data-ttu-id="4efd7-184">Pomocí XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="4efd7-184">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="4efd7-185">Načítání datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="4efd7-185">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="4efd7-186">Zápis obsah datovou sadu jako XML Data</span><span class="sxs-lookup"><span data-stu-id="4efd7-186">Writing DataSet Contents as XML Data</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)  
 [<span data-ttu-id="4efd7-187">Datové sady, DataTables a DataView</span><span class="sxs-lookup"><span data-stu-id="4efd7-187">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="4efd7-188">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="4efd7-188">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)