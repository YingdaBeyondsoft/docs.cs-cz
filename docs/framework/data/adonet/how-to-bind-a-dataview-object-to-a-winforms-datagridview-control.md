---
title: 'Postupy: vytvoření vazby na objekt DataView do ovládacího prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b73d60a-6049-446a-85a7-3e5a68b183e2
ms.openlocfilehash: 98b3afcded257bc11dc3bca7d9a9310dc1a7cc89
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765019"
---
# <a name="how-to-bind-a-dataview-object-to-a-windows-forms-datagridview-control"></a>Postupy: vytvoření vazby na objekt DataView do ovládacího prvku Windows Forms DataGridView
<xref:System.Windows.Forms.DataGridView> Řízení poskytuje výkonný a flexibilní způsob, jak zobrazit data ve formátu tabulky. <xref:System.Windows.Forms.DataGridView> Řízení podporuje standardní Windows Forms datový model vazby, tak ho vytvoří vazbu k <xref:System.Data.DataView> a různých dalších datových zdrojů. Ve většině případů však vytvoříte vazbu k <xref:System.Windows.Forms.BindingSource> komponenta, která bude spravovat podrobnosti o interakci se zdrojem dat.  
  
 Další informace o <xref:System.Windows.Forms.DataGridView> řízení najdete v tématu [– Přehled ovládacího prvku DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md).  
  
### <a name="to-connect-a-datagridview-control-to-a-dataview"></a>Pro připojení k v zobrazení DataView ovládacího prvku DataGridView  
  
1.  Implementujte metodu pro zpracování podrobnosti načítání dat z databáze. Následující příklad kódu implementuje `GetData` metoda, která inicializuje <xref:System.Data.SqlClient.SqlDataAdapter> součásti a použije ho k zadání <xref:System.Data.DataSet>. Nastavte `connectionString` proměnné na hodnotu, která je vhodná pro vaši databázi. Budete potřebovat přístup k serveru s ukázkovou databází AdventureWorks SQL Server nainstalován.  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1getdata)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1getdata)]  
  
2.  V <xref:System.Windows.Forms.Form.Load> obslužné rutiny události formuláře, vytvořit vazbu <xref:System.Windows.Forms.DataGridView> řídit k <xref:System.Windows.Forms.BindingSource> součásti a volání `GetData` metoda pro načtení dat z databáze. <xref:System.Data.DataView> Je vytvořený z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazu přes kontakt <xref:System.Data.DataTable> a pak je vázána <xref:System.Windows.Forms.BindingSource> součásti.  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1formload)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1formload)]  
  
## <a name="see-also"></a>Viz také  
 [Datová vazba a LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
