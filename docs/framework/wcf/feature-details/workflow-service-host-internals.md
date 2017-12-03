---
title: "Interní informace o hostiteli služby pracovního postupu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af44596f-bf6a-4149-9f04-08d8e8f45250
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cf12cac374759c1cb45a7086ac771a982758e78f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="workflow-service-host-internals"></a><span data-ttu-id="c52b9-102">Interní informace o hostiteli služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="c52b9-102">Workflow Service Host Internals</span></span>
<span data-ttu-id="c52b9-103"><xref:System.ServiceModel.WorkflowServiceHost>poskytuje hostitele pro služby pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="c52b9-103"><xref:System.ServiceModel.WorkflowServiceHost> provides a host for workflow services.</span></span> <span data-ttu-id="c52b9-104">Zodpovídá za naslouchání pro příchozí zprávy a směrování je v instanci služby odpovídající pracovní postup, se řídí uvolnění a zachování nečinnosti pracovních postupů a další.</span><span class="sxs-lookup"><span data-stu-id="c52b9-104">It is responsible for listening for incoming messages and routing them to the appropriate workflow service instance, it controls unloading and persisting of idle workflows, and more.</span></span> <span data-ttu-id="c52b9-105">Toto téma popisuje, jak hostitele služby pracovního postupu zpracovává příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="c52b9-105">This topic describes how WorkflowServiceHost processes incoming messages.</span></span>  
  
## <a name="workflowservicehost-overview"></a><span data-ttu-id="c52b9-106">Přehled hostitele služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="c52b9-106">WorkflowServiceHost Overview</span></span>  
 <span data-ttu-id="c52b9-107"><xref:System.ServiceModel.WorkflowServiceHost> Třída se používá k hostování služeb pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="c52b9-107">The <xref:System.ServiceModel.WorkflowServiceHost> class is used to host workflow services.</span></span> <span data-ttu-id="c52b9-108">Ho poslouchá příchozí zprávy a směruje je do instance příslušné služby, vytvoření nové instance služby nebo načtení existující instance z odolná úložiště, podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="c52b9-108">It listens for incoming messages and routes them to the appropriate service instance, creating new instances or loading existing instances from durable storage as needed.</span></span>  <span data-ttu-id="c52b9-109">Následující diagram znázorňuje na nejvyšší úrovni jak <xref:System.ServiceModel.WorkflowServiceHost> funguje.</span><span class="sxs-lookup"><span data-stu-id="c52b9-109">The following diagram illustrates on a high level how <xref:System.ServiceModel.WorkflowServiceHost> works.</span></span>  
  
 <span data-ttu-id="c52b9-110">![Přehled hostitele služby pracovního postupu](../../../../docs/framework/wcf/feature-details/media/wfshhighlevel.gif "WFSHHighLevel")</span><span class="sxs-lookup"><span data-stu-id="c52b9-110">![WorkflowServiceHost Overview](../../../../docs/framework/wcf/feature-details/media/wfshhighlevel.gif "WFSHHighLevel")</span></span>  
  
 <span data-ttu-id="c52b9-111">Tento diagram ukazuje, že <xref:System.ServiceModel.WorkflowServiceHost> načte definice pracovního postupu služby z .xamlx souborů a načte informace o konfiguraci z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="c52b9-111">This diagram shows that <xref:System.ServiceModel.WorkflowServiceHost> loads workflow service definitions from .xamlx files and loads configuration information from a configuration file.</span></span> <span data-ttu-id="c52b9-112">Konfigurace sledování také načtenou z profilu sledování.</span><span class="sxs-lookup"><span data-stu-id="c52b9-112">It also loads tracking configuration from the tracking profile.</span></span> <span data-ttu-id="c52b9-113"><xref:System.ServiceModel.WorkflowServiceHost>zpřístupní koncový bod pracovního postupu ovládací prvek, který umožňuje odeslat operace ovládacího prvku do instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="c52b9-113"><xref:System.ServiceModel.WorkflowServiceHost> exposes a workflow control endpoint which allows you to send control operations to workflow instances.</span></span>  <span data-ttu-id="c52b9-114">Další informace najdete v části [kontrolní koncový bod pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md) a [ukázka koncový bod pracovního postupu správy](../../../../docs/framework/windows-workflow-foundation/samples/workflow-management-endpoint-sample.md).</span><span class="sxs-lookup"><span data-stu-id="c52b9-114">For more information see [Workflow Control Endpoint](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md) and [Workflow Management Endpoint Sample](../../../../docs/framework/windows-workflow-foundation/samples/workflow-management-endpoint-sample.md).</span></span>  
  
 <span data-ttu-id="c52b9-115"><xref:System.ServiceModel.WorkflowServiceHost>také poskytuje koncových bodů aplikace, které přijímat příchozí zprávy aplikace.</span><span class="sxs-lookup"><span data-stu-id="c52b9-115"><xref:System.ServiceModel.WorkflowServiceHost> also exposes application endpoints that listen for incoming application messages.</span></span> <span data-ttu-id="c52b9-116">Pokud dorazí příchozí zprávy odesláním v instanci služby příslušné pracovního postupu (Pokud je aktuálně načtený).</span><span class="sxs-lookup"><span data-stu-id="c52b9-116">When an incoming message arrives it is sent to the appropriate workflow service instance (if it is currently loaded).</span></span> <span data-ttu-id="c52b9-117">V případě potřeby novou instanci pracovního postupu se vytvoří.</span><span class="sxs-lookup"><span data-stu-id="c52b9-117">If needed a new workflow instance is created.</span></span> <span data-ttu-id="c52b9-118">Nebo pokud byla jako trvalé existující instance je načten z obchodu trvalost.</span><span class="sxs-lookup"><span data-stu-id="c52b9-118">Or if an existing instance has been persisted it is loaded from the persistence store.</span></span>  
  
