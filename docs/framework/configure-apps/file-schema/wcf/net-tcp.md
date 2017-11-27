---
title: '&lt;NET.TCP&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6cd220b07c2d8f9a24591fc6e9614099e8460139
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltnettcpgt"></a><span data-ttu-id="fe386-102">&lt;NET.TCP&gt;</span><span class="sxs-lookup"><span data-stu-id="fe386-102">&lt;net.tcp&gt;</span></span>
<span data-ttu-id="fe386-103">Určuje nastavení konfigurace sítě. TCP Port sdílení služby, která umožňuje více procesů sdílet stejný port TCP.</span><span class="sxs-lookup"><span data-stu-id="fe386-103">Specifies configuration settings for the NET.TCP Port Sharing Service, which allows multiple processes to share the same TCP port.</span></span>  
  
 <span data-ttu-id="fe386-104">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="fe386-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="fe386-105">\<NET.TCP ></span><span class="sxs-lookup"><span data-stu-id="fe386-105">\<net.tcp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe386-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe386-106">Syntax</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <net.tcp listenBacklog="Integer"  
          maxPendingAccepts="Integer"  
          maxPendingConnections="Integer"  
          receiveTimeout="TimeSpan"  
          teredoEnabled="Boolean">  
          <allowAccounts>  
             <!-- LocalSystem account -->   
             <add securityIdentifier="S-1-5-18"/>  
             <!-- LocalService account -->   
             <add securityIdentifier="S-1-5-19"/>  
             <!-- Administrators account -->   
             <add securityIdentifier="S-1-5-20"/>  
             <!-- Network Service account -->   
             <add securityIdentifier="S-1-5-32-544" />  
             <!-- IIS_IUSRS account (Vista only)-->   
             <add securityIdentifier="S-1-5-32-568"/>  
           </allowAccounts>  
       </net.tcp>  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## <a name="type"></a><span data-ttu-id="fe386-107">Typ</span><span class="sxs-lookup"><span data-stu-id="fe386-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe386-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fe386-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fe386-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fe386-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe386-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="fe386-110">Attributes</span></span>  
  
|<span data-ttu-id="fe386-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="fe386-111">Attribute</span></span>|<span data-ttu-id="fe386-112">Popis</span><span class="sxs-lookup"><span data-stu-id="fe386-112">Description</span></span>|  
|---------------|-----------------|  
|`listenBacklog`|<span data-ttu-id="fe386-113">Celé číslo, které určuje maximální počet nezpracovaných připojení, které přijímají sdíleného připojení, ale ještě nejsou odeslaných [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="fe386-113">An integer that specifies the maximum outstanding connections that are accepted from the shared connection, but are not yet dispatched to [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services.</span></span> <span data-ttu-id="fe386-114">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="fe386-114">The default is 10.</span></span>|  
|`maxPendingAccepts`|<span data-ttu-id="fe386-115">Celé číslo, které určuje maximální počet nezpracovaných souběžných přijímá vláken pro naslouchání koncový bod pro službu sdílení.</span><span class="sxs-lookup"><span data-stu-id="fe386-115">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="fe386-116">Výchozí hodnota je 2.</span><span class="sxs-lookup"><span data-stu-id="fe386-116">The default is 2.</span></span>|  
|`MaxPendingConnections`|<span data-ttu-id="fe386-117">Maximální počet připojení, která naslouchací proces může mít čeká se na aplikace akceptovat.</span><span class="sxs-lookup"><span data-stu-id="fe386-117">The maximum number of connections that the listener can have waiting to be accepted by the application.</span></span> <span data-ttu-id="fe386-118">Při překročení této hodnoty kvóty na nový příchozí připojení zahozených místo čekání na přijmout.</span><span class="sxs-lookup"><span data-stu-id="fe386-118">When this quota value is exceeded, new incoming connections are dropped rather than waiting to be accepted.</span></span> <span data-ttu-id="fe386-119">Funkce připojení jako zabezpečení zpráv může způsobit klienta otevřít víc než jedno připojení.</span><span class="sxs-lookup"><span data-stu-id="fe386-119">Connection features such as message security can cause a client to open more than one connection.</span></span> <span data-ttu-id="fe386-120">Správci služeb by měl účet pro tyto další připojení při nastavování této hodnoty kvóty.</span><span class="sxs-lookup"><span data-stu-id="fe386-120">Service administrators should account for these additional connections when setting this quota value.</span></span> <span data-ttu-id="fe386-121">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="fe386-121">The default is 10.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="fe386-122">A `TimeSpan` který určuje časový limit pro čtení dat rámcovacích a provádění připojení odeslání od připojení podtržení.</span><span class="sxs-lookup"><span data-stu-id="fe386-122">A `TimeSpan` that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="fe386-123">Výchozí hodnota je "00: 00:10".</span><span class="sxs-lookup"><span data-stu-id="fe386-123">The default is "00:00:10".</span></span>|  
|`teredoEnabled`|<span data-ttu-id="fe386-124">Logická hodnota, která označuje, zda služby Sdílení portů používá službu Microsoft Teredo pro naslouchání TCP porty jménem [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="fe386-124">A Boolean value that indicates whether the port sharing service uses Microsoft Teredo service to listen on TCP ports on behalf of [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services.</span></span> <span data-ttu-id="fe386-125">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="fe386-125">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fe386-126">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fe386-126">Child Elements</span></span>  
  
|<span data-ttu-id="fe386-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="fe386-127">Element</span></span>|<span data-ttu-id="fe386-128">Popis</span><span class="sxs-lookup"><span data-stu-id="fe386-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fe386-129">\<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="fe386-129">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="fe386-130">Kolekci elementů konfigurace, které obsahují `securityIdentifier` atribut k určení uživatelských účtů pro procesy, které hostují [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služby a je uděleno oprávnění k připojení ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="fe386-130">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fe386-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fe386-131">Parent Elements</span></span>  
  
|<span data-ttu-id="fe386-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="fe386-132">Element</span></span>|<span data-ttu-id="fe386-133">Popis</span><span class="sxs-lookup"><span data-stu-id="fe386-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fe386-134">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="fe386-134">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="fe386-135">Obsahuje nastavení konfigurace pro proces naslouchání SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="fe386-135">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe386-136">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fe386-136">Remarks</span></span>  
 <span data-ttu-id="fe386-137">Další informace o sdílení portů najdete v tématu [sdílení portů Net.TCP](http://msdn.microsoft.com/en-us/f13692ee-a179-4439-ae72-50db9534eded).</span><span class="sxs-lookup"><span data-stu-id="fe386-137">For more information on port sharing, see [Net.TCP Port Sharing](http://msdn.microsoft.com/en-us/f13692ee-a179-4439-ae72-50db9534eded).</span></span> <span data-ttu-id="fe386-138">Chcete-li pochopit, jak nakonfigurovat služby Sdílení portů, přečtěte si téma [konfigurace služby Sdílení portů Net.TCP](http://msdn.microsoft.com/en-us/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0).</span><span class="sxs-lookup"><span data-stu-id="fe386-138">To understand how to configure the port sharing service, see [Configuring the Net.TCP Port Sharing Service](http://msdn.microsoft.com/en-us/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe386-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="fe386-139">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>  
 [<span data-ttu-id="fe386-140">Sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="fe386-140">Net.TCP Port Sharing</span></span>](http://msdn.microsoft.com/en-us/f13692ee-a179-4439-ae72-50db9534eded)  
 [<span data-ttu-id="fe386-141">Konfigurace služby Sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="fe386-141">Configuring the Net.TCP Port Sharing Service</span></span>](http://msdn.microsoft.com/en-us/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0)