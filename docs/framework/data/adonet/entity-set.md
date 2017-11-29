---
title: sada entit
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59ec6ab0-88e5-4d25-b112-7a4eccbe61f0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6b28be2b3bdddd9457874881e930ea978ef5c2b1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="entity-set"></a><span data-ttu-id="ae21d-102">sada entit</span><span class="sxs-lookup"><span data-stu-id="ae21d-102">entity set</span></span>
<span data-ttu-id="ae21d-103">*Sady entit* je logický kontejner pro instance [typ entity](../../../../docs/framework/data/adonet/entity-type.md) a instancí jakéhokoli typu odvozeného z tohoto typu entity.</span><span class="sxs-lookup"><span data-stu-id="ae21d-103">An *entity set* is a logical container for instances of an [entity type](../../../../docs/framework/data/adonet/entity-type.md) and instances of any type derived from that entity type.</span></span> <span data-ttu-id="ae21d-104">(Informace o odvozené typy najdete v tématu [datového modelu Entity: dědičnosti](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md).) Vztah mezi typem entity a sadu entit je podobná vztah mezi řádek a tabulku v relační databázi: řádek, jako je typ entity popisuje strukturu dat a jako tabulku, obsahuje sadu entit instance dané struktury.</span><span class="sxs-lookup"><span data-stu-id="ae21d-104">(For information about derived types, see [Entity Data Model: Inheritance](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md).) The relationship between an entity type and an entity set is analogous to the relationship between a row and a table in a relational database: Like a row, an entity type describes data structure, and, like a table, an entity set contains instances of a given structure.</span></span> <span data-ttu-id="ae21d-105">Sadu entit není dat modelování konstrukce; Struktura dat nepopisuje.</span><span class="sxs-lookup"><span data-stu-id="ae21d-105">An entity set is not a data modeling construct; it does not describe the structure of data.</span></span> <span data-ttu-id="ae21d-106">Místo toho sadu entit poskytuje konstrukt pro hostování nebo úložiště prostředí (například databáze SQL serveru nebo modul common language runtime) k instancím typu entity skupiny tak, aby se můžete namapovat k úložišti dat.</span><span class="sxs-lookup"><span data-stu-id="ae21d-106">Instead, an entity set provides a construct for a hosting or storage environment (such as the common language runtime or a SQL Server database) to group entity type instances so that they can be mapped to a data store.</span></span>  
  
 <span data-ttu-id="ae21d-107">Sadu entit je definována v rámci [kontejneru entit](../../../../docs/framework/data/adonet/entity-container.md), což je logické seskupení sad entit a [nastaví přidružení](../../../../docs/framework/data/adonet/association-set.md).</span><span class="sxs-lookup"><span data-stu-id="ae21d-107">An entity set is defined within an [entity container](../../../../docs/framework/data/adonet/entity-container.md), which is a logical grouping of entity sets and [association sets](../../../../docs/framework/data/adonet/association-set.md).</span></span>  
  
 <span data-ttu-id="ae21d-108">Instance typu entity existovat v sadu entit musí být splněné následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="ae21d-108">For an entity type instance to exist in an entity set, the following must be true:</span></span>  
  
-   <span data-ttu-id="ae21d-109">Typ instance je buď stejný jako typ entity, na kterém je na základě sady entit nebo typ instance není podtypem typ entity.</span><span class="sxs-lookup"><span data-stu-id="ae21d-109">The type of the instance is either the same as the entity type on which the entity set is based, or the type of the instance is a subtype of the entity type.</span></span>  
  
-   <span data-ttu-id="ae21d-110">[Klíč entity](../../../../docs/framework/data/adonet/entity-key.md) pro instance je jedinečné v rámci sady entit.</span><span class="sxs-lookup"><span data-stu-id="ae21d-110">The [entity key](../../../../docs/framework/data/adonet/entity-key.md) for the instance is unique within the entity set.</span></span>  
  
