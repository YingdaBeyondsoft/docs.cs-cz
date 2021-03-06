---
title: Základní služba AJAX
ms.date: 03/30/2017
ms.assetid: d66d0c91-0109-45a0-a901-f3e4667c2465
ms.openlocfilehash: 0bb8a2b28ea87cb0c22126540f6cdab604ca5120
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33805977"
---
# <a name="basic-ajax-service"></a>Základní služba AJAX
Tento příklad znázorňuje, jak vytvořit základní služby ASP.NET asynchronní JavaScript a XML (AJAX) (služba, která můžete přistupovat pomocí kódu jazyka JavaScript z webového prohlížeče klienta) pomocí služby Windows Communication Foundation (WCF). Služba používá <xref:System.ServiceModel.Web.WebGetAttribute> atribut zajistit, že je služba reaguje na požadavky HTTP GET a je nakonfigurovaný na použití formát JavaScript Object Notation (JSON) dat pro odpovědi.  
  
 Podpora jazyka AJAX v WCF je optimalizovaný pro použití s pomocí prvku ASP.NET AJAX `ScriptManager` ovládacího prvku. Příklad WCF pomocí prvku ASP.NET AJAX, najdete v článku [AJAX ukázky](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
> [!NOTE]
>  Nastavení postupu a sestavení pokyny k této ukázce jsou umístěné na konci tohoto tématu.  
  
 V následujícím kódu <xref:System.ServiceModel.Web.WebGetAttribute> je použit atribut `Add` operace zajistit, že služba reaguje na požadavky HTTP GET. Kód používá GET pro jednoduchost (můžete vytvořit požadavek HTTP GET z libovolného webového prohlížeče). GET můžete taky povolit ukládání do mezipaměti. Chybí výchozí hodnota je HTTP POST `WebGetAttribute` atribut.  

```csharp
[ServiceContract(Namespace = "SimpleAjaxService")]
public interface ICalculator
{
    [WebGet]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

 Ukázkový soubor .svc používá <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, který přidá <xref:System.ServiceModel.Description.WebScriptEndpoint> standardní koncového bodu služby. Koncový bod je nakonfigurován na prázdnou adresu relativně k souboru .svc. To znamená, že adresa služby je http://localhost/ServiceModelSamples/service.svc, s žádné další přípony jiný než název operace.  

```svc
<%@ServiceHost language="C#" Debug="true" Service="Microsoft.Samples.SimpleAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory" %>
```

 <xref:System.ServiceModel.Description.WebScriptEndpoint> Je předem nakonfigurovaný zpřístupnit službu z klienta stránku ASP.NET AJAX. V následující části v souboru Web.config lze provést další změny konfigurace ke koncovému bodu. Může být odebrán, pokud nejsou vyžadovány žádné další změny.  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webScriptEndpoint>  
      <!-- Use this element to configure the endpoint -->  
      <standardEndpoint name=""  />  
    </webScriptEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint> Nastaví výchozí formát dat pro službu do formátu JSON místo XML. Chcete-li vyvolat službu, přejděte na http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200 po dokončení sadu nahoru a vytvářet kroky uvidíte později v tomto tématu. Tato funkce testování je povolit pomocí služby požadavek HTTP GET.  
  
 Klient SimpleAjaxClientPage.aspx webová stránka obsahuje kód ASP.NET k vyvolání služby vždy, když uživatel klikne na jednu operaci tlačítek na stránce. `ScriptManager` Řízení se používá k zajištění proxy službě přístupné prostřednictvím jazyka JavaScript.  

```aspx-csharp
<asp:ScriptManager ID="ScriptManager" runat="server">  
    <Services>  
        <asp:ServiceReference Path="service.svc" />  
    </Services>  
</asp:ScriptManager>  
```

 Vytvoření instance místní proxy server a operace jsou vyvolány pomocí následujícího kódu JavaScript.  

```javascript
// Code for extracting arguments n1 and n2 omitted…  
// Instantiate a service proxy  
var proxy = new SimpleAjaxService.ICalculator();  
// Code for selecting operation omitted…  
proxy.Add(parseFloat(n1), parseFloat(n2), onSuccess, onFail, null);  
```

 Pokud je úspěšné volání služby, vyvolá kód `onSuccess` obslužnou rutinu a výsledek operace se zobrazí v textovém poli.  

```javascript
function onSuccess(mathResult){  
     document.getElementById("result").value = mathResult;  
}
```

> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\SimpleAjaxService`  
  
## <a name="see-also"></a>Viz také
