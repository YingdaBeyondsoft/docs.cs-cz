---
title: Sledování SQL
ms.date: 03/30/2017
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
ms.openlocfilehash: 9c42690570fb3f90f576327dcc5cfe870288b99a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33518300"
---
# <a name="sql-tracking"></a>Sledování SQL
Tento příklad znázorňuje, jak psát vlastní účastník sledování SQL, který zapíše sledování záznamů do databáze SQL. Windows Workflow Foundation (WF) poskytuje pracovní postup, chcete-li získat přehled o provádění instanci pracovního postupu pro sledování. Modul runtime sledování vysílá pracovní postup sledování záznamů během spouštění pracovního postupu. Další informace o sledování pracovního postupu najdete v tématu [pracovního postupu pro sledování a trasování](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Ověřte, máte systému SQL Server 2008, SQL Server 2008 Express nebo novější nainstalována. Skriptů spojených s ukázkou předpokládá použití instance SQL Express na místním počítači. Pokud máte jinou instanci před spuštěním ukázky upravte skripty vztahující se k databázi.  
  
2.  Vytvořte databázi systému SQL Server sledování spuštěním Trackingsetup.cmd v adresáři skripty (\WF\Basic\Tracking\SqlTracking\CS\Scripts). Tím se vytvoří databáze názvem TrackingSample.  
  
    > [!NOTE]
    >  Tento skript vytvoří databázi na výchozí instanci systému SQL Express. Pokud chcete nainstalovat na jinou instanci databáze, upravte skript Trackingsetup.cmd.  
  
3.  Otevřete SqlTrackingSample.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
4.  Stisknutím kombinace kláves CTRL + SHIFT + B řešení sestavíte.  
  
5.  Stisknutím klávesy F5 spusťte aplikaci.  
  
     Okno Prohlížeč otevře a ukazuje výpis pro aplikaci adresáře.  
  
6.  V prohlížeči klikněte na tlačítko StockPriceService.xamlx.  
  
7.  Prohlížeč zobrazí stránku StockPriceService, který obsahuje službu místní adresu WSDL. Zkopírujte tuto adresu.  
  
     Je například adresa WSDL místní služby http://localhost:65193/StockPriceService.xamlx?wsdl.  
  
8.  Pomocí [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], spuštění testovacího klienta WCF (WcfTestClient.exe). Je umístěn v adresáři 10.0\Common7\IDE Microsoft Visual Studio.  
  
9. V testu klienta WCF, klikněte na tlačítko **soubor** nabídku a vyberte **přidat službu**. Vložte adresu místní služby do textového pole. Klikněte na tlačítko **OK** zavřete dialogové okno.  
  
10. V testu klienta WCF, poklikejte na **GetStockPrice**. Tím se otevře `GetStockPrice` operace, které přijímá jeden parametr, zadejte hodnotu `Contoso` a klikněte na tlačítko **Invoke**.  
  
11. Záznamy emitovaného sledování se zapisují do databáze SQL. Pokud chcete zobrazit záznamy sledování, otevřete databázi TrackingSample v SQL Management Studio a přejděte do tabulky. Další informace o SQL Server Management Studio najdete v tématu [představení SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=165645). SQL Server 2008 Management Studio Express si můžete stáhnout [zde](http://go.microsoft.com/fwlink/?LinkId=180520). Spuštění vyberte možnost dotazu na tabulky zobrazí data v rámci sledování záznamů uložených v obou tabulkách.  
  
#### <a name="to-uninstall-the-sample"></a>Chcete-li odinstalovat vzorku  
  
1.  Spusťte skript theTrackingcleanup.cmd v adresáři ukázkové (\WF\Basic\Tracking\SqlTracking).  
  
    > [!NOTE]
    >  Trackingcleanup.cmd pokusí o odstranění databáze v místním počítači SQL Express. Pokud používáte jiné instance systému SQL server, upravte Trackingcleanup.cmd.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`  
  
## <a name="see-also"></a>Viz také  
 [Ukázky monitorování AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
