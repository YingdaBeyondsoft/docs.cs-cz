---
title: Kryptografická flexibilita v zabezpečení WCF
ms.date: 03/30/2017
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 40f4f8523d5286911216180846e94ec18e40da1c
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33810210"
---
# <a name="cryptographic-agility-in-wcf-security"></a>Kryptografická flexibilita v zabezpečení WCF
Tento příklad ukazuje postup zadejte v algoritmu standardní nebo vlastní k zajištění kryptografických agilní implementace v klienta Windows Communication Foundation (WCF) a služby. Ukázka se skládá z následujících projektech:  
  
 Služba  
 Toto je vlastním hostováním služby WCF, který implementuje `ICalculator` rozhraní a zabezpečuje koncový bod pomocí <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> s zabezpečené relace a spolehlivé relace zakázán. Služba definuje vlastní `SecurityAlgorithmSuite` třídu k určení kryptografické algoritmy, které má být použit pro zabezpečení zpráv.  
  
 Klient  
 Toto je WCFclient, který přistupuje k službě po úspěšném ověření. Vyvolá operace vystavené `ICalculator` rozhraní a implementují službu. Klient také definuje stejné vlastní `SecurityAlgorithmSuite` třídu k určení kryptografické algoritmy, které má být použit pro zabezpečení zpráv.  
  
### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Otevřete řešení CryptoAgility.sln v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Stisknutím kombinace kláves CTRL + SHIFT + B řešení sestavíte.  
  
3.  Otevřete [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] a přejděte do adresáře \WCF\Basic\Security\CryptoAgility\Service\bin a spusťte soubor service.exe s oprávněními správce service.exe kliknete pravým tlačítkem a výběrem **spustit jako správce**.  
  
4.  Přejděte do adresáře \WCF\Basic\Security\CryptoAgility\Client\bin a spusťte soubor client.exe normálně.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení](../../../../docs/framework/wcf/feature-details/security.md)
