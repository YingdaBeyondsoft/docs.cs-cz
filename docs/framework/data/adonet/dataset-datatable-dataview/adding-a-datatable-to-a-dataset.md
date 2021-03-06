---
title: Přidání DataTable do datové sady
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 556d29a3-8fc9-4e38-b3ee-c188f7e7b155
ms.openlocfilehash: 3554790bb65310031b00ca5fb320aa4c111e1e11
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758539"
---
# <a name="adding-a-datatable-to-a-dataset"></a>Přidání DataTable do datové sady
ADO.NET umožňuje vytvářet <xref:System.Data.DataTable> objekty a přidat je do existujícího <xref:System.Data.DataSet>. Můžete nastavit omezení informace <xref:System.Data.DataTable> pomocí <xref:System.Data.DataTable.PrimaryKey%2A> a <xref:System.Data.DataColumn.Unique%2A> vlastnosti.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Data.DataSet>, přidá nový <xref:System.Data.DataTable> do objektu <xref:System.Data.DataSet>a potom přidá tři <xref:System.Data.DataColumn> objekty, které se v tabulce. Nakonec kód nastaví jeden sloupec jako sloupec primárního klíče.  
  
 [!code-csharp[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/VB/source.vb#1)]  
  
## <a name="case-sensitivity"></a>Rozlišování velkých a malých písmen  
 Dvě nebo více tabulek nebo vztahy se stejným názvem, ale jiné velká a malá písmena, může existovat v <xref:System.Data.DataSet>. V takových případech odkazy podle názvu tabulky a relace je malá a velká písmena. Například pokud <xref:System.Data.DataSet> **datovou sadu** obsahuje tabulky **tabulky1** a **tabulky1**, by odkazujete **tabulky1** podle názvu jako **dataSet.Tables["Table1"]**, a **tabulky1** jako **dataSet.Tables["table1"]**. Pokus o jednu z tabulek jako odkaz na **dataSet.Tables["TABLE1"]** by generovat výjimku.  
  
 Chování rozlišování neplatí, pokud pouze jednu tabulku nebo relaci má určitý název. Například pokud <xref:System.Data.DataSet> je k dispozici pouze **tabulky1**, můžete odkazovat pomocí **dataSet.Tables["TABLE1"]**.  
  
> [!NOTE]
>  <xref:System.Data.DataSet.CaseSensitive%2A> Vlastnost <xref:System.Data.DataSet> nemá vliv na toto chování. <xref:System.Data.DataSet.CaseSensitive%2A> Vlastnost se vztahuje na data v <xref:System.Data.DataSet> a ovlivňuje řazení, hledání, filtrování, vynucení omezení a tak dále.  
  
## <a name="namespace-support"></a>Podpora Namespace  
 Ve verzích ADO.NET starších než 2.0 dvě tabulky nelze mít stejný název, i v případě, že byly v různých oborech názvů. Toto omezení byla odebrána v ADO.NET 2.0. A <xref:System.Data.DataSet> může obsahovat dvě tabulky, které mají stejnou <xref:System.Data.DataTable.TableName%2A> hodnotu vlastnosti, ale jiné <xref:System.Data.DataTable.Namespace%2A> hodnot vlastností.  
  
## <a name="see-also"></a>Viz také  
 [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
