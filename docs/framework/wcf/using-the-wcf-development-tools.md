---
title: Používání vývojářských nástrojů WCF
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: 41d2ee2881b79ffb086a931ec6d271d409ac66db
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806780"
---
# <a name="using-the-wcf-development-tools"></a>Používání vývojářských nástrojů WCF
Tato část popisuje vývojářské nástroje Visual Studio, které vám může pomoci při vývoji vaší WCFservice.  
  
 Můžete používat šablony sady Visual Studio jako základ pro rychle vytvářet vlastní služby a pak pomocí automatického hostitele služby WCF a testovacího klienta WCF pro ladění a testování vaší služby. Tyto nástroje společně poskytují rychlé a plynulé ladění a testování cyklu a bránit potřeba potvrdit k hostování modelu včas.  
  
## <a name="the-wcf-developer-tools"></a>Nástroje pro vývojáře WCF  
 [Šablony sady Visual Studio pro WCF](../../../docs/framework/wcf/wcf-vs-templates.md)  
  
 Předdefinovaných šablon projektů a položek v sadě Visual Studio v sadě Visual Studio vám pomůže rychle vytvářet služby WCF a okolního aplikace.  
  
 [Hostitel služby WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
 Automatické hostitel služby WCF (WcfSvcHost.exe) umožňuje spuštění ladicího programu sady Visual Studio (F5) automaticky hostování a testovat službu, kterou jste implementovali. Potom můžete otestovat pomocí klienta WCF Test (wcfTestClient.exe) nebo vlastního klienta najít a opravit všechny potenciální chyby.  
  
 [Testovací klient WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)  
  
 Testovacího klienta WCF (WcfTestClient.exe) je nástroj grafickým uživatelským rozhraním, který umožňuje vstupní parametry náhodné typy, odeslat tento vstup do služby a zobrazení, které odpovědi služba odesílá zpět. Poskytuje bezproblémové služby testování prostředí při kombinaci s automaticky hostitel služby WCF.  
  
 [Generování tříd datových typů z XML](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md)  
  
 Data XML uložené do schránky můžete vložit do kódu stránky. Třídy definované v datech se převede na typy kódu.  
  
## <a name="using-the-tools-without-administrator-privilege"></a>Pomocí nástrojů bez oprávnění správce  
 Pokud chcete povolit uživatelům bez oprávnění správce k vývoji služeb WCF, se vytvoří ACL (seznam řízení přístupu) pro obor názvů "http://+:8731/Design_Time_Addresses" při instalaci sady Visual Studio. Seznam řízení přístupu je nastavené na (UI), který zahrnuje všechny interaktivní uživatelé přihlášení k počítači. Správci mohou přidat nebo odebrat uživatele z tohoto seznamu ACL nebo otevřít další porty. Tento seznam ACL umožňuje WCF nebo WF šablon odesílat a přijímat data ve výchozí konfiguraci. Taky umožňuje uživatelům používat automatické hostitel služby WCF (wcfSvcHost.exe) bez je udělení oprávnění správce.  
  
 Můžete upravit přístup pomocí nástroje Netsh.exe v [!INCLUDE[wv](../../../includes/wv-md.md)] pod účtem zvýšenými na úroveň správce. Následuje příklad použití Netsh.exe.  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 Další informace o Netsh.exe najdete v tématu [jak pomocí nástroje Netsh.exe a přepínače příkazového řádku](http://go.microsoft.com/fwlink/?LinkId=97877).  
  
## <a name="see-also"></a>Viz také  
 [Šablony sady Visual Studio pro WCF](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [Hostitel služby WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [Testovací klient WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
