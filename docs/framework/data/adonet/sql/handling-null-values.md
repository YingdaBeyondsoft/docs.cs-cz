---
title: "Zpracování hodnot Null"
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
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1f29cbd51c036ecc15306f67fdd32dee6a4f1b68
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="handling-null-values"></a><span data-ttu-id="87cf3-102">Zpracování hodnot Null</span><span class="sxs-lookup"><span data-stu-id="87cf3-102">Handling Null Values</span></span>
<span data-ttu-id="87cf3-103">Hodnotu null v relační databázi se používá, pokud je hodnota ve sloupci neznámý nebo chybí.</span><span class="sxs-lookup"><span data-stu-id="87cf3-103">A null value in a relational database is used when the value in a column is unknown or missing.</span></span> <span data-ttu-id="87cf3-104">Null není prázdný řetězec (pro datové typy znaků nebo data a času) ani hodnotu nula (pro číselné datové typy).</span><span class="sxs-lookup"><span data-stu-id="87cf3-104">A null is neither an empty string (for character or datetime data types) nor a zero value (for numeric data types).</span></span> <span data-ttu-id="87cf3-105">Specifikace ANSI SQL-92 stavy s hodnotou null musí být stejné pro všechny typy dat, tak, aby všechny hodnoty Null zpracovává konzistentně.</span><span class="sxs-lookup"><span data-stu-id="87cf3-105">The ANSI SQL-92 specification states that a null must be the same for all data types, so that all nulls are handled consistently.</span></span> <span data-ttu-id="87cf3-106"><xref:System.Data.SqlTypes> Obor názvů obsahuje hodnotu null sémantiku implementací <xref:System.Data.SqlTypes.INullable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="87cf3-106">The <xref:System.Data.SqlTypes> namespace provides null semantics by implementing the <xref:System.Data.SqlTypes.INullable> interface.</span></span> <span data-ttu-id="87cf3-107">Každý dat typy v <xref:System.Data.SqlTypes> má svou vlastní `IsNull` vlastnost a `Null` hodnotu, která lze přiřadit k instanci daného datového typu.</span><span class="sxs-lookup"><span data-stu-id="87cf3-107">Each of the data types in <xref:System.Data.SqlTypes> has its own `IsNull` property and a `Null` value that can be assigned to an instance of that data type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="87cf3-108">Podpora rozhraní .NET Framework verze 2.0 zavedená pro typy s možnou hodnotou Null, která umožňuje programátorům typ hodnoty k reprezentaci všech hodnot základní typ rozšíření.</span><span class="sxs-lookup"><span data-stu-id="87cf3-108">The .NET Framework version 2.0 introduced support for nullable types, which allow programmers to extend a value type to represent all values of the underlying type.</span></span> <span data-ttu-id="87cf3-109">Tyto typy s možnou hodnotou Null CLR představují instanci <xref:System.Nullable> struktura.</span><span class="sxs-lookup"><span data-stu-id="87cf3-109">These CLR nullable types represent an instance of the <xref:System.Nullable> structure.</span></span> <span data-ttu-id="87cf3-110">Tato funkce je obzvláště užitečná při hodnota typy jsou do pole a nezabalený, pokud rozšířené kompatibilitu s typy objektů.</span><span class="sxs-lookup"><span data-stu-id="87cf3-110">This capability is especially useful when value types are boxed and unboxed, providing enhanced compatibility with object types.</span></span> <span data-ttu-id="87cf3-111">Typy s možnou hodnotou Null CLR nejsou určeny pro úložiště databáze hodnoty Null, protože ANSI SQL null není chovají stejně jako `null` odkaz (nebo `Nothing` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="87cf3-111">CLR nullable types are not intended for storage of database nulls because an ANSI SQL null does not behave the same way as a `null` reference (or `Nothing` in Visual Basic).</span></span> <span data-ttu-id="87cf3-112">Pro práci s hodnotami null ANSI SQL databáze, použijte <xref:System.Data.SqlTypes> hodnoty Null místo <xref:System.Nullable>.</span><span class="sxs-lookup"><span data-stu-id="87cf3-112">For working with database ANSI SQL null values, use <xref:System.Data.SqlTypes> nulls rather than <xref:System.Nullable>.</span></span> <span data-ttu-id="87cf3-113">Další informace o práci s CLR najdete v části typy s možnou hodnotou Null v jazyce Visual Basic [typy s možnou hodnotou Null hodnot](~/docs/visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)a C# najdete v tématu [pomocí typy s možnou hodnotou Null](~/docs/csharp/programming-guide/nullable-types/using-nullable-types.md).</span><span class="sxs-lookup"><span data-stu-id="87cf3-113">For more information on working with CLR nullable types in Visual Basic see [Nullable Value Types](~/docs/visual-basic/programming-guide/language-features/data-types/nullable-value-types.md), and for C# see [Using Nullable Types](~/docs/csharp/programming-guide/nullable-types/using-nullable-types.md).</span></span>  
  
## <a name="nulls-and-three-valued-logic"></a><span data-ttu-id="87cf3-114">Hodnoty Null a s hodnotou tři logiky</span><span class="sxs-lookup"><span data-stu-id="87cf3-114">Nulls and Three-Valued Logic</span></span>  
 <span data-ttu-id="87cf3-115">Povolení hodnoty null v definicích sloupce zavádí s hodnotou tři logiku do vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="87cf3-115">Allowing null values in column definitions introduces three-valued logic into your application.</span></span> <span data-ttu-id="87cf3-116">Porovnání lze vyhodnotit na jednu ze tří podmínek:</span><span class="sxs-lookup"><span data-stu-id="87cf3-116">A comparison can evaluate to one of three conditions:</span></span>  
  
-   <span data-ttu-id="87cf3-117">Hodnota TRUE</span><span class="sxs-lookup"><span data-stu-id="87cf3-117">True</span></span>  
  
-   <span data-ttu-id="87cf3-118">False</span><span class="sxs-lookup"><span data-stu-id="87cf3-118">False</span></span>  
  
-   <span data-ttu-id="87cf3-119">Neznámé</span><span class="sxs-lookup"><span data-stu-id="87cf3-119">Unknown</span></span>  
  
 <span data-ttu-id="87cf3-120">Protože null se považuje za neznámý, ve srovnání s navzájem dvě hodnoty null, se nepovažují za stejná.</span><span class="sxs-lookup"><span data-stu-id="87cf3-120">Because null is considered to be unknown, two null values compared to each other are not considered to be equal.</span></span> <span data-ttu-id="87cf3-121">Pomocí aritmetických operátorů, pokud je některý z operandy hodnotu null ve výrazech, výsledkem je null také.</span><span class="sxs-lookup"><span data-stu-id="87cf3-121">In expressions using arithmetic operators, if any of the operands is null, the result is null as well.</span></span>  
  
## <a name="nulls-and-sqlboolean"></a><span data-ttu-id="87cf3-122">Hodnoty Null a SqlBoolean</span><span class="sxs-lookup"><span data-stu-id="87cf3-122">Nulls and SqlBoolean</span></span>  
 <span data-ttu-id="87cf3-123">Porovnání mezi všechny <xref:System.Data.SqlTypes> vrátí <xref:System.Data.SqlTypes.SqlBoolean>.</span><span class="sxs-lookup"><span data-stu-id="87cf3-123">Comparison between any <xref:System.Data.SqlTypes> will return a <xref:System.Data.SqlTypes.SqlBoolean>.</span></span> <span data-ttu-id="87cf3-124">`IsNull` Funkce pro každou `SqlType` vrátí <xref:System.Data.SqlTypes.SqlBoolean> a slouží ke kontrole hodnot null.</span><span class="sxs-lookup"><span data-stu-id="87cf3-124">The `IsNull` function for each `SqlType` returns a <xref:System.Data.SqlTypes.SqlBoolean> and can be used to check for null values.</span></span> <span data-ttu-id="87cf3-125">Následující pravdivosti tabulky zobrazit, jak AND, OR a ne operátory funkce případě hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="87cf3-125">The following truth tables show how the AND, OR, and NOT operators function in the presence of a null value.</span></span> <span data-ttu-id="87cf3-126">(T = true, F = false a U = Neznámý, nebo hodnotu null.)</span><span class="sxs-lookup"><span data-stu-id="87cf3-126">(T=true, F=false, and U=unknown, or null.)</span></span>  
  
 <span data-ttu-id="87cf3-127">![Tabulka pravdivosti](../../../../../docs/framework/data/adonet/sql/media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")</span><span class="sxs-lookup"><span data-stu-id="87cf3-127">![Truth Table](../../../../../docs/framework/data/adonet/sql/media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")</span></span>  
  
### <a name="understanding-the-ansinulls-option"></a><span data-ttu-id="87cf3-128">Principy možnosti ANSI_NULLS</span><span class="sxs-lookup"><span data-stu-id="87cf3-128">Understanding the ANSI_NULLS Option</span></span>  
 <span data-ttu-id="87cf3-129"><xref:System.Data.SqlTypes>poskytuje stejnou sémantiku jako možnosti ANSI_NULLS nastavena na v systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="87cf3-129"><xref:System.Data.SqlTypes> provides the same semantics as when the ANSI_NULLS option is set on in SQL Server.</span></span> <span data-ttu-id="87cf3-130">Všech aritmetických operátorů (+, -, *, /, %), bitové operátory (~ &, &#124;), a většina funkce vrátí hodnotu null, pokud je některý z operandy nebo argumenty null, s výjimkou vlastnost `IsNull`.</span><span class="sxs-lookup"><span data-stu-id="87cf3-130">All arithmetic operators (+, -, *, /, %), bitwise operators (~, &, &#124;), and most functions return null if any of the operands or arguments is null, except for the property `IsNull`.</span></span>  
  
 <span data-ttu-id="87cf3-131">Standardu ANSI SQL-92 nepodporuje *columnName* = NULL v klauzuli WHERE.</span><span class="sxs-lookup"><span data-stu-id="87cf3-131">The ANSI SQL-92 standard does not support *columnName* = NULL in a WHERE clause.</span></span> <span data-ttu-id="87cf3-132">V systému SQL Server možnosti ANSI_NULLS Určuje, jak výchozí možnost použití hodnoty Null v databázi a vyhodnocení porovnání s hodnotami null.</span><span class="sxs-lookup"><span data-stu-id="87cf3-132">In SQL Server, the ANSI_NULLS option controls both default nullability in the database and evaluation of comparisons against null values.</span></span> <span data-ttu-id="87cf3-133">Pokud ANSI_NULLS je zapnuté (výchozí), musí být operátoru IS NULL použít ve výrazech při testování hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="87cf3-133">If ANSI_NULLS is turned on (the default), the IS NULL operator must be used in expressions when testing for null values.</span></span> <span data-ttu-id="87cf3-134">Například na toto porovnání vždy vypočítá Neznámý ANSI_NULLS je na:</span><span class="sxs-lookup"><span data-stu-id="87cf3-134">For example, the following comparison always yields unknown when ANSI_NULLS is on:</span></span>  
  
```  
colname > NULL  
```  
  
 <span data-ttu-id="87cf3-135">Porovnání proměnné obsahující hodnotu null také vypočítá neznámý:</span><span class="sxs-lookup"><span data-stu-id="87cf3-135">Comparison to a variable containing a null value also yields unknown:</span></span>  
  
```  
colname > @MyVariable  
```  
  
 <span data-ttu-id="87cf3-136">Predikát je NULL nebo je NOT NULL použijte k testování pro hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="87cf3-136">Use the IS NULL or IS NOT NULL predicate to test for a null value.</span></span> <span data-ttu-id="87cf3-137">Složitost to můžete přidat do klauzule WHERE.</span><span class="sxs-lookup"><span data-stu-id="87cf3-137">This can add complexity to the WHERE clause.</span></span> <span data-ttu-id="87cf3-138">Například TerritoryID sloupec v tabulce Zákazník AdventureWorks povoluje hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="87cf3-138">For example, the TerritoryID column in the AdventureWorks Customer table allows null values.</span></span> <span data-ttu-id="87cf3-139">Pokud příkaz SELECT k testování hodnot null kromě ostatní, musí obsahovat predikát je NULL:</span><span class="sxs-lookup"><span data-stu-id="87cf3-139">If a SELECT statement is to test for null values in addition to others, it must include an IS NULL predicate:</span></span>  
  
```  
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
 <span data-ttu-id="87cf3-140">Pokud nastavíte ANSI_NULLS v systému SQL Server, můžete vytvořit výrazy, které používají operátor rovnosti k porovnání na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="87cf3-140">If you set ANSI_NULLS off in SQL Server, you can create expressions that use the equality operator to compare to null.</span></span> <span data-ttu-id="87cf3-141">Nelze však zabránit jiné připojení z nastavení null možností pro toto připojení.</span><span class="sxs-lookup"><span data-stu-id="87cf3-141">However, you can't prevent different connections from setting null options for that connection.</span></span> <span data-ttu-id="87cf3-142">Použití IS NULL k testování hodnot null vždy funguje, bez ohledu na nastavení ANSI_NULLS pro připojení.</span><span class="sxs-lookup"><span data-stu-id="87cf3-142">Using IS NULL to test for null values always works, regardless of the ANSI_NULLS settings for a connection.</span></span>  
  
 <span data-ttu-id="87cf3-143">Nastavení ANSI_NULLS vypnout nepodporuje `DataSet`, který následuje vždy standardu ANSI SQL-92 pro zpracování hodnot null ve <xref:System.Data.SqlTypes>.</span><span class="sxs-lookup"><span data-stu-id="87cf3-143">Setting ANSI_NULLS off is not supported in a `DataSet`, which always follows the ANSI SQL-92 standard for handling null values in <xref:System.Data.SqlTypes>.</span></span>  
  
## <a name="assigning-null-values"></a><span data-ttu-id="87cf3-144">Přiřazení hodnoty Null</span><span class="sxs-lookup"><span data-stu-id="87cf3-144">Assigning Null Values</span></span>  
 <span data-ttu-id="87cf3-145">Hodnoty Null jsou speciální a jejich úložiště a přiřazení sémantiku se mezi systémy jiného typu a úložných systémů liší.</span><span class="sxs-lookup"><span data-stu-id="87cf3-145">Null values are special, and their storage and assignment semantics differ across different type systems and storage systems.</span></span> <span data-ttu-id="87cf3-146">A `Dataset` je určen k použití s různými systémy typu a úložiště.</span><span class="sxs-lookup"><span data-stu-id="87cf3-146">A `Dataset` is designed to be used with different type and storage systems.</span></span>  
  
 <span data-ttu-id="87cf3-147">Tato část popisuje null sémantiky pro přiřazení hodnoty null do <xref:System.Data.DataColumn> v <xref:System.Data.DataRow> mezi systémy jiného typu.</span><span class="sxs-lookup"><span data-stu-id="87cf3-147">This section describes the null semantics for assigning null values to a <xref:System.Data.DataColumn> in a <xref:System.Data.DataRow> across the different type systems.</span></span>  
  
 `DBNull.Value`  
 <span data-ttu-id="87cf3-148">Je platná pro toto přiřazení `DataColumn` libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="87cf3-148">This assignment is valid for a `DataColumn` of any type.</span></span> <span data-ttu-id="87cf3-149">Pokud typ implementuje `INullable`, `DBNull.Value` je má odpovídající silného typu hodnotu Null.</span><span class="sxs-lookup"><span data-stu-id="87cf3-149">If the type implements `INullable`, `DBNull.Value` is coerced into the appropriate strongly typed Null value.</span></span>  
  
 `SqlType.Null`  
 <span data-ttu-id="87cf3-150">Všechny <xref:System.Data.SqlTypes> implementovat datové typy `INullable`.</span><span class="sxs-lookup"><span data-stu-id="87cf3-150">All <xref:System.Data.SqlTypes> data types implement `INullable`.</span></span> <span data-ttu-id="87cf3-151">Pokud hodnotu silného typu null můžete převést na datový typ sloupce pomocí operátory implicitního přetypování, by měl projít přiřazení.</span><span class="sxs-lookup"><span data-stu-id="87cf3-151">If the strongly typed null value can be converted into the column's data type using implicit cast operators, the assignment should go through.</span></span> <span data-ttu-id="87cf3-152">V opačném případě je vyvolána výjimka neplatné přetypování.</span><span class="sxs-lookup"><span data-stu-id="87cf3-152">Otherwise an invalid cast exception is thrown.</span></span>  
  
 `null`  
 <span data-ttu-id="87cf3-153">Pokud "null" není platnou hodnotou pro v dané `DataColumn` datový typ, je do příslušné má `DbNull.Value` nebo `Null` přidružené `INullable` typu (`SqlType.Null`)</span><span class="sxs-lookup"><span data-stu-id="87cf3-153">If 'null' is a legal value for the given `DataColumn` data type, it is coerced into the appropriate `DbNull.Value` or `Null` associated with the `INullable` type (`SqlType.Null`)</span></span>  
  
 `derivedUdt.Null`  
 <span data-ttu-id="87cf3-154">Pro UDT sloupce jsou hodnoty Null vždy uloženy na základě typu přidružené `DataColumn`.</span><span class="sxs-lookup"><span data-stu-id="87cf3-154">For UDT columns, nulls are always stored based on the type associated with the `DataColumn`.</span></span> <span data-ttu-id="87cf3-155">Podívejte se UDT přidružené `DataColumn` který neimplementuje `INullable` při jeho dílčí třída nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="87cf3-155">Consider the case of a UDT associated with a `DataColumn` that does not implement `INullable` while its sub-class does.</span></span> <span data-ttu-id="87cf3-156">V takovém případě pokud má přiřazenou hodnotu silného typu null přidružené odvozené třídy, bude uložena jako netypové `DbNull.Value`, protože je vždy v souladu s sloupci DataColumn datový typ úložiště hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="87cf3-156">In this case, if a strongly typed null value associated with the derived class is assigned, it is stored as an untyped `DbNull.Value`, because null storage is always consistent with the DataColumn's data type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="87cf3-157">`Nullable<T>` Nebo <xref:System.Nullable> struktura aktuálně nepodporuje `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="87cf3-157">The `Nullable<T>` or <xref:System.Nullable> structure is not currently supported in the `DataSet`.</span></span>  
  
### <a name="multiple-column-row-assignment"></a><span data-ttu-id="87cf3-158">Více přiřazení sloupec (řádek)</span><span class="sxs-lookup"><span data-stu-id="87cf3-158">Multiple Column (Row) Assignment</span></span>  
 <span data-ttu-id="87cf3-159">`DataTable.Add`, `DataTable.LoadDataRow`, nebo jiná rozhraní API, které přijímají <xref:System.Data.DataRow.ItemArray%2A> , získá namapovaná na řádek, mapy null na sloupci DataColumn výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="87cf3-159">`DataTable.Add`, `DataTable.LoadDataRow`, or other APIs that accept an <xref:System.Data.DataRow.ItemArray%2A> that gets mapped to a row, map 'null' to the DataColumn's default value.</span></span> <span data-ttu-id="87cf3-160">Pokud obsahuje objekt v poli `DbNull.Value` nebo se použijí jeho protějšek silného typu, stejná pravidla jak je popsáno výše.</span><span class="sxs-lookup"><span data-stu-id="87cf3-160">If an object in the array contains `DbNull.Value` or its strongly typed counterpart, the same rules as described above are applied.</span></span>  
  
 <span data-ttu-id="87cf3-161">Kromě toho platí následující pravidla pro instanci `DataRow.["columnName"]` null přiřazení:</span><span class="sxs-lookup"><span data-stu-id="87cf3-161">In addition, the following rules apply for an instance of `DataRow.["columnName"]` null assignments:</span></span>  
  
1.  <span data-ttu-id="87cf3-162">Výchozí hodnota *výchozí* hodnota je `DbNull.Value` pro všechny kromě silného typu null sloupce tam, kde je odpovídající silně typované hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="87cf3-162">The default *default* value is `DbNull.Value` for all except the strongly typed null columns where it is the appropriate strongly typed null value.</span></span>  
  
2.  <span data-ttu-id="87cf3-163">Hodnoty Null se nikdy zapisují během serializace za účelem souborů XML (jako "xsi: nil").</span><span class="sxs-lookup"><span data-stu-id="87cf3-163">Null values are never written out during serialization to XML files (as in "xsi:nil").</span></span>  
  
3.  <span data-ttu-id="87cf3-164">Všechny hodnoty null, včetně výchozí hodnoty, jsou vždy zapsána při serializaci do formátu XML.</span><span class="sxs-lookup"><span data-stu-id="87cf3-164">All non-null values, including defaults, are always written out while serializing to XML.</span></span> <span data-ttu-id="87cf3-165">To je rozdíl oproti sémantiku XSD/XML, kde je explicitní hodnotu null (xsi: nil) a výchozí hodnota je implicitní (Pokud není přítomný v XML, ověřuje analyzátor můžete ho získat prostřednictvím přidruženému schématu XSD).</span><span class="sxs-lookup"><span data-stu-id="87cf3-165">This is unlike XSD/XML semantics where a null value (xsi:nil) is explicit and the default value is implicit (if not present in XML, a validating parser can get it from an associated XSD schema).</span></span> <span data-ttu-id="87cf3-166">Jako opak platí pro `DataTable`: hodnota null je implicitní a explicitní je výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="87cf3-166">The opposite is true for a `DataTable`: a null value is implicit and the default value is explicit.</span></span>  
  
4.  <span data-ttu-id="87cf3-167">Všechny chybějící hodnoty sloupce pro čtení z vstup XML řádky jsou přiřadit hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="87cf3-167">All missing column values for rows read from XML input are assigned NULL.</span></span> <span data-ttu-id="87cf3-168">Řádky, které jsou vytvořené pomocí <xref:System.Data.DataTable.NewRow%2A> nebo podobné metody jsou přiřazeny sloupci DataColumn výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="87cf3-168">Rows created using <xref:System.Data.DataTable.NewRow%2A> or similar methods are assigned the DataColumn's default value.</span></span>  
  
5.  <span data-ttu-id="87cf3-169"><xref:System.Data.DataRow.IsNull%2A> Metoda vrátí `true` pro obě `DbNull.Value` a `INullable.Null`.</span><span class="sxs-lookup"><span data-stu-id="87cf3-169">The <xref:System.Data.DataRow.IsNull%2A> method returns `true` for both `DbNull.Value` and `INullable.Null`.</span></span>  
  
## <a name="assigning-null-values"></a><span data-ttu-id="87cf3-170">Přiřazení hodnoty Null</span><span class="sxs-lookup"><span data-stu-id="87cf3-170">Assigning Null Values</span></span>  
 <span data-ttu-id="87cf3-171">Výchozí hodnota pro některý <xref:System.Data.SqlTypes> instance je null.</span><span class="sxs-lookup"><span data-stu-id="87cf3-171">The default value for any <xref:System.Data.SqlTypes> instance is null.</span></span>  
  
 <span data-ttu-id="87cf3-172">Hodnoty Null v <xref:System.Data.SqlTypes> jsou specifické pro typ a nemůže být reprezentovaná jednu hodnotu, jako například `DbNull`.</span><span class="sxs-lookup"><span data-stu-id="87cf3-172">Nulls in <xref:System.Data.SqlTypes> are type-specific and cannot be represented by a single value, such as `DbNull`.</span></span> <span data-ttu-id="87cf3-173">Použití `IsNull` vlastnost zkontrolujte hodnoty Null.</span><span class="sxs-lookup"><span data-stu-id="87cf3-173">Use the `IsNull` property to check for nulls.</span></span>  
  
 <span data-ttu-id="87cf3-174">Hodnoty Null lze přiřadit k <xref:System.Data.DataColumn> jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="87cf3-174">Null values can be assigned to a <xref:System.Data.DataColumn> as shown in the following code example.</span></span> <span data-ttu-id="87cf3-175">Můžete přímo přiřadit hodnoty null do `SqlTypes` proměnné bez vyvolání k výjimce.</span><span class="sxs-lookup"><span data-stu-id="87cf3-175">You can directly assign null values to `SqlTypes` variables without triggering an exception.</span></span>  
  
### <a name="example"></a><span data-ttu-id="87cf3-176">Příklad</span><span class="sxs-lookup"><span data-stu-id="87cf3-176">Example</span></span>  
 <span data-ttu-id="87cf3-177">Následující příklad kódu vytvoří <xref:System.Data.DataTable> s dva sloupce, které jsou definované jako <xref:System.Data.SqlTypes.SqlInt32> a <xref:System.Data.SqlTypes.SqlString>.</span><span class="sxs-lookup"><span data-stu-id="87cf3-177">The following code example creates a <xref:System.Data.DataTable> with two columns defined as <xref:System.Data.SqlTypes.SqlInt32> and <xref:System.Data.SqlTypes.SqlString>.</span></span> <span data-ttu-id="87cf3-178">Kód přidá jeden řádek známé hodnoty, jeden řádek Null hodnoty a pak provádí iteraci <xref:System.Data.DataTable>, přiřazení hodnoty k proměnné a zobrazení výstupu v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="87cf3-178">The code adds one row of known values, one row of null values and then iterates through the <xref:System.Data.DataTable>, assigning the values to variables and displaying the output in the console window.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 <span data-ttu-id="87cf3-179">Tento příklad zobrazí následující výsledky:</span><span class="sxs-lookup"><span data-stu-id="87cf3-179">This example displays the following results:</span></span>  
  
```  
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a><span data-ttu-id="87cf3-180">Porovnání hodnoty Null s SqlTypes a typy CLR</span><span class="sxs-lookup"><span data-stu-id="87cf3-180">Comparing Null Values with SqlTypes and CLR Types</span></span>  
 <span data-ttu-id="87cf3-181">Při porovnávání hodnoty null, je důležité si uvědomit rozdíl mezi způsob, jakým `Equals` metoda vyhodnotí hodnoty null v <xref:System.Data.SqlTypes> ve srovnání s způsob, jak to funguje s typy CLR.</span><span class="sxs-lookup"><span data-stu-id="87cf3-181">When comparing null values, it is important to understand the difference between the way the `Equals` method evaluates null values in <xref:System.Data.SqlTypes> as compared with the way it works with CLR types.</span></span> <span data-ttu-id="87cf3-182">Všechny <xref:System.Data.SqlTypes> `Equals` metody používají sémantiku databáze pro vyhodnocení hodnoty null: Pokud má jednu nebo obě hodnoty hodnotu null, je výsledkem porovnávání vypočítá hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="87cf3-182">All of the <xref:System.Data.SqlTypes>`Equals` methods use database semantics for evaluating null values: if either or both of the values is null, the comparison yields null.</span></span> <span data-ttu-id="87cf3-183">Na druhé straně pomocí modulu CLR `Equals` metoda na dva <xref:System.Data.SqlTypes> předá hodnotu true, pokud jsou obě hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="87cf3-183">On the other hand, using the CLR `Equals` method on two <xref:System.Data.SqlTypes> will yield true if both are null.</span></span> <span data-ttu-id="87cf3-184">Tento údaj zohledňuje rozdíl mezi použitím metody instance například modulu CLR `String.Equals` metoda a pomocí metody statické nebo sdílené `SqlString.Equals`.</span><span class="sxs-lookup"><span data-stu-id="87cf3-184">This reflects the difference between using an instance method such as the CLR `String.Equals` method, and using the static/shared method, `SqlString.Equals`.</span></span>  
  
 <span data-ttu-id="87cf3-185">Následující příklad ukazuje rozdíl mezi výsledky `SqlString.Equals` metoda a `String.Equals` metoda když každý předána pár hodnoty null a poté páru prázdné řetězce.</span><span class="sxs-lookup"><span data-stu-id="87cf3-185">The following example demonstrates the difference in results between the `SqlString.Equals` method and the `String.Equals` method when each is passed a pair of null values and then a pair of empty strings.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/VB/source.vb#1)]  
  
 <span data-ttu-id="87cf3-186">Kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="87cf3-186">The code produces the following output:</span></span>  
  
```  
SqlString.Equals shared/static method:  
  Two nulls=Null  
  
String.Equals instance method:  
  Two nulls=True  
  
SqlString.Equals shared/static method:  
  Two empty strings=True  
  
String.Equals instance method:  
  Two empty strings=True   
```  
  
## <a name="see-also"></a><span data-ttu-id="87cf3-187">Viz také</span><span class="sxs-lookup"><span data-stu-id="87cf3-187">See Also</span></span>  
 [<span data-ttu-id="87cf3-188">Data serveru SQL typy a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="87cf3-188">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [<span data-ttu-id="87cf3-189">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="87cf3-189">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)