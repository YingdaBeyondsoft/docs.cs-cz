---
title: Ukázky vytváření Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 2899e7a5-9cb2-4e8d-b8d2-f31391549198
ms.openlocfilehash: 637b862d81ce4eeddc56acb24a527e6937f33f64
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806952"
---
# <a name="building-the-windows-communication-foundation-samples"></a>Ukázky vytváření Windows Communication Foundation
Ukázky Windows Communication Foundation (WCF) se dají vytvářet pomocí sady Visual Studio 2010 nebo pomocí **msbuild** příkazu z příkazového řádku. Oba postupy jsou popsány v tomto tématu.  
  
> [!NOTE]
>  Před sestavení nebo s některým z ukázky WCF, ujistěte se, jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
### <a name="to-build-the-sample-using-a-command-prompt"></a>Chcete-li sestavit ukázku pomocí příkazového řádku  
  
1.  Otevřete [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazový řádek s oprávněními správce a přejděte do konkrétní jazyk podadresáře v části umístění adresáře, kam jste nainstalovali vzorku.  
  
2.  Typ `msbuild` na příkazovém řádku. Soubory programu klienta jsou vytvořeny tak client\bin a soubory programu služby jsou vytvořeny tak service\bin. Pokud je služba hostovaná Internetové informační služby (IIS), zkopírují se k adresáři servicemodelsamples a podadresář \bin také soubory programu služby.  
  
> [!NOTE]
>  Seznamy ACL musíte nastavit na %systemdrive%\inetpub\wwwroot udělit oprávnění pro účet, pod kterým jste přihlášeni k úpravě. V opačném případě některé post sestavení událostí selhání. Alternativně můžete ponechat seznamy ACL, jak jsou a spustit příkazový řádek SDK jako správce.  
  
### <a name="to-build-the-sample-using-visual-studio"></a>K vytvoření vzorku pomocí sady Visual Studio  
  
1.  Pokud používáte [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], Windows 7 nebo Windows Server 2008 R2 a spuštění [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], Visual Studio je nutné spustit s oprávněním vyšší úrovně oprávnění. Chcete-li to provést, klikněte pravým tlačítkem myši na ikonu v nabídce Start a pak klikněte na **spustit jako správce**.  
  
2.  Z **soubor** nabídky v sadě Visual Studio, klikněte na tlačítko **otevřete**, pak klikněte na tlačítko **projekt nebo řešení**. Přejděte na konkrétní jazyk podadresáře v adresáři, do které jste nainstalovali vzorku a dvakrát klikněte na ikonu .sln soubor otevřete řešení v sadě Visual Studio.  
  
3.  V **sestavení** nabídce vyberte možnost **znovu sestavit řešení**. Soubory programu klienta jsou vytvořeny tak client\bin a soubory programu služby jsou vytvořeny tak service\bin. Pokud je služba hostovaná ve službě IIS, zkopírují se k adresáři servicemodelsamples a podadresář \bin také soubory programu služby.  
  
> [!NOTE]
>  Seznamy ACL musíte nastavit na %systemdrive%\inetpub\wwwroot udělit oprávnění pro účet, pod kterým jste přihlášeni k úpravě. V opačném případě některé post sestavení událostí selhání. Alternativně můžete ponechat seznamy ACL, jak jsou a spustit příkazový řádek SDK nebo sady Visual Studio jako správce. Některé akce Visual Studio (jako je připojení ladicího programu pracovnímu procesu ASP.Net) taky vyžadují oprávnění správce.  
  
## <a name="setup-batch-files-and-scripts"></a>Instalační program dávkové soubory a skripty  
 Setup.exe a Cleanup.exe dávkové soubory a skripty mají spustit z příkazového řádku Visual Studia. Několik set nahoru a vyčištění souborů provádět úlohy, které vyžadují oprávnění správce a musí být spuštěna s oprávněními správce.  
  
## <a name="important-security-information-about-metadata-endpoints"></a>Důležité informace o zabezpečení o koncové body metadat  
 Pokud chcete zabránit neúmyslnému zveřejnění metadata potenciálně citlivých služby, výchozí konfiguraci pro služby Windows Communication Foundation (WCF) zakáže publikování metadat. Toto chování je ve výchozím nastavení zabezpečení, ale také znamená, že nelze použít metadata importovat nástroj (například Svcutil.exe) ke generování kódu klienta pro volání služby, pokud není výslovně povolena chování publikování metadat služby v konfiguraci požadován. Chcete-li experimentování se ukázky jednodušší, téměř všechny ukázky vystavit zabezpečená metadata publikování koncový bod. Tyto koncové body jsou potenciálně dostupné pro anonymní neověřené spotřebitelů a musí dát pozor před nasazením těchto koncových bodů a zajistit tak veřejně předání metadata služby příslušné. Další informace o publikování metadat služby najdete v tématu [chování publikování metadat](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md) ukázka. Najdete v článku [koncový bod metadat zabezpečení vlastní](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) ukázku pro ukázku zabezpečení koncový bod metadat.  
  
## <a name="exception-handling"></a>Zpracování výjimek  
 Obecně řečeno tyto ukázky nezahrnují tento kód se zaměřuje na předmět ukázky zpracování výjimek. Další informace o zpracování výjimek najdete v tématu [očekává výjimky](../../../../docs/framework/wcf/samples/expected-exceptions.md) ukázka.  
  
## <a name="regenerating-clients-and-configuration-with-svcutil"></a>Obnovuje se klienti a konfigurací s Svcutil  
 Můžete použít [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) znovu vygenerovat kód klienta a konfigurace pro většinu ukázky. Některé ukázky vyžadovat ručně upravená konfiguraci. Například pokud použijete Svcutil.exe znovu vygenerovat konfiguraci pro ukázku, která používá přihlašovací údaje certifikátu klienta, ručně zadejte přihlašovací údaje předtím nakonfigurovali. Některé ukázky použít konkrétní možnosti Svcutil.exe ovlivnit generovaný kód, tyto možnosti jsou určené v konkrétní ukázka témata.  
  
#### <a name="to-regenerate-the-client-and-configuration-files"></a>K opětovnému vytvoření klienta a konfiguračních souborů  
  
1.  Otevřete příkazový řádek SDK a přejděte do konkrétní jazyk podadresáře v části umístění adresáře, kam jste nainstalovali vzorku.  
  
2.  Pokud služba je typu hostuje Web, použijte následující příkaz.  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs  
    ```  
  
     Pokud je služba vlastním hostováním zadejte následující příkaz.  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /out:generatedClient.cs  
    ```  
  
     Nahraďte http://localhost:8000/ServiceModelSamples/service.svc/mex s adresou koncového bodu mex samoobslužné hostovanou službu.  
  
     Ke generování klienta v jazyce Visual Basic typu, použijte následující příkaz.  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb  
    ```  
  
     Je-li služba vlastním hostováním typ, použijte následující příkaz.  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb  
    ```  
  
    > [!NOTE]
    >  Tak, aby přeskočil generování konfigurace klienta přidat **/noconfig** možnost.  
  
## <a name="see-also"></a>Viz také  
 [Spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md)  
 [Nástroj metadat modelu služby (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
