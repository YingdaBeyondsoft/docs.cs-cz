---
title: 'Návod: Uspořádání ovládacích prvků Windows Forms v subsystému WPF'
ms.date: 04/03/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
ms.openlocfilehash: f2cf82c54724a43a60fb9077c5731d4b4ad2cfd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549656"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a>Návod: Uspořádání ovládacích prvků Windows Forms v subsystému WPF
Tento postup vám ukáže, jak používat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkce rozložení uspořádat [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacích prvků v hybridní aplikace.  
  
 Úkoly v tomto návodu zahrnují:  
  
-   Vytváření projektu.  
  
-   Pomocí výchozího nastavení rozložení.  
  
-   Nastavení velikosti obsahu.  
  
-   Pomocí absolutní umístění.  
  
-   Určení velikosti explicitně.  
  
-   Nastavení vlastností rozložení.  
  
-   Principy pořadí z-order omezení.  
  
-   Ukotvení.  
  
-   Nastavení viditelnosti.  
  
-   Hostování ovládacího prvku, který není funkce stretch.  
  
-   Škálování.  
  
-   Otáčení.  
  
-   Nastavení odsazení a okraje.  
  
-   Použití dynamické rozložení kontejnerů.  
  
 Kompletní kód tak seznam všech úloh v tomto návodu, najdete v části [uspořádání ovládacích prvků Windows Forms v ukázce WPF](http://go.microsoft.com/fwlink/?LinkID=159971).  
  
 Po dokončení bude mít k pochopení [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] rozložení funkce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– na základě aplikací.  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
  
#### <a name="to-create-and-set-up-the-project"></a>Vytvoření a nastavení projektu  
  
1.  Vytvořte projekt aplikace WPF s názvem `WpfLayoutHostingWf`.  
  
2.  V Průzkumníku řešení přidejte odkazy na následující sestavení.  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
    -   System.Drawing  
  
3.  Dvakrát klikněte na MainWindow.xaml a otevře se v zobrazení jazyka XAML.  
  
4.  V <xref:System.Windows.Window> elementu, přidejte následující [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mapování oboru názvů.  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  V <xref:System.Windows.Controls.Grid> element sadu <xref:System.Windows.Controls.Grid.ShowGridLines%2A> vlastnost `true` a definovat pět řádků a tři sloupce.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]  
  
## <a name="using-default-layout-settings"></a>Pomocí výchozího nastavení rozložení  
 Ve výchozím nastavení <xref:System.Windows.Forms.Integration.WindowsFormsHost> element zpracovává rozložení pro hostované [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku.  
  
#### <a name="to-use-default-layout-settings"></a>Chcete-li použít výchozí nastavení rozložení  
  
1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]  
  
2.  Stisknutím klávesy F5 sestavení a spuštění aplikace. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType> Zobrazí ovládací prvek v <xref:System.Windows.Controls.Canvas>. Je velikost hostované ovládacího prvku, na základě jeho obsahu a <xref:System.Windows.Forms.Integration.WindowsFormsHost> element je dimenzovány pro zvládnutí hostovaného ovládacího prvku.  
  
## <a name="sizing-to-content"></a>Nastavení velikosti obsahu  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Prvek zajišťuje, že je správně zobrazit jeho obsah velikost hostované ovládacího prvku.  
  
#### <a name="to-size-to-content"></a>Velikost obsahu  
  
1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]  
  
2.  Stisknutím klávesy F5 sestavení a spuštění aplikace. Jsou dvě nové ovládací prvky tlačítko dimenzované k zobrazení delší textového řetězce a zvětšení velikosti písma správně a <xref:System.Windows.Forms.Integration.WindowsFormsHost> jsou možnosti změnit velikost elementů zohlednit hostované ovládací prvky.  
  
## <a name="using-absolute-positioning"></a>Pomocí absolutní umístění  
 Absolutní umístění můžete použít k umístění <xref:System.Windows.Forms.Integration.WindowsFormsHost> element kdekoli v uživatelském rozhraní (UI).  
  
#### <a name="to-use-absolute-positioning"></a>Chcete-li použít absolutní umístění  
  
1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]  
  
2.  Stisknutím klávesy F5 sestavení a spuštění aplikace. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Prvek je umístěn 20 pixelů z na horní straně buňky mřížky a 20 pixelů od levého okraje.  
  
