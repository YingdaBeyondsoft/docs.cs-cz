---
title: DataTables
ms.date: 03/30/2017
ms.assetid: 52ff0e32-3e5a-41de-9a3b-7b04ea52b83e
ms.openlocfilehash: e148b20c7d8efdb16a897c5606535e4b0112ea29
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32759709"
---
# <a name="datatables"></a>DataTables
A <xref:System.Data.DataSet> se skládá z kolekce tabulek, vztahy a omezení. V technologii ADO.NET <xref:System.Data.DataTable> objekty se používají k vyjádření tabulky v **datovou sadu**. A **DataTable** představuje jednu tabulku v paměti relačních dat; je místní pro data. Aplikace založené na NET, ve kterém se nachází, ale je možné importovat ze zdroje dat, například pomocí systému Microsoft SQL Server **DataAdapter** Další informace najdete v tématu [naplňování datové sady z modul DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md) .  
  
 **DataTable** třída je členem skupiny **System.Data** oboru názvů v knihovně tříd rozhraní .NET Framework. Můžete vytvořit a použít **DataTable** samostatně nebo jako člen skupiny **datovou sadu**, a **DataTable** objekty lze také použít ve spojení s jinými objekty rozhraní .NET Framework včetně <xref:System.Data.DataView>. Přístup kolekce tabulek v **datovou sadu** prostřednictvím **tabulky** vlastnost **datovou sadu** objektu.  
  
 Schéma a struktura tabulky je reprezentována sloupce a omezení. Můžete definovat schéma **DataTable** pomocí <xref:System.Data.DataColumn> objekty a také <xref:System.Data.ForeignKeyConstraint> a <xref:System.Data.UniqueConstraint> objekty. Sloupce v tabulce můžete mapovat na sloupce ve zdroji dat, obsahují počítané hodnoty z výrazů, automaticky zvýšit jejich hodnoty nebo obsahovat hodnot primárního klíče.  
  
 Kromě schématu **DataTable** musí mít také řádky, které obsahují a pořadí data. <xref:System.Data.DataRow> Třída reprezentuje skutečný data obsažená v tabulce. Můžete použít **DataRow** a jeho vlastnosti a metody k načtení, hodnocení a pracovat s daty v tabulce. Při přístupu a při změně data v řádku, **DataRow** objekt udržovat její aktuální a původní stav.  
  
 Můžete vytvořit nadřazený podřízený relace mezi tabulkami pomocí jednoho nebo více souvisejících sloupců v tabulkách. Vytvoření vztahu mezi **DataTable** objekty pomocí <xref:System.Data.DataRelation>. **DataRelation** objekty pak lze vrátit řádky v relaci nadřazená nebo podřízená konkrétního řádku. Další informace najdete v tématu [přidání DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Vytvoření datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datatable.md)  
 Vysvětluje, jak vytvořit **DataTable** a přidejte ho do **datovou sadu**.  
  
 [Definice schématu datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 Poskytuje informace o vytváření a používání **DataColumn** objekty a omezení.  
  
 [Manipulace s daty v datové tabulce](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 Vysvětluje, jak přidat, upravit a odstranit data v tabulce. Vysvětluje, jak používat **DataTable** událostí k prozkoumání změny dat v tabulce.  
  
 [Zpracování událostí datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 Poskytuje informace o událostech, které jsou k dispozici pro použití s **DataTable**, včetně událostí při změně hodnoty sloupců a řádků se přidají nebo odstranit.  
  
## <a name="related-sections"></a>Související oddíly  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)  
 Popisuje technologie ADO.NET architektura a komponenty a jak je používat pro přístup k existující zdroje dat a spravovat data aplikací.  
  
 [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 Poskytuje informace o technologie ADO.NET **datovou sadu** včetně toho, jak vytvořit relace mezi tabulkami.  
  
 <xref:System.Data.Constraint>  
 Poskytuje referenční informace o **omezení** objektu.  
  
 <xref:System.Data.DataColumn>  
 Poskytuje referenční informace o **DataColumn** objektu.  
  
 <xref:System.Data.DataSet>  
 Poskytuje referenční informace o **datovou sadu** objektu.  
  
 <xref:System.Data.DataTable>  
 Poskytuje referenční informace o **DataTable** objektu.  
  
 [Přehled knihovny tříd](../../../../../docs/standard/class-library-overview.md)  
 Najdete zde přehled knihovny tříd rozhraní .NET Framework, včetně **systému** obor názvů a také její obor názvů druhé úrovně **System.Data**.  
  
## <a name="see-also"></a>Viz také  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
