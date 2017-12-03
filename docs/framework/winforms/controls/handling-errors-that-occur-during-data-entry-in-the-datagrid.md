---
title: "Návod: Zpracování chyb vzniklých při zadávání dat v ovládacím prvku Windows Forms DataGridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- error handling [Windows Forms], dataGridView control
- data grids [Windows Forms], error handling
- DataGridView control [Windows Forms], error handling
- data entry [Windows Forms], error handling
- error handling [Windows Forms], data entry
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 30a68b85-d3af-4946-83c1-1e2d010d0511
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7c602af6799da57fec904c87da7bed77c0040eff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-handling-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="fe327-102">Návod: Zpracování chyb vzniklých při zadávání dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="fe327-102">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="fe327-103">Zpracování chyb z podkladové úložiště dat je povinnou funkci pro zadávání dat aplikace.</span><span class="sxs-lookup"><span data-stu-id="fe327-103">Handling errors from the underlying data store is a required feature for a data-entry application.</span></span> <span data-ttu-id="fe327-104">Windows Forms <xref:System.Windows.Forms.DataGridView> řízení to výrazně usnadňuje díky zpřístupnění <xref:System.Windows.Forms.DataGridView.DataError> událost, která se vyvolá, když zjistí úložiště dat porušení omezení nebo přerušená obchodní pravidlo.</span><span class="sxs-lookup"><span data-stu-id="fe327-104">The Windows Forms <xref:System.Windows.Forms.DataGridView> control makes this easy by exposing the <xref:System.Windows.Forms.DataGridView.DataError> event, which is raised when the data store detects a constraint violation or a broken business rule.</span></span>  
  
 <span data-ttu-id="fe327-105">V tomto návodu se budou načítat řádky z `Customers` tabulky v ukázkové databázi Northwind a jejich zobrazení <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fe327-105">In this walkthrough, you will retrieve rows from the `Customers` table in the Northwind sample database and display them in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="fe327-106">Pokud duplicitní `CustomerID` hodnota je zjištěn během nového řádku nebo upravených stávající řádek, <xref:System.Windows.Forms.DataGridView.DataError> události dojde, který bude zpracován adresou zobrazení <xref:System.Windows.Forms.MessageBox> která popisuje výjimku.</span><span class="sxs-lookup"><span data-stu-id="fe327-106">When a duplicate `CustomerID` value is detected in a new row or an edited existing row, the <xref:System.Windows.Forms.DataGridView.DataError> event will occur, which will be handled by displaying a <xref:System.Windows.Forms.MessageBox> that describes the exception.</span></span>  
  
 <span data-ttu-id="fe327-107">Zkopírujte kód v tomto tématu v jednom seznamu, najdete v části [postupy: zpracování chyb, dojít během zadávání dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/handle-errors-that-occur-during-data-entry-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="fe327-107">To copy the code in this topic as a single listing, see [How to: Handle Errors That Occur During Data Entry in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/handle-errors-that-occur-during-data-entry-in-the-datagrid.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="fe327-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fe327-108">Prerequisites</span></span>  
 <span data-ttu-id="fe327-109">K dokončení tohoto návodu, budete potřebovat:</span><span class="sxs-lookup"><span data-stu-id="fe327-109">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="fe327-110">Přístup k serveru, který má ukázková databáze Northwind SQL Server.</span><span class="sxs-lookup"><span data-stu-id="fe327-110">Access to a server that has the Northwind SQL Server sample database.</span></span>  
  
## <a name="creating-the-form"></a><span data-ttu-id="fe327-111">Vytvoření formuláře</span><span class="sxs-lookup"><span data-stu-id="fe327-111">Creating the Form</span></span>  
  
#### <a name="to-handle-data-entry-errors-in-the-datagridview-control"></a><span data-ttu-id="fe327-112">Zpracování chyb zadávání dat v ovládacím prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="fe327-112">To handle data-entry errors in the DataGridView control</span></span>  
  
1.  <span data-ttu-id="fe327-113">Vytvořte třídu, která je odvozena z <xref:System.Windows.Forms.Form> a obsahuje <xref:System.Windows.Forms.DataGridView> řízení a <xref:System.Windows.Forms.BindingSource> součásti.</span><span class="sxs-lookup"><span data-stu-id="fe327-113">Create a class that derives from <xref:System.Windows.Forms.Form> and contains a <xref:System.Windows.Forms.DataGridView> control and a <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
     <span data-ttu-id="fe327-114">Následující příklad kódu poskytuje základní inicializace a zahrnuje `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="fe327-114">The following code example provides basic initialization and includes a `Main` method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]  
  
2.  <span data-ttu-id="fe327-115">Implementujte metodu v definici třídy svého formuláře pro zpracování podrobnosti o připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="fe327-115">Implement a method in your form's class definition for handling the details of connecting to the database.</span></span>  
  
     <span data-ttu-id="fe327-116">Tento příklad kódu používá `GetData` metodu, která vrátí vyplněná <xref:System.Data.DataTable> objektu.</span><span class="sxs-lookup"><span data-stu-id="fe327-116">This code example uses a `GetData` method that returns a populated <xref:System.Data.DataTable> object.</span></span> <span data-ttu-id="fe327-117">Ujistěte se, že jste nastavili `connectionString` proměnné na hodnotu, která je vhodná pro vaši databázi.</span><span class="sxs-lookup"><span data-stu-id="fe327-117">Be sure that you set the `connectionString` variable to a value that is appropriate for your database.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="fe327-118">Ukládání citlivé informace, jako jsou hesla, v připojovacím řetězci může ovlivnit zabezpečení vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="fe327-118">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="fe327-119">Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení).</span><span class="sxs-lookup"><span data-stu-id="fe327-119">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="fe327-120">Další informace najdete v tématu [chrání informace o připojení](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="fe327-120">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]  
  
3.  <span data-ttu-id="fe327-121">Implementujte obslužnou rutinu pro daný formulář <xref:System.Windows.Forms.Form.Load> událost, která inicializuje <xref:System.Windows.Forms.DataGridView> a <xref:System.Windows.Forms.BindingSource> a nastavuje datové vazby.</span><span class="sxs-lookup"><span data-stu-id="fe327-121">Implement a handler for your form's <xref:System.Windows.Forms.Form.Load> event that initializes the <xref:System.Windows.Forms.DataGridView> and <xref:System.Windows.Forms.BindingSource> and sets up the data binding.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]  
  
4.  <span data-ttu-id="fe327-122">Zpracování <xref:System.Windows.Forms.DataGridView.DataError> událostí na <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="fe327-122">Handle the <xref:System.Windows.Forms.DataGridView.DataError> event on the <xref:System.Windows.Forms.DataGridView>.</span></span>  
  
     <span data-ttu-id="fe327-123">Pokud je kontext chyby operace potvrzení, zobrazí chybu v <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="fe327-123">If the context for the error is a commit operation, display the error in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="fe327-124">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="fe327-124">Testing the Application</span></span>  
 <span data-ttu-id="fe327-125">Nyní můžete otestovat formuláře a ujistěte se, že se chová podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="fe327-125">You can now test the form to make sure it behaves as expected.</span></span>  
  
#### <a name="to-test-the-form"></a><span data-ttu-id="fe327-126">Postup testování formuláře</span><span class="sxs-lookup"><span data-stu-id="fe327-126">To test the form</span></span>  
  
-   <span data-ttu-id="fe327-127">Stisknutím klávesy F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="fe327-127">Press F5 to run the application.</span></span>  
  
     <span data-ttu-id="fe327-128">Zobrazí se <xref:System.Windows.Forms.DataGridView> řízení, naplní se data z tabulky zákazníků.</span><span class="sxs-lookup"><span data-stu-id="fe327-128">You will see a <xref:System.Windows.Forms.DataGridView> control filled with data from the Customers table.</span></span> <span data-ttu-id="fe327-129">Pokud zadáte hodnotu duplicitní pro `CustomerID` a Potvrdit úpravy, bude automaticky vracet hodnotu buňky a zobrazí se <xref:System.Windows.Forms.MessageBox> , zobrazí se chyba vstupní data.</span><span class="sxs-lookup"><span data-stu-id="fe327-129">If you enter a duplicate value for `CustomerID` and commit the edit, the cell value will revert automatically and you will see a <xref:System.Windows.Forms.MessageBox> that displays the data entry error.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="fe327-130">Další kroky</span><span class="sxs-lookup"><span data-stu-id="fe327-130">Next Steps</span></span>  
 <span data-ttu-id="fe327-131">Tato aplikace získáte základní znalosti o <xref:System.Windows.Forms.DataGridView> možnosti ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fe327-131">This application gives you a basic understanding of the <xref:System.Windows.Forms.DataGridView> control's capabilities.</span></span> <span data-ttu-id="fe327-132">Můžete přizpůsobit vzhled a chování <xref:System.Windows.Forms.DataGridView> řízení několika způsoby:</span><span class="sxs-lookup"><span data-stu-id="fe327-132">You can customize the appearance and behavior of the <xref:System.Windows.Forms.DataGridView> control in several ways:</span></span>  
  
-   <span data-ttu-id="fe327-133">Změna stylů ohraničení a záhlaví.</span><span class="sxs-lookup"><span data-stu-id="fe327-133">Change border and header styles.</span></span> <span data-ttu-id="fe327-134">Další informace najdete v tématu [postupy: Změna ohraničení a mřížky styly v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="fe327-134">For more information, see [How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md).</span></span>  
  
-   <span data-ttu-id="fe327-135">Povolit nebo zakázat vstupu uživatele na <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fe327-135">Enable or restrict user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="fe327-136">Další informace najdete v tématu [postupy: zabránění přidávání řádků a odstranění v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md), a [postup: Zkontrolujte sloupce jen pro čtení v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="fe327-136">For more information, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md), and [How to: Make Columns Read-Only in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).</span></span>  
  
-   <span data-ttu-id="fe327-137">Ověření vstupu uživatele na <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fe327-137">Validate user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="fe327-138">Další informace najdete v tématu [návod: ověřování dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="fe327-138">For more information, see [Walkthrough: Validating Data in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
-   <span data-ttu-id="fe327-139">Zpracování pomocí virtuální režim velmi velkých datových sad.</span><span class="sxs-lookup"><span data-stu-id="fe327-139">Handle very large data sets using virtual mode.</span></span> <span data-ttu-id="fe327-140">Další informace najdete v tématu [návod: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="fe327-140">For more information, see [Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).</span></span>  
  
-   <span data-ttu-id="fe327-141">Přizpůsobení vzhledu buněk.</span><span class="sxs-lookup"><span data-stu-id="fe327-141">Customize the appearance of cells.</span></span> <span data-ttu-id="fe327-142">Další informace najdete v tématu [postupy: přizpůsobení vzhledu buněk v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md) a [postupy: nastavení výchozí styly buňky pro ovládací prvek Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="fe327-142">For more information, see [How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md) and [How to: Set Default Cell Styles for the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe327-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="fe327-143">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="fe327-144">Vkládání dat v systému Windows Forms DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="fe327-144">Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="fe327-145">Postupy: zpracování chyb vzniklých při zadávání dat v systému Windows Forms DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="fe327-145">How to: Handle Errors That Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/handle-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 [<span data-ttu-id="fe327-146">Návod: Ověřování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="fe327-146">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="fe327-147">Ochrana informací o připojení</span><span class="sxs-lookup"><span data-stu-id="fe327-147">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)