## <a name="specifying-size-explicitly"></a>Určení velikosti explicitně  
 Můžete zadat velikost <xref:System.Windows.Forms.Integration.WindowsFormsHost> element pomocí <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti.  
  
#### <a name="to-specify-size-explicitly"></a>Chcete-li explicitně určit velikost  
  
1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]  
  
2.  Stisknutím klávesy F5 sestavení a spuštění aplikace. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element je nastavena velikost 50 × široké 70 pixelů vysoké, což je menší než výchozí nastavení rozložení. Obsah [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek je přeskupení odpovídajícím způsobem.  
  
## <a name="setting-layout-properties"></a>Nastavení vlastností rozložení  
 Vždy nastavit vlastnosti související s rozložením na hostované ovládacího prvku pomocí vlastnosti <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu. Nastavení vlastností rozložení přímo na hostované ovládací prvek předá neočekávaným výsledkům.  
  
 Nastavit vlastnosti související s rozložením hostované ovládacího prvku [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nemá žádný vliv.  
  
#### <a name="to-see-the-effects-of-setting-properties-on-the-hosted-control"></a>Chcete-li zobrazit důsledky nastavení vlastnosti na hostované ovládací prvek  
  
1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]  
  
2.  V Průzkumníku řešení klikněte dvakrát na MainWindow.xaml. vb nebo MainWindow.xaml.cs a otevře se v editoru kódu.  
  
3.  Zkopírujte následující kód do `MainWindow` definici třídy.  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]  
  
4.  Stisknutím klávesy F5 sestavení a spuštění aplikace.  
  
5.  Klikněte **klikněte na tlačítko mi** tlačítko. `button1_Click` Sady obslužné rutiny událostí <xref:System.Windows.Forms.Control.Top%2A> a <xref:System.Windows.Forms.Control.Left%2A> vlastností hostovaného prvku. To způsobí, že hostovaný ovládací prvek změnit jejich umístění v rámci <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu. Hostitel udržuje stejné oblasti obrazovky, ale je oříznut hostovaného ovládacího prvku. Místo toho by měla vždycky vyplnění hostovaného ovládacího prvku <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.  
  
## <a name="understanding-z-order-limitations"></a>Seznámení s omezeními pořadí Z-Order  
 Viditelné <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementy jsou vždy vykreslován nad dalších prvků grafického subsystému WPF a jsou to nemá vliv pořadí z-order. Toto chování pořadí z-order najdete takto:

1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]  
 
2.  Stisknutím klávesy F5 sestavení a spuštění aplikace. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Vymalovávání elementu přes do elementu label.  


## <a name="docking"></a>Ukotvení  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> element podporuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ukotvení. Nastavte <xref:System.Windows.Controls.DockPanel.Dock%2A> přidružená vlastnost chcete ukotvit hostované ovládacího prvku <xref:System.Windows.Controls.DockPanel> elementu.  
  
#### <a name="to-dock-a-hosted-control"></a>Chcete-li ukotvit hostované ovládacího prvku  
  
1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]  
  
2.  Stisknutím klávesy F5 sestavení a spuštění aplikace. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element ukotven na pravé straně <xref:System.Windows.Controls.DockPanel> elementu.  
  
## <a name="setting-visibility"></a>Nastavení viditelnosti  
 Můžete provést vaše [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] řízení neviditelná nebo sbalit nastavením <xref:System.Windows.UIElement.Visibility%2A> vlastnost <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu. Když je ovládací prvek neviditelná, se nezobrazí, ale zabírá prostor rozložení. Když ovládacího prvku sbalena, se nezobrazí, ani nemá zabírají prostor rozložení.  
  
#### <a name="to-set-the-visibility-of-a-hosted-control"></a>Chcete-li nastavit viditelnost hostované ovládacího prvku  
  
1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]  
  
2.  MainWindow.xaml.vb nebo MainWindow.xaml.cs zkopírujte následující kód do definici třídy.  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]  
  
3.  Stisknutím klávesy F5 sestavení a spuštění aplikace.  
  
4.  Klikněte na tlačítko **kliknutím na nastavit jako neviditelné** tlačítko, aby <xref:System.Windows.Forms.Integration.WindowsFormsHost> element neviditelná.  
  
5.  Klikněte na tlačítko **kliknutím sbalit** tlačítko skrýt <xref:System.Windows.Forms.Integration.WindowsFormsHost> element z rozložení úplně. Když [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] řízení sbalena, okolního elementy jsou změněno tak, aby zabíral jeho místa.  
  
