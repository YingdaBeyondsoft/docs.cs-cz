---
title: Místní kanál
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: 2473704c751ad0ea2d2a00bf7f3ea43d6e39498f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33501504"
---
# <a name="local-channel"></a>Místní kanál
Místní kanál je přenos kanálu Windows Communication Foundation (WCF), který se používá pro komunikaci v rámci stejné domény aplikace. To je užitečné pro scénáře, kde klient a služba běží ve stejné doméně aplikace a je třeba se vyhnout režii typické kanál zásobníku WCF (serializace a deserializace zpráv).  
  
## <a name="demonstrates"></a>Demonstruje  
 Místní kanál  
  
## <a name="discussion"></a>Diskusní  
 Ukázkový soubor obsahuje dva soubory projektu:  
  
-   **LocalChannel**: programové reprezentace místní kanál v rámci aktuální doménu aplikace. V tomto projektu komponentu odesílání umístí zprávu do fronty v paměti a komponentu přijímající zrušte fronty na zprávu, aby ji přijmou.  
  
-   **ClientAndService**: Tento projekt hostuje službu v konzolové aplikaci a poté spustí klienta k volání služby ze stejné domény aplikace.  
  
 Místní kanál návrhu přeskočí zásobníku kanál a zvýšit rychlost proces serializace. Kanál místní přenosu se implementuje pomocí fronty přenosu volání služby z klienta ke službě a vrátí hodnotu zpět klientovi. Místo serializaci parametry a návratové hodnoty, zkopíruje ukázce objekty.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Sestavte a spusťte LocalChannel řešení.  
  
2.  Hostitel služby je spuštěná a klient zavolá službu pomocí místní kanál. Výsledky volání služby se zobrazí okno konzoly.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
