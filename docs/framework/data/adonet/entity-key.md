---
title: klíč entity
ms.date: 03/30/2017
ms.assetid: 0d447a6d-fa7a-4db0-8e7a-fd45e385fca0
ms.openlocfilehash: 6b4e3c6876aa3de1661d680d79caa3116550e073
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764993"
---
# <a name="entity-key"></a>klíč entity
*Klíč entity* je [vlastnost](../../../../docs/framework/data/adonet/property.md) nebo sada vlastností [typ entity](../../../../docs/framework/data/adonet/entity-type.md) , se používají k určení identity. Vlastnosti, které tvoří klíč entity, jsou vybraná v době návrhu. Hodnoty vlastnosti klíče entity musí jednoznačně identifikovat instance typu entity v rámci [sady entit](../../../../docs/framework/data/adonet/entity-set.md) za běhu. Vlastnosti, které tvoří klíč entity je třeba zvolit zaručovat jedinečnost instancí v sadu entit.  
  
 Následují požadavky na sadu vlastností pro být klíč entity:  
  
-   Žádné klíče dvě entity v rámci sadu entit může být identické. To znamená dvě entity v rámci sadu entit, hodnoty pro všechny vlastnosti, které tvoří klíč nesmí být stejné. Ale některé (ale ne všechny) hodnoty, které tvoří entitu klíč může být stejné.  
  
-   Klíč entity musí obsahovat sadu neumožňující hodnotu Null, neměnné, [primitivní typ vlastnosti](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md).  
  
-   Vlastnosti, které tvoří klíčem entity pro danou entitu Typ nelze změnit. Více než jeden klíč možné entity nelze povolit pro danou entitu typu; náhradní klíče nejsou podporovány.  
  
-   Když entity je součástí hierarchie dědičnosti, kořenové entity musí obsahovat všechny vlastnosti, které tvoří klíč entity a klíč musí být definovaný pro kořenové typ entity. Další informace najdete v tématu [datového modelu Entity: dědičnosti](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md).  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje Koncepční model se tři typy entit: `Book`, `Publisher`, a `Author`. Vlastnosti každého typu entity, které tvoří svůj klíč entity, jsou označeny "(klíč)". Všimněte si, že `Author` typ entity má klíč entity, která se skládá ze dvou vlastností `Name` a `Address`.  
  
 ![Ukázkový Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá specifické pro doménu jazyka (DSL) nazývaného konceptuálního schématu definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelech. Definuje CSDL níže `Book` typ entity, které jsou uvedené v diagramu výše. Všimněte si, že klíč entity je definován pod položkou `ISBN` vlastnost typu entity.  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 `ISBN` Vlastnost je vhodná pro klíč entity, protože mezinárodní číslo pro standardní adresáře (ISBN) jednoznačně identifikuje knihy.  
  
 Definuje CSDL níže `Author` typ entity, které jsou uvedené v diagramu výše. Všimněte si, že klíč entity se skládá ze dvou vlastností `Name` a `Address`.  
  
 [!code-xml[EDM_Example_Model#CompositeKeyExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#compositekeyexample)]  
  
 Pomocí `Name` a `Address` pro entitu klíč je vhodná volba, protože je nepravděpodobné, že za provozu na stejnou adresu dva autoři se stejným názvem. Tato volba pro klíč entity, ale v absolutně nezaručuje klíče jedinečné entity v sadu entit. Přidání vlastnosti, jako například `AuthorId`, který může použít k jednoznačné identifikaci Autor doporučenou v tomto případě.  
  
## <a name="see-also"></a>Viz také  
 [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Model EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md)
