---
title: "Ukázka služby AJAX s protokoly JSON a XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ea5860d-0c42-4ae9-941a-e07efdd8e29c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a6d60bec8c3b69d9fd094f59b1f4d8c9ec4d8dff
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ajax-service-with-json-and-xml-sample"></a><span data-ttu-id="4a268-102">Ukázka služby AJAX s protokoly JSON a XML</span><span class="sxs-lookup"><span data-stu-id="4a268-102">AJAX Service with JSON and XML Sample</span></span>
<span data-ttu-id="4a268-103">Tento příklad ukazuje, jak používat [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] k vytvoření služby asynchronní JavaScript a XML (AJAX), který vrací data JavaScript Object Notation (JSON) nebo XML.</span><span class="sxs-lookup"><span data-stu-id="4a268-103">This sample demonstrates how to use [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to create an Asynchronous JavaScript and XML (AJAX) service that returns either JavaScript Object Notation (JSON) or XML data.</span></span> <span data-ttu-id="4a268-104">Služby AJAX můžete přistupovat pomocí kódu jazyka JavaScript z webového prohlížeče klienta.</span><span class="sxs-lookup"><span data-stu-id="4a268-104">You can access an AJAX service by using JavaScript code from a Web browser client.</span></span> <span data-ttu-id="4a268-105">Tato ukázka je založena na [základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="4a268-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="4a268-106">Na rozdíl od jiných AJAX ukázky, tato ukázka nepoužívá prvku ASP.NET AJAX a <xref:System.Web.UI.ScriptManager> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4a268-106">Unlike the other AJAX samples, this sample does not use ASP.NET AJAX and the <xref:System.Web.UI.ScriptManager> control.</span></span> <span data-ttu-id="4a268-107">S určitou další konfiguraci [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby AJAX lze přistupovat z libovolné stránce HTML pomocí jazyka JavaScript a tento scénář je zobrazen v tomto poli.</span><span class="sxs-lookup"><span data-stu-id="4a268-107">With some additional configuration, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] AJAX services can be accessed from any HTML page through JavaScript, and this scenario is shown here.</span></span> <span data-ttu-id="4a268-108">Příklad použití [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pomocí prvku ASP.NET AJAX, najdete v části [AJAX ukázky](http://msdn.microsoft.com/en-us/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span><span class="sxs-lookup"><span data-stu-id="4a268-108">For an example of using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] with ASP.NET AJAX, see [AJAX Samples](http://msdn.microsoft.com/en-us/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span></span>  
  
 <span data-ttu-id="4a268-109">Tento příklad ukazuje, jak přepínat typ odpovědi operace mezi JSON a XML.</span><span class="sxs-lookup"><span data-stu-id="4a268-109">This sample shows how to switch the response type of an operation between JSON and XML.</span></span> <span data-ttu-id="4a268-110">Tato funkce je k dispozici bez ohledu na to, zda je služba nakonfigurována pro přistupovat pomocí prvku ASP.NET AJAX nebo stránku HTML/JavaScript klienta.</span><span class="sxs-lookup"><span data-stu-id="4a268-110">This functionality is available regardless of whether the service is configured to be accessed by ASP.NET AJAX or by an HTML/JavaScript client page.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a268-111">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="4a268-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="4a268-112">Pokud chcete povolit použití ASP.NET AJAX klientů, použijte <xref:System.ServiceModel.Activation.WebServiceHostFactory> (ne <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) v souboru .svc.</span><span class="sxs-lookup"><span data-stu-id="4a268-112">To enable the use of non-ASP.NET AJAX clients, use <xref:System.ServiceModel.Activation.WebServiceHostFactory> (not <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) in the .svc file.</span></span> <span data-ttu-id="4a268-113"><xref:System.ServiceModel.Activation.WebServiceHostFactory>Přidá <xref:System.ServiceModel.Description.WebHttpEndpoint> standardní koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="4a268-113"><xref:System.ServiceModel.Activation.WebServiceHostFactory> adds a <xref:System.ServiceModel.Description.WebHttpEndpoint> standard endpoint to the service.</span></span> <span data-ttu-id="4a268-114">Koncový bod je konfigurována na prázdnou adresu relativně k souboru .svc; To znamená, že adresu služby je http://localhost/ServiceModelSamples/service.svc s žádné další přípony jiný než název operace.</span><span class="sxs-lookup"><span data-stu-id="4a268-114">The endpoint is configured at an empty address relative to the .svc file; this means that the address of the service is http://localhost/ServiceModelSamples/service.svc, with no additional suffixes other than the operation name.</span></span>  
  
```html  
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.Samples.XmlAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebServiceHostFactory" %>  
```  
  
 <span data-ttu-id="4a268-115">V následující části v souboru Web.config lze provést další změny konfigurace ke koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="4a268-115">The following section in Web.config can be used to make additional configuration changes to the endpoint.</span></span> <span data-ttu-id="4a268-116">Může být odebrán, pokud jsou potřeba žádné další změny.</span><span class="sxs-lookup"><span data-stu-id="4a268-116">It can be removed if no extra changes are needed.</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <!-- Use this element to configure the endpoint -->  
      <standardEndpoint name="" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="4a268-117">Výchozí data formátu pro <xref:System.ServiceModel.Description.WebHttpEndpoint> XML, je při výchozí formát dat pro <xref:System.ServiceModel.Description.WebScriptEndpoint> je JSON.</span><span class="sxs-lookup"><span data-stu-id="4a268-117">The default data format for <xref:System.ServiceModel.Description.WebHttpEndpoint> is XML, while the default data format for <xref:System.ServiceModel.Description.WebScriptEndpoint> is JSON.</span></span> <span data-ttu-id="4a268-118">Další informace najdete v tématu [vytváření služeb WCF AJAX bez ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="4a268-118">For more information, see [Creating WCF AJAX Services without ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).</span></span>  
  
 <span data-ttu-id="4a268-119">Službu v následující ukázce je standard [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby s dvěma operacemi.</span><span class="sxs-lookup"><span data-stu-id="4a268-119">The service in the following sample is a standard [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service with two operations.</span></span> <span data-ttu-id="4a268-120">Obě operace vyžadují <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> body styl na <xref:System.ServiceModel.Web.WebGetAttribute> nebo <xref:System.ServiceModel.Web.WebInvokeAttribute> atributy, které je specifická pro `webHttp` chování a nemá žádný vliv na přepínač formátu dat JSON/XML.</span><span class="sxs-lookup"><span data-stu-id="4a268-120">Both operations require the <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> body style on the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes, which is specific to the `webHttp` behavior and has no bearing on the JSON/XML data format switch.</span></span>  
  
```  
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Xml, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathXml(double n1, double n2);  
```  
  
 <span data-ttu-id="4a268-121">Formát odpovědi pro tuto operaci je zadán jako XML, který je výchozí nastavení [ \<webHttp >](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) chování.</span><span class="sxs-lookup"><span data-stu-id="4a268-121">The response format for the operation is specified as XML, which is the default setting for the [\<webHttp>](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) behavior.</span></span> <span data-ttu-id="4a268-122">Ale je dobrým zvykem explicitně zadat formát odpovědi.</span><span class="sxs-lookup"><span data-stu-id="4a268-122">However, it is good practice explicitly specify the response format.</span></span>  
  
 <span data-ttu-id="4a268-123">Používá jiné operace `WebInvokeAttribute` atribut a explicitně určuje JSON místo XML pro odpověď.</span><span class="sxs-lookup"><span data-stu-id="4a268-123">The other operation uses the `WebInvokeAttribute` attribute and explicitly specifies JSON instead of XML for the response.</span></span>  
  
```  
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Json, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathJson(double n1, double n2);  
```  
  
 <span data-ttu-id="4a268-124">Všimněte si, že v obou případech vrátí operace komplexního typu, `MathResult`, což je standard [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kontraktů dat typu.</span><span class="sxs-lookup"><span data-stu-id="4a268-124">Note that in both cases the operations return a complex type, `MathResult`, which is a standard [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] data contract type.</span></span>  
  
 <span data-ttu-id="4a268-125">Klient XmlAjaxClientPage.htm webová stránka obsahuje kód JavaScript, který některé z předchozích dvou operací vyvolá, když uživatel klikne **provádění výpočtu (návratový JSON)** nebo **provádění výpočtu (návratový XML)**  tlačítka na stránce.</span><span class="sxs-lookup"><span data-stu-id="4a268-125">The client Web page XmlAjaxClientPage.htm contains JavaScript code that invokes one of the preceding two operations when the user clicks the **Perform calculation (return JSON)** or **Perform calculation (return XML)** buttons on the page.</span></span> <span data-ttu-id="4a268-126">Kód k vyvolání služby vytvoří text JSON a odešle ji pomocí HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="4a268-126">The code to invoke the service constructs a JSON body and sends it using HTTP POST.</span></span> <span data-ttu-id="4a268-127">Požadavek je vytvořen ručně v jazyce JavaScript, na rozdíl od [základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) ukázka a další ukázky pomocí prvku ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="4a268-127">The request is created manually in JavaScript, unlike the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample and the other samples using ASP.NET AJAX.</span></span>  
  
```  
// Create HTTP request  
var xmlHttp;  
// Request instantiation code omitted…  
// Result handler code omitted…  
  
// Build the operation URL  
var url = "service.svc/ajaxEndpoint/";  
url = url + operation;  
  
// Build the body of the JSON message  
var body = '{"n1":';  
body = body + document.getElementById("num1").value + ',"n2":';  
body = body + document.getElementById("num2").value + '}';  
  
// Send the HTTP request  
xmlHttp.open("POST", url, true);  
xmlHttp.setRequestHeader("Content-type", "application/json");  
xmlHttp.send(body);  
```  
  
 <span data-ttu-id="4a268-128">Když službu odpoví, zobrazí se bez dalšího zpracování do textového pole na stránce odpovědi.</span><span class="sxs-lookup"><span data-stu-id="4a268-128">When the service responds, the response is displayed without any further processing in a textbox on the page.</span></span> <span data-ttu-id="4a268-129">Tato možnost je implementovaná pro demonstrační účely, abyste mohli přímo sledovat XML a JSON formáty dat použít.</span><span class="sxs-lookup"><span data-stu-id="4a268-129">This is implemented for demonstration purposes to allow you to directly observe the XML and JSON data formats used.</span></span>  
  
```  
// Create result handler   
xmlHttp.onreadystatechange=function(){  
     if(xmlHttp.readyState == 4){  
          document.getElementById("result").value = xmlHttp.responseText;  
     }  
}  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="4a268-130">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="4a268-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4a268-131">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="4a268-131">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4a268-132">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="4a268-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4a268-133">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="4a268-133">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\XmlAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4a268-134">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="4a268-134">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="4a268-135">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4a268-135">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="4a268-136">Sestavte řešení XmlAjaxService.sln, jak je popsáno v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4a268-136">Build the solution XmlAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="4a268-137">Přejděte na http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm (neotevírejte XmlAjaxClientPage.htm v prohlížeči z adresáře projektu).</span><span class="sxs-lookup"><span data-stu-id="4a268-137">Navigate to http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm (do not open XmlAjaxClientPage.htm in the browser from the project directory).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a268-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="4a268-138">See Also</span></span>  
 [<span data-ttu-id="4a268-139">AJAX služby pomocí HTTP POST</span><span class="sxs-lookup"><span data-stu-id="4a268-139">AJAX Service Using HTTP POST</span></span>](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)