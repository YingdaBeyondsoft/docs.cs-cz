---
title: Spouštění ukázek Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: db8a83da-95c1-4a21-a9d2-48caeb6398ea
ms.openlocfilehash: 68b05b590e80a65ba8816c0dcfd8d140b71eb8c8
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807251"
---
# <a name="running-the-windows-communication-foundation-samples"></a>Spouštění ukázek Windows Communication Foundation
Ukázky Windows Communication Foundation (WCF) se může spouštět v konfiguraci s jedním počítače nebo počítači. Zadaný, ukázky jsou připravené ke spuštění na jednom počítači. V konfiguraci mezi počítači je potřeba upravit nastavení tohoto příkladu konfiguračního souboru. Následující postupy popisují, jak spustit ukázku ve stejném počítači a počítači konfigurace. Všimněte si, že jsou rozdíly v kroků pro služby hostované v Internetové informační služby (IIS) a vlastním hostováním ukázky. Většina ukázky jsou hostované ve službě IIS; Zobrazit informace o ukázkový soubor readme k určení, jak je hostovaná.  
  
 Na [!INCLUDE[wv](../../../../includes/wv-md.md)], ukázky, které nejsou hostované ve službě IIS vyžaduje zvýšená oprávnění k registraci naslouchací proces s ovladače Http.sys. Použijte aplikaci Httpcfg.exe registrace naslouchání adresy služby u účtu, který služba běží pod nebo spusťte službu z příkazového řádku s oprávněními správce.  
  
> [!NOTE]
>  Před sestavení nebo s některým z ukázky WCF, ujistěte se, jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Ke spuštění ukázky na stejném počítači  
  
1.  Pokud služba je hostitelem služby IIS, ujistěte se, že mají přístup ke službě pomocí prohlížeče tak, že zadáte tuto adresu: http://localhost/servicemodelsamples/service.svc. Potvrzovací stránku má být zobrazena v odpovědi. Pokud se nezobrazí stránka potvrzení, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
2.  Pokud je samoobslužně hostovaná služba, spusťte Service.exe z \service\bin získáte složky pro konkrétní jazyk. Aktivita služby se zobrazí v okně konzoly služby.  
  
3.  Spusťte Client.exe z \client\bin\\, získáte složky pro konkrétní jazyk. Činnost klienta se zobrazí v okně konzoly klienta.  
  
4.  Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-machines"></a>Ke spuštění ukázky mezi počítači  
  
1.  Pokud je služba hostovaná ve službě IIS:  
  
    1.  Na počítači služby vytvořte virtuální adresář s názvem ServiceModelSamples. Dávkový soubor součástí Setupvroot.bat [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) slouží k vytvoření adresáře disk a virtuální adresář.  
  
    2.  Zkopírujte soubory programu služby z %SystemDrive%\Inetpub\wwwroot\servicemodelsamples do ServiceModelSamples virtuálního adresáře na počítači služby. Ujistěte se, jestli jste zahrnuli soubory v adresáři \bin.  
  
    3.  Test službě můžete dostat z klientského počítače pomocí prohlížeče.  
  
     Pokud služba se hostuje sama:  
  
    1.  Na počítači služby vytvořte adresář k uložení souborů služby.  
  
    2.  Zkopírujte soubory programu služby ve složce \service\bin\ ve složce pro specifický jazyk k počítači služby.  
  
    3.  V konfiguračním souboru služby změňte hodnotu adresu definice koncového bodu tak, aby odpovídala nové adresy vaší služby. Nahraďte všechny odkazy na "localhost" plně kvalifikovaný název domény v adrese.  
  
    4.  Service.exe spusťte z příkazového řádku.  
  
2.  Zkopírujte soubory programu klienta ve složce \client\bin\ ve složce jazyka na klientský počítač.  
  
3.  Nastavte adresu koncového bodu.  
  
    1.  Pokud služba není spuštěna pod účtem domény, otevřete konfigurační soubor klienta a změňte hodnotu adresu definice koncového bodu tak, aby odpovídala nové adresy vaší služby. Nahraďte všechny odkazy na "localhost" plně kvalifikovaný název domény v adrese.  
  
    2.  Pokud služba běží pod účtem domény, znovu vygenerujte konfigurace klienta spuštěním Svcutil.exe proti službu. Další informace o spouštění Svcutil.exe najdete v tématu [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md). Použijte vygenerovaný soubor místo konfiguračního souboru ve vzorku. Vygenerovaný konfigurační soubor obsahuje informace o dalších identity a obsahuje všechna nastavení, které jsou potřebné pro připojení ke koncovému bodu služby, i když jsou výchozí nastavení. Další informace o informace o identitě najdete v tématu [identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md), a [ \<identity >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md).  
  
4.  V klientském počítači spusťte z příkazového řádku Client.exe.  
  
### <a name="to-debug-a-service"></a>K ladění služby  
  
1.  Sestavení řešení (klient a service) pomocí **sestavení** nabídky nebo CTRL + SHIFT + B.  
  
2.  Pokud je služba hostovaná ve službě IIS:  
  
    1.  Aktivovat službu pomocí prohlížeče tak, že zadáte adresu http://localhost/servicemodelsamples/service.svc.  
  
    2.  V řešení, vyberte **ladění** nabídky a **připojit k procesu** položku nabídky.  
  
    3.  Vyberte **Zobrazit procesy od všech uživatelů** zaškrtávací políčko.  
  
    4.  Vyberte hostitele pracovní proces W3wp.exe k ladění (vyberte ASPNet_wp.exe v systému Windows XP).  
  
3.  Teď můžete nastavit zarážky v kódu služby a povolit zarážky na výjimky.  
  
4.  Klikněte pravým tlačítkem na položku projektu klienta a zvolte **ladění**, **spustit novou instanci**.  
  
### <a name="to-clean-up-after-the-sample"></a>Vyčistěte po vzorku  
  
-   Pokud je služba hostovaná ve službě IIS pro účely zabezpečení, odeberte definici virtuální adresář a oprávnění udělená v průběhu instalace, když skončíte s ukázky.  
  
## <a name="see-also"></a>Viz také  
 [Ukázky vytváření Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md)  
 [Spuštění ukázky v pracovní skupině a v počítačích](http://msdn.microsoft.com/library/a451a525-e7ce-452d-9da9-620221260113)  
 [Tipy pro odstraňování potíží](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)
