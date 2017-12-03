---
title: "Trasování a protokolování zpráv"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
caps.latest.revision: "53"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d37e050933f0f94a74fcabe3afe007ad2333d58a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="tracing-and-message-logging"></a><span data-ttu-id="5e4f2-102">Trasování a protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="5e4f2-102">Tracing and Message Logging</span></span>
<span data-ttu-id="5e4f2-103">Tento příklad znázorňuje postup povolení trasování a protokolování zpráv.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-103">This sample demonstrates how to enable tracing and message logging.</span></span> <span data-ttu-id="5e4f2-104">Výsledné trasování a protokolů zpráv jsou zobrazit pomocí [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="5e4f2-104">The resulting traces and message logs are viewed using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="5e4f2-105">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="5e4f2-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e4f2-106">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="tracing"></a><span data-ttu-id="5e4f2-107">Trasování</span><span class="sxs-lookup"><span data-stu-id="5e4f2-107">Tracing</span></span>  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="5e4f2-108">používá mechanismus trasování definovaný v <xref:System.Diagnostics> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-108"> uses the tracing mechanism defined in the <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="5e4f2-109">V tomto modelu trasování dat trasování je produkovaný trasování zdrojů, které implementují aplikace.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-109">In this tracing model, trace data is produced by trace sources that applications implement.</span></span> <span data-ttu-id="5e4f2-110">Každý zdroj je identifikována názvem.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-110">Each source is identified by a name.</span></span> <span data-ttu-id="5e4f2-111">Trasování uživatelé vytváří trasování – moduly naslouchání pro trasování zdrojů, pro které se chcete získat informace.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-111">Trace consumers create trace listeners for the trace sources for which they want to retrieve information.</span></span> <span data-ttu-id="5e4f2-112">Pro příjem dat trasování, je nutné vytvořit naslouchací proces pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-112">To receive trace data, you must create a listener for the trace source.</span></span> <span data-ttu-id="5e4f2-113">V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], tento krok můžete provést přidáním následující kód do buď služby nebo klienta konfigurační soubor nastavením zdroj trasování modelu služby `switchValue`:</span><span class="sxs-lookup"><span data-stu-id="5e4f2-113">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], this can be done by adding the following code to either the service’s or client’s configuration file by setting the Service Model trace source `switchValue`:</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-service.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>  
```  
  
 <span data-ttu-id="5e4f2-114">Další informace o trasování zdrojů, najdete v části Zdroj trasování v [Konfigurace trasování](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-114">For more information about trace sources, see the Trace Source section in the [Configuring Tracing](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) topic.</span></span>  
  
## <a name="activity-tracing-and-propagation"></a><span data-ttu-id="5e4f2-115">Trasování aktivit a šíření</span><span class="sxs-lookup"><span data-stu-id="5e4f2-115">Activity Tracing and Propagation</span></span>  
 <span data-ttu-id="5e4f2-116">S `ActivityTracing` povolená a `propagateActivity` nastavena na `true` v `system.ServiceModel` zdroje trasování pro klienta a služby poskytovat korelace trasování v rámci logické jednotky zpracování (aktivity), mezi aktivity v rámci (koncové body prostřednictvím přenosu aktivity) a napříč aktivity pokrývání uzlů několik koncových bodů (prostřednictvím šíření ID aktivity).</span><span class="sxs-lookup"><span data-stu-id="5e4f2-116">Having `ActivityTracing` enabled and `propagateActivity` set to `true` in the `system.ServiceModel` trace sources for both the client and service provide correlation of traces within logical units of processing (activities), across activities within endpoints (through activity transfers), and across activities spanning multiple endpoints (through activity ID propagation).</span></span>  
  
 <span data-ttu-id="5e4f2-117">Tyto tři mechanismy (aktivit, přenosy a šíření) můžete najít další rychle pomocí nástroje prohlížeče trasování služeb hlavní příčinu chyby.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-117">These three mechanisms (activities, transfers, and propagation) can help you locate the root cause of an error more quickly using the Service Trace Viewer tool.</span></span> <span data-ttu-id="5e4f2-118">Další informace najdete v tématu [pomocí prohlížeče trasování služeb pro zobrazení korelační trasování a Poradce při potížích s](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="5e4f2-118">For more information, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span></span>  
  
 <span data-ttu-id="5e4f2-119">Je možné rozšířit trasování ServiceModel od tak, že vytvoříte vlastní aktivitu trasování.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-119">It is possible to extend the tracing that is provided by the ServiceModel by creating user-defined activity traces.</span></span> <span data-ttu-id="5e4f2-120">Trasování aktivit uživatelem definované umožňuje uživateli vytvořit trasování aktivity:</span><span class="sxs-lookup"><span data-stu-id="5e4f2-120">User-defined activity tracing allows the user to create trace activities to:</span></span>  
  
-   <span data-ttu-id="5e4f2-121">Skupiny trasování do logické jednotky práce.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-121">Group traces into logical units of work.</span></span>  
  
-   <span data-ttu-id="5e4f2-122">Korelovat aktivity prostřednictvím přenosů a šíření.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-122">Correlate activities through transfers and propagation.</span></span>  
  
-   <span data-ttu-id="5e4f2-123">Snížit náklady na výkon [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] trasování (například disk místo náklady souboru protokolu).</span><span class="sxs-lookup"><span data-stu-id="5e4f2-123">Lessen the performance cost of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tracing (for example, the disk space cost of a log file).</span></span>  
  
 <span data-ttu-id="5e4f2-124">Další informace o trasování aktivity definovaný uživatelem, najdete v tématu [rozšíření trasování](../../../../docs/framework/wcf/samples/extending-tracing.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-124">For more information about user-defined activity trace, please see the [Extending Tracing](../../../../docs/framework/wcf/samples/extending-tracing.md) sample.</span></span>  
  
## <a name="message-logging"></a><span data-ttu-id="5e4f2-125">Protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="5e4f2-125">Message Logging</span></span>  
 <span data-ttu-id="5e4f2-126">Protokolování zpráv se dá nastavit klienta a služby všech [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-126">Message logging can be enabled both on the client and service of any [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application.</span></span> <span data-ttu-id="5e4f2-127">Pokud chcete povolit protokolování zpráv, musíte přidat následující kód u klienta nebo služby:</span><span class="sxs-lookup"><span data-stu-id="5e4f2-127">To enable message logging, you must add the following code to either the client or service:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics>  
      <!-- Enable Message Logging here. -->  
      <!-- log all messages received or sent at the transport or service model levels >  
      <messageLogging logEntireMessage="true"  
                      maxMessagesToLog="300"  
                      logMessagesAtServiceLevel="true"  
                      logMalformedMessages="true"  
                      logMessagesAtTransportLevel="true" />  
    </diagnostics>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="5e4f2-128">Když se zaznamená zprávu, typ trasování, závisí na tom, jestli jsou trasovány na klienta nebo serveru.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-128">When a message is recorded, the trace type depends on whether it is being traced at the client or the server.</span></span> <span data-ttu-id="5e4f2-129">Například zprávu "Přidat", které je odesláno klienta trasovaný v kategorii "TransportWrite" na straně klienta, zatímco stejnou zprávu trasovaný v kategorii "TransportRead" na službu.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-129">For example, an "Add" message that is sent to a client is traced under the "TransportWrite" category at the client, whereas the same message is traced under the "TransportRead" category at the service.</span></span>  
  
 <span data-ttu-id="5e4f2-130">Nakonfigurovat naslouchací proces trasování přidáním následující kód, který <xref:System.Diagnostics> části souboru App.config klienta nebo v souboru Web.config služby:</span><span class="sxs-lookup"><span data-stu-id="5e4f2-130">Configure the trace listener by adding the following code to the <xref:System.Diagnostics> section of the client's App.config file or the service's Web.config file:</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-client.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
  </system.diagnostics>  
```  
  
 <span data-ttu-id="5e4f2-131">Zprávy jsou protokolovány ve formátu XML v cílovém adresáři zadaný v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-131">Messages are logged in XML format in the target directory specified in the configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e4f2-132">Trasovací soubory nejsou vytvořeny bez původně vytvoření adresář protokolu.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-132">Trace files are not created without initially creating the log directory.</span></span> <span data-ttu-id="5e4f2-133">Ujistěte se, že existuje adresář C:\logs\ nebo zadejte alternativní protokolování adresář v konfiguraci naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-133">Make sure that the directory C:\logs\ exists, or specify an alternate logging directory in the listener configuration.</span></span> <span data-ttu-id="5e4f2-134">Postupujte podle pokynů počáteční nastavení na konci tohoto dokumentu pro další informace.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-134">See the initial setup instructions at the end of this document for more information.</span></span>  
  
 <span data-ttu-id="5e4f2-135">Další informace o protokolování zpráv najdete v tématu [konfigurace protokolování zpráv](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-135">For more information about message logging, see the [Configuring Message Logging](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) topic.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5e4f2-136">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="5e4f2-136">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="5e4f2-137">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5e4f2-137">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="5e4f2-138">Před spuštěním ukázky trasování a protokolování zpráv, vytvořte adresář C:\logs\ pro službu zápis .svclog soubory.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-138">Before running the Tracing and Message Logging sample, create the directory C:\logs\ for the service to write the .svclog files to.</span></span> <span data-ttu-id="5e4f2-139">Název tohoto adresáře je definována v konfiguračním souboru jako cestu pro trasování a zprávy, která je zaznamenána a lze změnit.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-139">The name of this directory is defined in the configuration file as the path for the traces and messages to be logged and can be changed.</span></span> <span data-ttu-id="5e4f2-140">Poskytněte uživatel oprávnění k zápisu síťová služba k adresáři s protokoly.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-140">Give the user Network Service write access to the logs directory.</span></span>  
  
3.  <span data-ttu-id="5e4f2-141">Sestavení C#, C++ nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5e4f2-141">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="5e4f2-142">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5e4f2-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5e4f2-143">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-143">The samples may already be installed on your computer.</span></span> <span data-ttu-id="5e4f2-144">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="5e4f2-144">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5e4f2-145">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-145">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5e4f2-146">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-146">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a><span data-ttu-id="5e4f2-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="5e4f2-147">See Also</span></span>  
 [<span data-ttu-id="5e4f2-148">Trasování</span><span class="sxs-lookup"><span data-stu-id="5e4f2-148">Tracing</span></span>](../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="5e4f2-149">Ukázky monitorování AppFabric</span><span class="sxs-lookup"><span data-stu-id="5e4f2-149">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)