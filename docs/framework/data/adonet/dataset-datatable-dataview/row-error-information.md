---
title: Informace o chybě řádek
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b1f9070-d032-48c7-b030-bd8fbb2ca59a
ms.openlocfilehash: 6f3f332d4b9bd0be9934c7bf7722e8ff71c4eb2f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32767190"
---
# <a name="row-error-information"></a>Informace o chybě řádek
Abyste se vyhnuli nutnosti reagovat na řádek chyby při úpravě hodnoty v <xref:System.Data.DataTable>, informace o chybě můžete přidat na řádek pro pozdější použití. <xref:System.Data.DataRow> Objekt poskytuje <xref:System.Data.DataRow.RowError%2A> vlastnost na každý řádek pro tento účel. Přidání dat do **RowError** vlastnost **DataRow** nastaví <xref:System.Data.DataRow.HasErrors%2A> vlastnost **DataRow** k **true**. Pokud **DataRow** je součástí **DataTable**, a **DataRow.HasErrors** je **true**, **DataTable.HasErrors** vlastnost je také **true**. To platí také pro **datovou sadu** ke kterému **DataTable** patří. Při testování pro nalezení chyb, můžete zkontrolovat **HasErrors** vlastnosti k určení, zda informace o chybě byl přidán k žádnému z řádků. Pokud **HasErrors** je **true**, můžete použít <xref:System.Data.DataTable.GetErrors%2A> metodu **DataTable** a vrátit pouze sloupce s chybami, zkontrolujte, jak je znázorněno v následujícím příkladu.  
  
```vb  
Dim workTable As DataTable = New DataTable("Customers")  
workTable.Columns.Add("CustID", Type.GetType("System.Int32"))  
workTable.Columns.Add("Total", Type.GetType("System.Double"))  
  
AddHandler workTable.RowChanged, New DataRowChangeEventHandler(AddressOf OnRowChanged)  
  
Dim i  As Int32  
  
For i  = 0 To 10  
  workTable.Rows.Add(New Object() {i , i *100})  
Next  
  
If workTable.HasErrors Then  
  Console.WriteLine("Errors in Table " & workTable.TableName)  
  
  Dim myRow As DataRow  
  
  For Each myRow In workTable.GetErrors()  
    Console.WriteLine("CustID = " & myRow("CustID").ToString())  
    Console.WriteLine(" Error = " & myRow.RowError & vbCrLf)  
  Next  
End If  
  
Private Shared Sub OnRowChanged( _  
    sender As Object, args As DataRowChangeEventArgs)  
  ' Check for zero values.  
  If CDbl(args.Row("Total")) = 0 Then args.Row.RowError = _  
      "Total cannot be 0."  
End Sub  
```  
  
```csharp  
DataTable  workTable = new DataTable("Customers");  
workTable.Columns.Add("CustID", typeof(Int32));  
workTable.Columns.Add("Total", typeof(Double));  
  
workTable.RowChanged += new DataRowChangeEventHandler(OnRowChanged);  
  
for (int i = 0; i < 10; i++)  
  workTable.Rows.Add(new Object[] {i, i*100});  
  
if (workTable.HasErrors)  
{  
  Console.WriteLine("Errors in Table " + workTable.TableName);  
  
  foreach (DataRow myRow in workTable.GetErrors())  
  {  
    Console.WriteLine("CustID = " + myRow["CustID"]);  
    Console.WriteLine(" Error = " + myRow.RowError + "\n");  
  }  
}  
  
protected static void OnRowChanged(  
    Object sender, DataRowChangeEventArgs args)  
{  
  // Check for zero values.  
  if (args.Row["Total"].Equals(0D))  
    args.Row.RowError = "Total cannot be 0.";  
}  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataTable>  
 [Manipulace s daty v datové tabulce](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
