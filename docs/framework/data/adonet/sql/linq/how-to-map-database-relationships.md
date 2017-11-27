---
title: "Postupy: mapování relace databáze"
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
ms.assetid: 538def39-8399-46fb-b02d-60ede4e050af
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: aa771fbde889febb269f49603f7d2a2ac5c67784
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-map-database-relationships"></a><span data-ttu-id="f2f62-102">Postupy: mapování relace databáze</span><span class="sxs-lookup"><span data-stu-id="f2f62-102">How to: Map Database Relationships</span></span>
<span data-ttu-id="f2f62-103">Můžete zakódovat jako odkazuje vlastnost v třídě entity žádné vztahy dat, které budou vždy stejné.</span><span class="sxs-lookup"><span data-stu-id="f2f62-103">You can encode as property references in your entity class any data relationships that will always be the same.</span></span> <span data-ttu-id="f2f62-104">Ukázková databáze Northwind například vzhledem k tomu, že zákazníci obvykle umístit objednávky, je vždy vztah v modelu mezi zákazníků a jejich objednávky.</span><span class="sxs-lookup"><span data-stu-id="f2f62-104">In the Northwind sample database, for example, because customers typically place orders, there is always a relationship in the model between customers and their orders.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="f2f62-105">definuje <xref:System.Data.Linq.Mapping.AssociationAttribute> atribut pomohou představují takové vztahy.</span><span class="sxs-lookup"><span data-stu-id="f2f62-105"> defines an <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute to help represent such relationships.</span></span> <span data-ttu-id="f2f62-106">Tento atribut slouží společně s <xref:System.Data.Linq.EntitySet%601> a <xref:System.Data.Linq.EntityRef%601> typy představují, co by relace cizího klíče v databázi.</span><span class="sxs-lookup"><span data-stu-id="f2f62-106">This attribute is used together with the <xref:System.Data.Linq.EntitySet%601> and <xref:System.Data.Linq.EntityRef%601> types to represent what would be a foreign key relationship in a database.</span></span> <span data-ttu-id="f2f62-107">Další informace najdete v tématu části přidružení atribut [na základě atributů mapování](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="f2f62-107">For more information, see the Association Attribute section of [Attribute-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2f62-108">Hodnoty vlastností AssociationAttribute a ColumnAttribute úložiště rozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="f2f62-108">AssociationAttribute and ColumnAttribute Storage property values are case sensitive.</span></span> <span data-ttu-id="f2f62-109">Například zajistěte, že hodnoty atributu pro vlastnost AssociationAttribute.Storage malá a velká písmena pro odpovídající vlastnost názvy používá někde v kódu.</span><span class="sxs-lookup"><span data-stu-id="f2f62-109">For example, ensure that values used in the attribute for the AssociationAttribute.Storage property match the case for the corresponding property names used elsewhere in the code.</span></span> <span data-ttu-id="f2f62-110">To platí pro všechny programovacích jazyků .NET, včetně těch, které nejsou obvykle velká a malá písmena, včetně [!INCLUDE[vb_current_short](../../../../../../includes/vb-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f2f62-110">This applies to all .NET programming languages, even those which are not typically case sensitive, including [!INCLUDE[vb_current_short](../../../../../../includes/vb-current-short-md.md)].</span></span> <span data-ttu-id="f2f62-111">Další informace o vlastnosti úložiště najdete v tématu <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f2f62-111">For more information about the Storage property, see <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="f2f62-112">Jeden mnoho, jako v příkladu dále v tomto tématu se většina vztahy.</span><span class="sxs-lookup"><span data-stu-id="f2f62-112">Most relationships are one-to-many, as in the example later in this topic.</span></span> <span data-ttu-id="f2f62-113">Můžete také představovat relace 1: 1 a m: n následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f2f62-113">You can also represent one-to-one and many-to-many relationships as follows:</span></span>  
  
-   <span data-ttu-id="f2f62-114">1: 1: Tento typ vztahu představují zahrnutím <xref:System.Data.Linq.EntitySet%601> na obou stranách.</span><span class="sxs-lookup"><span data-stu-id="f2f62-114">One-to-one: Represent this kind of relationship by including <xref:System.Data.Linq.EntitySet%601> on both sides.</span></span>  
  
     <span data-ttu-id="f2f62-115">Představte si třeba `Customer` - `SecurityCode` relace vytvořená tak, aby zákazníka bezpečnostní kód nebude nalezeno v `Customer` tabulky a lze k němu přístup pouze oprávněných osob.</span><span class="sxs-lookup"><span data-stu-id="f2f62-115">For example, consider a `Customer`-`SecurityCode` relationship, created so that the customer's security code will not be found in the `Customer` table and can be accessed only by authorized persons.</span></span>  
  
-   <span data-ttu-id="f2f62-116">M m: V relace m: n, primární klíč tabulky odkaz (také s názvem *spojení* tabulky) je často formátu složeného cizího klíče z obou tabulek.</span><span class="sxs-lookup"><span data-stu-id="f2f62-116">Many-to-many: In many-to-many relationships, the primary key of the link table (also named the *junction* table) is often formed by a composite of the foreign keys from the other two tables.</span></span>  
  
     <span data-ttu-id="f2f62-117">Představte si třeba `Employee` - `Project` relace m: n vytvořená pomocí tabulky odkaz `EmployeeProject`.</span><span class="sxs-lookup"><span data-stu-id="f2f62-117">For example, consider an `Employee`-`Project` many-to-many relationship formed by using link table `EmployeeProject`.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="f2f62-118">vyžaduje, aby takové relace modelovat pomocí tří tříd: `Employee`, `Project`, a `EmployeeProject`.</span><span class="sxs-lookup"><span data-stu-id="f2f62-118"> requires that such a relationship be modeled by using three classes: `Employee`, `Project`, and `EmployeeProject`.</span></span> <span data-ttu-id="f2f62-119">V takovém případě změna vztah mezi `Employee` a `Project` můžete zobrazit tak, aby vyžadovala aktualizace primární klíč `EmployeeProject`.</span><span class="sxs-lookup"><span data-stu-id="f2f62-119">In this case, changing the relationship between an `Employee` and a `Project` can appear to require an update of the primary key `EmployeeProject`.</span></span> <span data-ttu-id="f2f62-120">Však tato situace je nejlépe modelován jako odstranění existující `EmployeeProject` a vytvoření nové `EmployeeProject`.</span><span class="sxs-lookup"><span data-stu-id="f2f62-120">However, this situation is best modeled as deleting an existing `EmployeeProject` and the creating a new `EmployeeProject`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f2f62-121">Vztahy v relačních databází jsou obvykle modelován jako hodnoty cizího klíče, které odkazují na primárních klíčů v jiné tabulky.</span><span class="sxs-lookup"><span data-stu-id="f2f62-121">Relationships in relational databases are typically modeled as foreign key values that refer to primary keys in other tables.</span></span> <span data-ttu-id="f2f62-122">Umožňují přecházet mezi jednotlivými je explicitně přidružíte dvě tabulky pomocí relační *spojení* operaci.</span><span class="sxs-lookup"><span data-stu-id="f2f62-122">To navigate between them you explicitly associate the two tables by using a relational *join* operation.</span></span>  
    >   
    >  <span data-ttu-id="f2f62-123">Objekty v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], na dalším ruční, odkazovat navzájem pomocí vlastnosti odkazy nebo kolekce odkazy, které přejdete pomocí *tečkou* zápis.</span><span class="sxs-lookup"><span data-stu-id="f2f62-123">Objects in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], on the other hand, refer to each other by using property references or collections of references that you navigate by using *dot* notation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2f62-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="f2f62-124">Example</span></span>  
 <span data-ttu-id="f2f62-125">V následujícím příkladu jeden mnoho `Customer` třída obsahuje vlastnosti, který deklaruje vztah mezi zákazníků a jejich objednávky.</span><span class="sxs-lookup"><span data-stu-id="f2f62-125">In the following one-to-many example, the `Customer` class has a property that declares the relationship between customers and their orders.</span></span>  <span data-ttu-id="f2f62-126">`Orders` Vlastnost je typu <xref:System.Data.Linq.EntitySet%601>.</span><span class="sxs-lookup"><span data-stu-id="f2f62-126">The `Orders` property is of type <xref:System.Data.Linq.EntitySet%601>.</span></span> <span data-ttu-id="f2f62-127">Tento typ označuje, že je tento vztah jeden mnoho (jedno zákazníka na mnoho objednávky).</span><span class="sxs-lookup"><span data-stu-id="f2f62-127">This type signifies that this relationship is one-to-many (one customer to many orders).</span></span> <span data-ttu-id="f2f62-128"><xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A> Vlastnost se používá k popisu, jak toto přidružení se provádí, konkrétně, tak, že zadáte název vlastnosti v související třídy, který se má porovnat s Tato.</span><span class="sxs-lookup"><span data-stu-id="f2f62-128">The <xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A> property is used to describe how this association is accomplished, namely, by specifying the name of the property in the related class to be compared with this one.</span></span> <span data-ttu-id="f2f62-129">V tomto příkladu `CustomerID` vlastnost porovnání, stejně jako databázi *spojení* by porovnat hodnotě sloupce.</span><span class="sxs-lookup"><span data-stu-id="f2f62-129">In this example, the `CustomerID` property is compared, just as a database *join* would compare that column value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2f62-130">Pokud používáte [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], můžete použít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] k vytvoření přidružení mezi třídami.</span><span class="sxs-lookup"><span data-stu-id="f2f62-130">If you are using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to create an association between classes.</span></span>  
  
 [!code-csharp[DlinqCustomize#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#3)]
 [!code-vb[DlinqCustomize#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="f2f62-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="f2f62-131">Example</span></span>  
 <span data-ttu-id="f2f62-132">Můžete také nechat provést zpětnou situaci.</span><span class="sxs-lookup"><span data-stu-id="f2f62-132">You can also reverse the situation.</span></span> <span data-ttu-id="f2f62-133">Místo použití `Customer` třídy k popisu přidružení mezi zákazníci a objednávky, můžete použít `Order` třídy.</span><span class="sxs-lookup"><span data-stu-id="f2f62-133">Instead of using the `Customer` class to describe the association between customers and orders, you can use the `Order` class.</span></span> <span data-ttu-id="f2f62-134">`Order` Třídy používá <xref:System.Data.Linq.EntityRef%601> typu, který popisuje relace zpět k zákazníka, jako v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="f2f62-134">The `Order` class uses the <xref:System.Data.Linq.EntityRef%601> type to describe the relationship back to the customer, as in the following code example.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2f62-135"><xref:System.Data.Linq.EntityRef%601> Třídy podporuje *odložené načítání*.</span><span class="sxs-lookup"><span data-stu-id="f2f62-135">The <xref:System.Data.Linq.EntityRef%601> class supports *deferred loading*.</span></span> <span data-ttu-id="f2f62-136">Další informace najdete *najdete v části* [odložení versus okamžitou načítání](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="f2f62-136">For more information, *see* [Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span></span>  
  
 [!code-csharp[DLinqCustomize#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#5)]
 [!code-vb[DLinqCustomize#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="f2f62-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2f62-137">See Also</span></span>  
 [<span data-ttu-id="f2f62-138">Postupy: přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="f2f62-138">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)  
 [<span data-ttu-id="f2f62-139">Technologie LINQ to SQL objektový Model</span><span class="sxs-lookup"><span data-stu-id="f2f62-139">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)