-   <span data-ttu-id="ae21d-111">Instance neexistuje v jiné sadě entit.</span><span class="sxs-lookup"><span data-stu-id="ae21d-111">The instance does not exist in any other entity set.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ae21d-112">Několik sad entit lze definovat pomocí stejného typu entity, ale může existovat pouze instance typu danou entitu v sadě jednu entitu.</span><span class="sxs-lookup"><span data-stu-id="ae21d-112">Multiple entity sets can be defined using the same entity type, but an instance of a given entity type can only exist in one entity set.</span></span>  
  
 <span data-ttu-id="ae21d-113">Nemusíte definovat entitu ke každému typu entity v konceptuálním modelu.</span><span class="sxs-lookup"><span data-stu-id="ae21d-113">You do not have to define an entity set for each entity type in a conceptual model.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae21d-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="ae21d-114">Example</span></span>  
 <span data-ttu-id="ae21d-115">Následující diagram znázorňuje Koncepční model se tři typy entit: `Book`, `Publisher`, a `Author`.</span><span class="sxs-lookup"><span data-stu-id="ae21d-115">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  
  
 <span data-ttu-id="ae21d-116">![Ukázkový Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="ae21d-116">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="ae21d-117">Následující diagram znázorňuje dvě sady entit (`Books` a `Publishers`) a nastavená přidružení (`PublishedBy`) na základě konceptuálního modelu uvedené výše.</span><span class="sxs-lookup"><span data-stu-id="ae21d-117">The following diagram shows two entity sets (`Books` and `Publishers`) and an association set (`PublishedBy`) based on the conceptual model shown above.</span></span> <span data-ttu-id="ae21d-118">BI v `Books` sady entit představuje instanci `Book` typ entity v době běhu.</span><span class="sxs-lookup"><span data-stu-id="ae21d-118">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="ae21d-119">Podobně Pj představují `Publisher` instance v `Publishers` sady entit.</span><span class="sxs-lookup"><span data-stu-id="ae21d-119">Similarly, Pj represent a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="ae21d-120">BiPj představuje instanci `PublishedBy` přidružení v `PublishedBy` sadu přidružení.</span><span class="sxs-lookup"><span data-stu-id="ae21d-120">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 <span data-ttu-id="ae21d-121">![Nastaví příklad](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")</span><span class="sxs-lookup"><span data-stu-id="ae21d-121">![Sets Example](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")</span></span>  
  
 <span data-ttu-id="ae21d-122">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá specifické pro doménu jazyka (DSL) nazývaného konceptuálního schématu definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelech.</span><span class="sxs-lookup"><span data-stu-id="ae21d-122">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="ae21d-123">Následující CSDL definuje jednu sadu entit pro každý typ entity v konceptuálním modelu výše uvedeném kontejner entity.</span><span class="sxs-lookup"><span data-stu-id="ae21d-123">The following CSDL defines an entity container with one entity set for each entity type in the conceptual model shown above.</span></span> <span data-ttu-id="ae21d-124">Všimněte si, že název a entity zadejte pro každou sadu entit jsou definovány pomocí atributy XML.</span><span class="sxs-lookup"><span data-stu-id="ae21d-124">Note that the name and entity type for each entity set are defined using XML attributes.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 <span data-ttu-id="ae21d-125">Je možné definovat několik sad entit na typ (MEST).</span><span class="sxs-lookup"><span data-stu-id="ae21d-125">It is possible to define multiple entity sets per type (MEST).</span></span> <span data-ttu-id="ae21d-126">Následující CSDL definuje kontejner entity dvě sady entit pro `Book` typ entity:</span><span class="sxs-lookup"><span data-stu-id="ae21d-126">The following CSDL defines an entity container with two entity sets for the `Book` entity type:</span></span>  
  
 [!code-xml[EDM_Example_Model#MESTExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#mestexample)]  
  
## <a name="see-also"></a><span data-ttu-id="ae21d-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="ae21d-127">See Also</span></span>  
 [<span data-ttu-id="ae21d-128">Entity Data Model klíčové koncepty</span><span class="sxs-lookup"><span data-stu-id="ae21d-128">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="ae21d-129">Datového modelu entity</span><span class="sxs-lookup"><span data-stu-id="ae21d-129">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)