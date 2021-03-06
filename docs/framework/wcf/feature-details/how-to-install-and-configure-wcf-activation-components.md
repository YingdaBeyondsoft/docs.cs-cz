---
title: 'Postupy: Instalace a konfigurace aktivačních komponent WCF'
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP activation [WCF]
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
ms.openlocfilehash: f362bd1e4a644488e85cdeca674d46ca340bde05
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491745"
---
# <a name="how-to-install-and-configure-wcf-activation-components"></a>Postupy: Instalace a konfigurace aktivačních komponent WCF
Toto téma popisuje kroky potřebné k nastavení aktivační služba procesů systému Windows (WAS) na [!INCLUDE[wv](../../../../includes/wv-md.md)] k hostování Windows Communication Foundation (WCF) služeb, které není komunikaci pomocí protokolu HTTP síťových protokolů. Následující oddíly popisují kroky pro tuto konfiguraci:  
  
-   Nainstalovat (nebo potvrďte instalaci) aktivačních komponent WCF.  
  
-   Konfigurace WAS pro podporu protokolu než HTTP. Následující postup umožňuje konfiguraci [!INCLUDE[wv](../../../../includes/wv-md.md)] pro Aktivace protokolem TCP.  
  
 Po instalaci a konfiguraci služby WAS, najdete v části [postupy: hostování služby WCF ve WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) postupy k vytvoření služby WCF, který zveřejňuje jiným protokolem než HTTP koncový bod, který využívá WAS.  
  
### <a name="to-install-the-wcf-non-http-activation-components"></a>Chcete-li nainstalovat komponenty Aktivace jiným protokolem než HTTP WCF  
  
1.  Klikněte **spustit** tlačítko a potom klikněte na **ovládací panely**.  
  
2.  Klikněte na tlačítko **programy**a potom klikněte na **programy a funkce**.  
  
3.  Na **úlohy** nabídky, klikněte na tlačítko **Windows zapnout nebo vypnout funkce**.  
  
4.  Najít [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] uzlu, vyberte a potom rozbalte ho.  
  
5.  Vyberte **součásti Aktivace jiným protokolem než Http WCF** pole a uložte nastavení.  
  
### <a name="to-configure-the-was-to-support-tcp-activation"></a>Konfigurace WAS pro podporu Aktivace protokolem TCP  
  
1.  Kvůli podpoře aktivace net.tcp, nutné ji nejdřív svázat výchozí web na net.tcp port. Můžete to provést pomocí Appcmd.exe, která se instaluje s [!INCLUDE[iisver](../../../../includes/iisver-md.md)] sada nástrojů pro správu. V okně příkazového řádku na úrovni správce spusťte následující příkaz.  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  Tento příkaz je na jednom řádku textu. Tento příkaz přidá vazbu net.tcp lokality na výchozí web naslouchá na portu TCP 808 s libovolným názvem hostitele.  
  
2.  Přestože všechny aplikace v rámci lokality sdílet běžné net.tcp vazbu, každá aplikace můžete povolit podporu net.tcp jednotlivě. Pokud chcete povolit net.tcp pro aplikaci, spusťte následující příkaz z příkazového řádku na úrovni správce.  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app   
    "Default Web Site/<WCF Application>" /enabledProtocols:http,net.tcp  
    ```  
  
    > [!NOTE]
    >  Tento příkaz je na jednom řádku textu. Tento příkaz povolí nebo\<*aplikace WCF*> přístup k aplikaci lze pomocí obou http://localhost  */ \<aplikace WCF >* a net.tcp:// localhost nebo*\<aplikace WCF >*.  
  
     Odeberte net.tcp vazby webu, který jste přidali Tato ukázka.  
  
     Pro potřeby následující dva kroky jsou implementované v dávkovém souboru názvem RemoveNetTcpSiteBinding.cmd umístěný v adresáři ukázka.  
  
    1.  Odeberte net.tcp ze seznamu povolených protokolů spuštěním následujícího příkazu v okně příkazového řádku na úrovni správce.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app   
        "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  Tento příkaz je na jednom řádku textu.  
  
    2.  Odeberte vazbu webu net.tcp v okno příkazového řádku se zvýšenými oprávněními spustíte následující příkaz:  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        --bindings.[protocol='net.tcp',bindingInformation='808:*']  
        ```  
  
        > [!NOTE]
        >  Tento příkaz je na jednom řádku textu.  
  
### <a name="to-remove-nettcp-from-the-list-of-enabled-protocols"></a>Chcete-li odebrat ze seznamu povolených protokolů net.tcp  
  
1.  Chcete-li odebrat net.tcp ze seznamu povolených protokolů, spusťte následující příkaz v okně příkazového řádku na úrovni správce.  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http  
    ```  
  
    > [!NOTE]
    >  Tento příkaz je na jednom řádku textu.  
  
### <a name="to-remove-the-nettcp-site-binding"></a>Chcete-li odebrat vazby webu net.tcp  
  
1.  Vazba k odebrání net.tcp lokality spusťte následující příkaz v okně příkazového řádku na úrovni správce.  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
    -bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  Tento příkaz je na jednom řádku textu.  
  
## <a name="see-also"></a>Viz také  
 [Aktivace protokolu TCP](../../../../docs/framework/wcf/samples/tcp-activation.md)  
 [Aktivace služby MSMQ](../../../../docs/framework/wcf/samples/msmq-activation.md)  
 [Aktivace pojmenovaného kanálu](../../../../docs/framework/wcf/samples/namedpipe-activation.md)  
 [Hostování funkcí systému Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)
