---
title: Služba AJAX bez konfigurace
ms.date: 03/30/2017
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
ms.openlocfilehash: 53a0de88d08fbc12cb8861042a50da6503fa5def
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809183"
---
# <a name="ajax-service-without-configuration"></a>Služba AJAX bez konfigurace
Tento příklad znázorňuje způsob použití Windows Communication Foundation (WCF) pro vytvoření základní služby ASP.NET asynchronní JavaScript a XML (AJAX) (služba, který je přístupný pomocí kódu jazyka JavaScript z webového prohlížeče klienta) bez použití žádnou konfiguraci. nastavení. Služba používá speciální syntaxe v souboru .svc automaticky povolení koncového bodu AJAX.  
  
 Podpora jazyka AJAX v WCF je optimalizovaný pro použití s pomocí prvku ASP.NET AJAX `ScriptManager` ovládacího prvku. Příklad WCF pomocí prvku ASP.NET AJAX, najdete v článku [Ajax ukázky](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Tato ukázka je založen na AJAX služby pomocí HTTP POST. Jak je popsáno v [základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) ukázce <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> se používá k hostování služby.  

```svc
<%ServiceHost  
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CalculatorService  
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"  
%>  
```

 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> automaticky přidá <xref:System.ServiceModel.Description.WebScriptEndpoint> ke službě. Pokud potřebujete provést ke koncovému bodu, žádné změny konfigurace `<system.ServiceModel>` části lze úplně odebrat ze souboru Web.config pro službu. Soubor Web.config obsahuje některá nastavení ASP.NET, které jsou používány ConfigFreeClientPage.aspx. Pokud je tento není tento případ, může odebrat celý soubor Web.config.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že můžete provádět pokynů pro instalaci v [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavte řešení ConfigFreeAjaxService.sln, jak je popsáno v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Přejděte na http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx (neotevírejte ConfigFreeClientPage.aspx v prohlížeči z v adresáři projektu).  
  
> [!NOTE]
>  Při spuštění této ukázce, Zkontrolujte prosím, že anonymní ověřování a ověřování systému Windows nejsou povolené současně ServiceModelSamples složky ve službě IIS. Pokud tomu tak je, zakažte ověřování systému Windows. Po spuštění vzorového povolit ověřování systému Windows a spusťte "příkaz iisreset".  
  
## <a name="see-also"></a>Viz také  
 [Základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
