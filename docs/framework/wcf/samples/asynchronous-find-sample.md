---
title: Ukázka asynchronního hledání
ms.date: 03/30/2017
ms.assetid: 7a713a25-c1f4-42e1-8c4a-93d64ca45a3b
ms.openlocfilehash: ed900ba3cd1b55f4e35ec0d2b92ef6b7283b498e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33500274"
---
# <a name="asynchronous-find-sample"></a>Ukázka asynchronního hledání
Tento příklad ukazuje způsob použití operace asynchronní hledání z klientské aplikace.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Výhodou následující tohoto vzoru návrhu je, že klient proběhne asynchronně koncových bodů umístěný jako výsledek požadavku najít. Pokud chcete zobrazit, jak to funguje, otevřete soubor Client.cs. Poznámka: <xref:System.ServiceModel.Discovery.DiscoveryClient> objekt má dva delegáti připojené k jeho obslužné rutiny událostí. Jeden delegáta je volána, když <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> událost se vyvolá, a jiné se nazývá pokaždé, když <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> událost se vyvolá. Ukázka ukazuje, jak můžete použít tento vzor ve vaší aplikaci.  
  
> [!NOTE]
>  Tato ukázka používá koncových bodů protokolu HTTP a pokud chcete spustit, musí být přidán správné seznamy ACL adresy URL. Další informace najdete v tématu [konfigurace HTTP a HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md). Spuštěním následujícího příkazu na zvýšená oprávnění měli přidat příslušné seznamy ACL. Chcete nahradit domény a uživatelské jméno pro následující argumenty, pokud příkaz nefunguje, protože je. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete AsyncFind.sln.  
  
2.  Stisknutím kombinace kláves CTRL + SHIFT + B řešení sestavíte.  
  
3.  Otevřete [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazový řádek a přejděte do adresáře \WCF\Basic\Discovery\AsyncFind\CS\service\bin\Debug nebo \WCF\Basic\Discovery\AsyncFind\VB\service\bin\Debug a spustit Service.exe.  
  
4.  Po spuštění služby, přejděte na daný adresář WCF\Basic\Discovery\AsyncFind\VB\client\bin\Debug nebo \WCF\Basic\Discovery\AsyncFind\CS\client\bin\Debug a spusťte Client.exe.  
  
5.  Zkontrolujte, že klient je možné najít a volání služby.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\AsyncFind`  
  
## <a name="see-also"></a>Viz také