## <a name="hosting-a-control-that-does-not-stretch"></a>Hostování ovládacího prvku, který není funkce Stretch  
 Některé [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky s pevnou velikostí mají a není roztáhnou tak, aby vyplnil celou dostupné místo v rozložení. Například <xref:System.Windows.Forms.MonthCalendar> zobrazí měsíce v pevné mezery.  
  
#### <a name="to-host-a-control-that-does-not-stretch"></a>K hostování ovládacího prvku, který není funkce stretch  
  
1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]  
  
2.  Stisknutím klávesy F5 sestavení a spuštění aplikace. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element je umístěn na střed v řádku mřížky, ale není roztažen tak, aby vyplňování dostupného místa. Pokud je okno dostatečně velké na to, uvidíte dvě nebo více měsíců zobrazuje hostované <xref:System.Windows.Forms.MonthCalendar> řízení, ale ty se na v řádku. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Modul rozložení centra prvky, které nemůže být dimenzovány pro vyplňování dostupného místa.  
  
## <a name="scaling"></a>Změna měřítka  
 Na rozdíl od WPF elementy nejsou nepřetržitě škálovatelné většina ovládacích prvků Windows Forms. Pokud chcete zadat vlastní škálování, můžete přepsat <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> metoda. 
  
#### <a name="to-scale-a-hosted-control-by-using-the-default-behavior"></a>Škálování hostované ovládacího prvku pomocí výchozí chování  
  
1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]  
  
2.  Stisknutím klávesy F5 sestavení a spuštění aplikace. Hostované ovládací prvek a jeho okolního elementy jsou škálovat faktorem 0,5. Však není škálovat písma hostované ovládacího prvku.

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a>Otáčení  
 Na rozdíl od WPF elementy ovládací prvky Windows Forms nepodporuje otočení. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Při otočení transformací element není otočit u ostatních prvků grafického subsystému WPF. Jakoukoli jinou hodnotu než 180 stupňů vyvolá otočení <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> událostí.
 
#### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application"></a>Pokud chcete vidět otočení v hybridní aplikace  
  
1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]  
  
2.  Stisknutím klávesy F5 sestavení a spuštění aplikace. Hostované ovládací prvek není otáčet, ale jeho elementy okolního jsou otáčet o úhel 180 stupňů. Možná budete muset změnit velikost okna zobrazíte elementy.  
 

## <a name="setting-padding-and-margins"></a>Nastavení odsazení a okraje  
 Odsazení a okraje v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozložení jsou podobné odsazení a okraje v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Jednoduše nastavit <xref:System.Windows.Controls.Control.Padding%2A> a <xref:System.Windows.FrameworkElement.Margin%2A> vlastnosti <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.  
  
#### <a name="to-set-padding-and-margins-for-a-hosted-control"></a>Nastavení odsazení a okrajů pro hostované ovládací prvek  
  
1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]  
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]  
  
2.  Stisknutím klávesy F5 sestavení a spuštění aplikace. Nastavení odsazení a okrajů se použijí k hostované [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky stejným způsobem, že by bylo možné provést v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
## <a name="using-dynamic-layout-containers"></a>Použití kontejnerů dynamické rozložení  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] poskytuje dvě dynamické rozložení kontejnery <xref:System.Windows.Forms.FlowLayoutPanel> a <xref:System.Windows.Forms.TableLayoutPanel>. Můžete také použít tyto kontejnery v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozložení.  
  
#### <a name="to-use-a-dynamic-layout-container"></a>Použít kontejner dynamické rozložení  
  
1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]  
  
2.  MainWindow.xaml.vb nebo MainWindow.xaml.cs zkopírujte následující kód do definici třídy.  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]  
  
3.  Přidejte volání `InitializeFlowLayoutPanel` metoda v konstruktoru.  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]  
  
4.  Stisknutím klávesy F5 sestavení a spuštění aplikace. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element doplní <xref:System.Windows.Controls.DockPanel>, a <xref:System.Windows.Forms.FlowLayoutPanel> uspořádá jeho podřízených ovládacích prvků ve výchozí <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Návrhář WPF](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [Předpoklady rozložení pro element WindowsFormsHost](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)  
 [Uspořádání Windows Forms – ovládací prvky v ukázce WPF](http://go.microsoft.com/fwlink/?LinkID=159971)  
 [Návod: Hostování složeného ovládacího prvku Windows Forms v subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
