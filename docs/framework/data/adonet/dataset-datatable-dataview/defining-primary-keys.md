---
title: "Definování primárních klíčů"
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
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a2ba353353b52e5a866887e7f0dc4b743e336bd0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="defining-primary-keys"></a><span data-ttu-id="8bed5-102">Definování primárních klíčů</span><span class="sxs-lookup"><span data-stu-id="8bed5-102">Defining Primary Keys</span></span>
<span data-ttu-id="8bed5-103">Tabulka databáze běžně má sloupec nebo skupiny sloupců, která jednoznačně identifikuje každý řádek v tabulce.</span><span class="sxs-lookup"><span data-stu-id="8bed5-103">A database table commonly has a column or group of columns that uniquely identifies each row in the table.</span></span> <span data-ttu-id="8bed5-104">Toto identifikační sloupec nebo skupiny sloupců se nazývá primární klíč.</span><span class="sxs-lookup"><span data-stu-id="8bed5-104">This identifying column or group of columns is called the primary key.</span></span>  
  
 <span data-ttu-id="8bed5-105">Při identifikaci jedné <xref:System.Data.DataColumn> jako <xref:System.Data.DataTable.PrimaryKey%2A> pro <xref:System.Data.DataTable>, v tabulce automaticky nastaví <xref:System.Data.DataColumn.AllowDBNull%2A> vlastnost sloupce, který se **false** a <xref:System.Data.DataColumn.Unique%2A> vlastnost  **Hodnota TRUE,**.</span><span class="sxs-lookup"><span data-stu-id="8bed5-105">When you identify a single <xref:System.Data.DataColumn> as the <xref:System.Data.DataTable.PrimaryKey%2A> for a <xref:System.Data.DataTable>, the table automatically sets the <xref:System.Data.DataColumn.AllowDBNull%2A> property of the column to **false** and the <xref:System.Data.DataColumn.Unique%2A> property to **true**.</span></span> <span data-ttu-id="8bed5-106">Pro sloupec primárního klíče, jenom **AllowDBNull** je automaticky nastavena na **false**.</span><span class="sxs-lookup"><span data-stu-id="8bed5-106">For multiple-column primary keys, only the **AllowDBNull** property is automatically set to **false**.</span></span>  
  
 <span data-ttu-id="8bed5-107">**PrimaryKey** vlastnost <xref:System.Data.DataTable> obdrží jako svou hodnotu pole jednoho či více **DataColumn** objekty, jak je znázorněno v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="8bed5-107">The **PrimaryKey** property of a <xref:System.Data.DataTable> receives as its value an array of one or more **DataColumn** objects, as shown in the following examples.</span></span> <span data-ttu-id="8bed5-108">V prvním příkladu definuje jeden sloupec jako primární klíč.</span><span class="sxs-lookup"><span data-stu-id="8bed5-108">The first example defines a single column as the primary key.</span></span>  
  
```vb  
workTable.PrimaryKey = New DataColumn() {workTable.Columns("CustID")}  
  
' Or  
  
Dim columns(1) As DataColumn  
columns(0) = workTable.Columns("CustID")  
workTable.PrimaryKey = columns  
```  
  
```csharp  
workTable.PrimaryKey = new DataColumn[] {workTable.Columns["CustID"]};  
  
// Or  
  
DataColumn[] columns = new DataColumn[1];  
columns[0] = workTable.Columns["CustID"];  
workTable.PrimaryKey = columns;  
```  
  
 <span data-ttu-id="8bed5-109">V následujícím příkladu definuje dva sloupce jako primární klíč.</span><span class="sxs-lookup"><span data-stu-id="8bed5-109">The following example defines two columns as a primary key.</span></span>  
  
```vb  
workTable.PrimaryKey = New DataColumn() {workTable.Columns("CustLName"), _  
                                         workTable.Columns("CustFName")}  
  
' Or  
  
Dim keyColumn(2) As DataColumn  
keyColumn(0) = workTable.Columns("CustLName")  
keyColumn(1) = workTable.Columns("CustFName")  
workTable.PrimaryKey = keyColumn  
```  
  
```csharp  
workTable.PrimaryKey = new DataColumn[] {workTable.Columns["CustLName"],   
                                         workTable.Columns["CustFName"]};  
  
// Or  
  
DataColumn[] keyColumn = new DataColumn[2];  
keyColumn[0] = workTable.Columns["CustLName"];  
keyColumn[1] = workTable.Columns["CustFName"];  
workTable.PrimaryKey = keyColumn;  
```  
  
## <a name="see-also"></a><span data-ttu-id="8bed5-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="8bed5-110">See Also</span></span>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="8bed5-111">Definice schématu DataTable</span><span class="sxs-lookup"><span data-stu-id="8bed5-111">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [<span data-ttu-id="8bed5-112">DataTables</span><span class="sxs-lookup"><span data-stu-id="8bed5-112">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="8bed5-113">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="8bed5-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)