---
title: Práce s Data Definition Language
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec50083d-44f4-4093-9b23-5eacd601f96e
ms.openlocfilehash: c6b3151a95f949100e10e630da848e34ebbf1187
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764395"
---
# <a name="working-with-data-definition-language"></a>Práce s Data Definition Language
Od verze [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] verze 4, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] podporuje jazyk definice dat (DDL). To vám umožňuje vytvořit nebo odstranit instanci databáze na základě připojovací řetězec a metadata modelu úložiště (SSDL).  
  
 Následující metody na <xref:System.Data.Objects.ObjectContext> pomůže provést následující připojovací řetězec a obsah SSDL: vytvoření nebo odstranění databáze, zkontrolujte, zda databáze existuje a zobrazit generovaného skriptu DDL:  
  
-   <xref:System.Data.Objects.ObjectContext.CreateDatabase%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.CreateDatabaseScript%2A>  
  
> [!NOTE]
>  Provádění příkazů DDL předpokládá dostatečná oprávnění.  
  
 Metody dříve uvedených delegovat většinu práce na základní zprostředkovatel dat ADO.NET. Je zodpovědností poskytovatele pro zajištění souladu s konvencemi použitými pro dotazování na zásady vytváření názvů sloužící ke generování databázové objekty a aktualizace.  
  
 Následující příklad ukazuje, jak vygenerovat databázi založenou na stávající modelu. Také přidá nový objekt entity do kontextu objektu a pak ji uloží je do databáze.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-define-a-database-based-on-the-existing-model"></a>Chcete-li definovat databázi založenou na stávající modelu  
  
1.  Vytvořte konzolovou aplikaci.  
  
2.  Přidání existujícího modelu do aplikace.  
  
    1.  Přidat prázdný model s názvem `SchoolModel`. Pokud chcete vytvořit prázdný model, přečtěte si téma [postup: vytvoření nové .edmx souboru](http://msdn.microsoft.com/library/beb8189e-e51c-4051-839c-9902c224abf2) tématu.  
  
     Soubor SchoolModel.edmx je přidán do projektu.  
  
    1.  Zkopírujte koncepční, úložiště a mapování obsahu pro model školní ze [školní modelu](http://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac) tématu.  
  
    2.  Otevřete soubor SchoolModel.edmx a vložte obsah v rámci `edmx:Runtime` značky.  
  
3.  Přidejte následující kód do hlavní funkce. Kód inicializuje připojovací řetězec k databázovému serveru, zobrazení skriptu DDL vytvoří databázi, přidá novou entitu do kontextu a uloží změny do databáze.  
  
     [!code-csharp[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/csharp/VS_Snippets_Data/DP ObjectServices Concepts/CS/Source.cs#ddl)]
     [!code-vb[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP ObjectServices Concepts/VB/Source.vb#ddl)]
