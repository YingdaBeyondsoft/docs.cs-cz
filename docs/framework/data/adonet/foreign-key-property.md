---
title: "vlastností cizího klíče"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 626feac70099667e0dc15b12043834bda6d4b20e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="foreign-key-property"></a><span data-ttu-id="5e572-102">vlastností cizího klíče</span><span class="sxs-lookup"><span data-stu-id="5e572-102">foreign key property</span></span>
<span data-ttu-id="5e572-103">A *vlastností cizího klíče* v Entity Data Model (EDM) je primitivní typ [vlastnost](../../../../docs/framework/data/adonet/property.md) (nebo sadu vlastností primitivní typ) na [typ entity](../../../../docs/framework/data/adonet/entity-type.md) obsahující [klíč entity](../../../../docs/framework/data/adonet/entity-key.md) jiného typu entity.</span><span class="sxs-lookup"><span data-stu-id="5e572-103">A *foreign key property* in the Entity Data Model (EDM) is a primitive type [property](../../../../docs/framework/data/adonet/property.md) (or a set of primitive type properties) on an [entity type](../../../../docs/framework/data/adonet/entity-type.md) that contains the [entity key](../../../../docs/framework/data/adonet/entity-key.md) of another entity type.</span></span>  
  
 <span data-ttu-id="5e572-104">Vlastností cizího klíče je podobná sloupec cizího klíče v relační databázi.</span><span class="sxs-lookup"><span data-stu-id="5e572-104">A foreign key property is analogous to a foreign key column in a relational database.</span></span> <span data-ttu-id="5e572-105">Stejným způsobem, že sloupce cizího klíče v relační databázi slouží k vytváření vztahů mezi řádků v tabulkách, vlastnosti cizího klíče v konceptuálním modelu se použijí k vytvoření [přidružení](../../../../docs/framework/data/adonet/association-type.md) mezi typy entit.</span><span class="sxs-lookup"><span data-stu-id="5e572-105">In the same way that foreign key columns are used in a relational database to create relationships between rows in tables, foreign key properties in a conceptual model are used to establish [associations](../../../../docs/framework/data/adonet/association-type.md) between entity types.</span></span> <span data-ttu-id="5e572-106">A [omezení referenční integrity](../../../../docs/framework/data/adonet/referential-integrity-constraint.md) se používá k definování přidružení mezi dvěma typy entit, pokud jeden z typů vlastností cizího klíče.</span><span class="sxs-lookup"><span data-stu-id="5e572-106">A [referential integrity constraint](../../../../docs/framework/data/adonet/referential-integrity-constraint.md) is used to define an association between two entity types when one of the types has a foreign key property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e572-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="5e572-107">Example</span></span>  
 <span data-ttu-id="5e572-108">Následující diagram znázorňuje Koncepční model se tři typy entit: `Book`, `Publisher`, a `Author`.</span><span class="sxs-lookup"><span data-stu-id="5e572-108">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="5e572-109">`Book` Typ entity má vlastnosti, `PublisherId`, klíč entity, který odkazuje `Publisher` typ entity, když definujete omezení referenční integrity na `PublishedBy` přidružení.</span><span class="sxs-lookup"><span data-stu-id="5e572-109">The `Book` entity type has a property, `PublisherId`, that references the entity key of the `Publisher` entity type when you define a referential integrity constraint on the `PublishedBy` association.</span></span>  
  
 <span data-ttu-id="5e572-110">![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")</span><span class="sxs-lookup"><span data-stu-id="5e572-110">![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")</span></span>  
  
 <span data-ttu-id="5e572-111">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá specifické pro doménu jazyka (DSL) nazývaného konceptuálního schématu definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelech.</span><span class="sxs-lookup"><span data-stu-id="5e572-111">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="5e572-112">Následující CSDL používá vlastností cizího klíče `PublisherId` definovat omezení referenční integrity na `PublishedBy` přidružení zobrazí v konceptuálním modelu uvedené výše.</span><span class="sxs-lookup"><span data-stu-id="5e572-112">The following CSDL uses the foreign key property `PublisherId` to define a referential integrity constraint on the `PublishedBy` association shown in the conceptual model shown above.</span></span>  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a><span data-ttu-id="5e572-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="5e572-113">See Also</span></span>  
 [<span data-ttu-id="5e572-114">Entity Data Model klíčové koncepty</span><span class="sxs-lookup"><span data-stu-id="5e572-114">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="5e572-115">Datového modelu entity</span><span class="sxs-lookup"><span data-stu-id="5e572-115">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)