## <a name="workflowservicehost-details"></a><span data-ttu-id="c52b9-119">Podrobnosti o hostitele služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="c52b9-119">WorkflowServiceHost Details</span></span>  
 <span data-ttu-id="c52b9-120">Následující obrázek ukazuje, jak <xref:System.ServiceModel.WorkflowServiceHost> zpracovává zprávy trochu podrobněji.</span><span class="sxs-lookup"><span data-stu-id="c52b9-120">The following diagram shows how <xref:System.ServiceModel.WorkflowServiceHost> handles messages in a bit more detail.</span></span>  
  
 <span data-ttu-id="c52b9-121">![Tok zpráv hostitele služby pracovního postupu](../../../../docs/framework/wcf/feature-details/media/wfshmessageflow.gif "WFSHMessageFlow")</span><span class="sxs-lookup"><span data-stu-id="c52b9-121">![Workflow Service Host Message Flow](../../../../docs/framework/wcf/feature-details/media/wfshmessageflow.gif "WFSHMessageFlow")</span></span>  
  
 <span data-ttu-id="c52b9-122">Tento diagram zobrazuje tři různými koncovými body, koncový bod aplikace, ovládací prvek koncový bod pracovního postupu a hostování koncový bod pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="c52b9-122">This diagram shows three different endpoints, an application endpoint, a workflow control endpoint, and a workflow hosting endpoint.</span></span> <span data-ttu-id="c52b9-123">Koncový bod aplikace přijímá zprávy, které nejsou pro instanci konkrétní pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="c52b9-123">The application endpoint receives messages that are bound for a specific workflow instance.</span></span> <span data-ttu-id="c52b9-124">Kontrolní koncový bod pracovního postupu naslouchá operace ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c52b9-124">The workflow control endpoint listens for control operations.</span></span> <span data-ttu-id="c52b9-125">Pracovní postup, který je hostitelem koncového bodu přijímá zprávy, které způsobí <xref:System.ServiceModel.WorkflowServiceHost> načtení a provedení bez služby pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="c52b9-125">The workflow hosting endpoint listens for messages that cause <xref:System.ServiceModel.WorkflowServiceHost> to load and execute non-service workflows.</span></span> <span data-ttu-id="c52b9-126">Jak je vidět v diagramu všechny zprávy jsou zpracovány WCF runtime.</span><span class="sxs-lookup"><span data-stu-id="c52b9-126">As shown in the diagram all messages are processed through the WCF runtime.</span></span>  <span data-ttu-id="c52b9-127">Omezení instance pracovního postupu služby je dosaženo pomocí <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c52b9-127">Workflow service instance throttling is achieved by using the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> property.</span></span> <span data-ttu-id="c52b9-128">Tato vlastnost omezí počet instancí služby souběžných pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="c52b9-128">This property will limit the number of concurrent workflow service instances.</span></span> <span data-ttu-id="c52b9-129">Pokud toto omezení je překročena všechny další požadavky pro nové instance služby pracovního postupu nebo žádosti o aktivaci instancí trvalou pracovního postupu se zařadí do fronty.</span><span class="sxs-lookup"><span data-stu-id="c52b9-129">When this throttle is exceeded any additional requests for new workflow service instances or requests to activate persisted workflow instances will be queued.</span></span> <span data-ttu-id="c52b9-130">Požadavky ve frontě jsou zpracovány v pořadí FIFO bez ohledu na to, zda jsou požadavky na novou instanci nebo instance spuštěný, trvalý.</span><span class="sxs-lookup"><span data-stu-id="c52b9-130">The queued requests are processed in FIFO order regardless of whether they are requests for a new instance or a running, persisted instance.</span></span> <span data-ttu-id="c52b9-131">Informace o zásadách hostitele je načtena, který určuje, jak jsou vyřešit neošetřené výjimky a nečinnosti pracovního postupu služby jsou uvolněna a trvalé.</span><span class="sxs-lookup"><span data-stu-id="c52b9-131">Host policy information is loaded that determines how unhandled exceptions are dealt with, and how idle workflow services are unloaded and persisted.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="c52b9-132">Tato témata najdete v části [postupy: Konfigurace chování pracovního postupu neošetřené výjimky pomocí třídy WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/config-workflow-unhandled-exception-workflowservicehost.md) a [postupy: Konfigurace chování nečinnosti pomocí WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/how-to-configure-idle-behavior-with-workflowservicehost.md).</span><span class="sxs-lookup"><span data-stu-id="c52b9-132"> these topics see [How to: Configure Workflow Unhandled Exception Behavior with WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/config-workflow-unhandled-exception-workflowservicehost.md) and [How to: Configure Idle Behavior with WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/how-to-configure-idle-behavior-with-workflowservicehost.md).</span></span> <span data-ttu-id="c52b9-133">Instance pracovního postupu se znovu načíst v případě potřeby a jsou nastavené jako trvalé podle zásad hostitele.</span><span class="sxs-lookup"><span data-stu-id="c52b9-133">Workflow instances are persisted according to host policies and are reloaded when needed.</span></span> <span data-ttu-id="c52b9-134">Další informace o trvalost pracovního postupu v tématu: [postupy: Konfigurace trvalosti pomocí třídy WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/how-to-configure-persistence-with-workflowservicehost.md), [vytvoření dlouhodobé služby pracovního postupu](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md), a [trvalost pracovního postupu ](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md).</span><span class="sxs-lookup"><span data-stu-id="c52b9-134">For more information about workflow persistence see: [How to: Configure Persistence with WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/how-to-configure-persistence-with-workflowservicehost.md), [Creating a Long-running Workflow Service](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md), and [Workflow Persistence](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md).</span></span>  
  
 <span data-ttu-id="c52b9-135">Následující obrázek znázorňuje, co se nazývá WorkflowServiceHost.Open.</span><span class="sxs-lookup"><span data-stu-id="c52b9-135">The following illustration shows what the WorkflowServiceHost.Open is called.</span></span>  
  
 <span data-ttu-id="c52b9-136">![Když je volána WorkflowServiceHost.Open](../../../../docs/framework/wcf/feature-details/media/wfhostopen.gif "WFHostOpen")</span><span class="sxs-lookup"><span data-stu-id="c52b9-136">![When WorkflowServiceHost.Open is called](../../../../docs/framework/wcf/feature-details/media/wfhostopen.gif "WFHostOpen")</span></span>  
  
 <span data-ttu-id="c52b9-137">Pracovní postup je načtena z XAML a k vytvoření stromu aktivity.</span><span class="sxs-lookup"><span data-stu-id="c52b9-137">The workflow is loaded from XAML and the activity tree is created.</span></span> <span data-ttu-id="c52b9-138"><xref:System.ServiceModel.WorkflowServiceHost>provede stromu aktivity a vytvoří popis služby.</span><span class="sxs-lookup"><span data-stu-id="c52b9-138"><xref:System.ServiceModel.WorkflowServiceHost> walks the activity tree and creates the service description.</span></span> <span data-ttu-id="c52b9-139">Konfigurace se použije na hostiteli.</span><span class="sxs-lookup"><span data-stu-id="c52b9-139">Configuration is applied to the host.</span></span> <span data-ttu-id="c52b9-140">Nakonec hostitele začne naslouchat pro příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="c52b9-140">Finally the host begins to listen for incoming messages.</span></span>  
  
 <span data-ttu-id="c52b9-141">Následující obrázek znázorňuje, co <xref:System.ServiceModel.WorkflowServiceHost> nepodporuje, když obdrží zprávu vázaný aktivity Receive, který má CanCreateInstance nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="c52b9-141">The following illustration shows what the <xref:System.ServiceModel.WorkflowServiceHost> does when it receives a message bound for a Receive activity that has CanCreateInstance set to `true`.</span></span>  
  
 <span data-ttu-id="c52b9-142">![Hostitel služby pracovního postupu přijme zprávu o](../../../../docs/framework/wcf/feature-details/media/wfhreceivemessagecci.gif "WFHReceiveMessageCCI")</span><span class="sxs-lookup"><span data-stu-id="c52b9-142">![Workflow Service Host Receives a message](../../../../docs/framework/wcf/feature-details/media/wfhreceivemessagecci.gif "WFHReceiveMessageCCI")</span></span>  
  
 <span data-ttu-id="c52b9-143">Zpráva dorazí a zpracovává zásobníku kanálu WCF.</span><span class="sxs-lookup"><span data-stu-id="c52b9-143">The message arrives and is processed by the WCF channel stack.</span></span> <span data-ttu-id="c52b9-144">Omezení jsou zaškrtnutá políčka a provedení korelace dotazy.</span><span class="sxs-lookup"><span data-stu-id="c52b9-144">Throttles are checked and correlation queries are executed.</span></span> <span data-ttu-id="c52b9-145">Pokud zpráva je vázaný existující instance je zpráva doručena.</span><span class="sxs-lookup"><span data-stu-id="c52b9-145">If the message is bound for an existing instance the message is delivered.</span></span> <span data-ttu-id="c52b9-146">Pokud je potřeba vytvořit novou instanci, zkontroluje se CanCreateInstance vlastnost Receive aktivity.</span><span class="sxs-lookup"><span data-stu-id="c52b9-146">If a new instance needs to be created, the Receive activity’s CanCreateInstance property is checked.</span></span> <span data-ttu-id="c52b9-147">Pokud je nastavena na hodnotu true, je vytvořena nová instance a doručí zprávy.</span><span class="sxs-lookup"><span data-stu-id="c52b9-147">If it is set to true, a new instance is created and the message is delivered.</span></span>  
  
 <span data-ttu-id="c52b9-148">Následující obrázek znázorňuje, co <xref:System.ServiceModel.WorkflowServiceHost> nepodporuje, když obdrží zprávu vázaný aktivity Receive, který má CanCreateInstance nastaven na hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="c52b9-148">The following illustration shows what the <xref:System.ServiceModel.WorkflowServiceHost> does when it receives a message bound for a Receive activity that has CanCreateInstance set to false.</span></span>  
  
 <span data-ttu-id="c52b9-149">![Hostitele služby pracovního postupu přijme zprávu o](../../../../docs/framework/wcf/feature-details/media/wfshreceivemessage.gif "WFSHReceiveMessage")</span><span class="sxs-lookup"><span data-stu-id="c52b9-149">![WorkflowServiceHost receives a message](../../../../docs/framework/wcf/feature-details/media/wfshreceivemessage.gif "WFSHReceiveMessage")</span></span>  
  
 <span data-ttu-id="c52b9-150">Zpráva dorazí a zpracovává zásobníku kanálu WCF.</span><span class="sxs-lookup"><span data-stu-id="c52b9-150">The message arrives and is processed by the WCF channel stack.</span></span> <span data-ttu-id="c52b9-151">Omezení jsou zaškrtnutá políčka a provedení korelace dotazy.</span><span class="sxs-lookup"><span data-stu-id="c52b9-151">Throttles are checked and correlation queries are executed.</span></span> <span data-ttu-id="c52b9-152">Zpráva je vázaný existující instance (protože CanCreateInstance je false) tak, aby instance je načtena z úložiště trvalosti, je obnovena záložku a spustí pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="c52b9-152">The message is bound for an existing instance (because CanCreateInstance is false) so the instance is loaded from persistence store, the bookmark is resumed and the workflow executes.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="c52b9-153">Hostitel služby pracovního postupu se nepodaří otevřít, i když systému SQL Server je nakonfigurován pro naslouchání pouze protokol pojmenovaný kanál.</span><span class="sxs-lookup"><span data-stu-id="c52b9-153">Workflow Service Host will fail to open if SQL Server is configured to listen on NamedPipe protocol only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c52b9-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="c52b9-154">See Also</span></span>  
 [<span data-ttu-id="c52b9-155">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="c52b9-155">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="c52b9-156">Hostování služeb pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="c52b9-156">Hosting Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)  
 [<span data-ttu-id="c52b9-157">Kontrolní koncový bod pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="c52b9-157">Workflow Control Endpoint</span></span>](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)  
 [<span data-ttu-id="c52b9-158">Ukázka koncový bod správy pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="c52b9-158">Workflow Management Endpoint Sample</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/workflow-management-endpoint-sample.md)  
 [<span data-ttu-id="c52b9-159">Postupy: Konfigurace pracovního postupu neošetřená výjimka chování pomocí třídy WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="c52b9-159">How to: Configure Workflow Unhandled Exception Behavior with WorkflowServiceHost</span></span>](../../../../docs/framework/wcf/feature-details/config-workflow-unhandled-exception-workflowservicehost.md)  
 [<span data-ttu-id="c52b9-160">Vytvoření dlouhodobé služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="c52b9-160">Creating a Long-running Workflow Service</span></span>](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)  
 [<span data-ttu-id="c52b9-161">Trvalost pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="c52b9-161">Workflow Persistence</span></span>](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)