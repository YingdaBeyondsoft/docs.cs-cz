---
title: "&lt;System.Web&gt; – Element (webové nastavení)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 44a978eae9ae85e1ba12f117288a3c9ce4db75b4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltsystemwebgt-element-web-settings"></a><span data-ttu-id="537d2-102">&lt;System.Web&gt; – Element (webové nastavení)</span><span class="sxs-lookup"><span data-stu-id="537d2-102">&lt;system.web&gt; Element (Web Settings)</span></span>
<span data-ttu-id="537d2-103">Obsahuje informace o správě procesy chování vrstvě hostování technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="537d2-103">Contains information about how the ASP.NET hosting layer manages process-wide behavior.</span></span>  
  
 <span data-ttu-id="537d2-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="537d2-104">\<configuration></span></span>  
<span data-ttu-id="537d2-105">\<System.Web > elementu (webové nastavení)</span><span class="sxs-lookup"><span data-stu-id="537d2-105">\<system.web> Element (Web Settings)</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="537d2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="537d2-106">Syntax</span></span>  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="537d2-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="537d2-107">Attributes and Elements</span></span>  
 <span data-ttu-id="537d2-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="537d2-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="537d2-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="537d2-109">Attributes</span></span>  
 <span data-ttu-id="537d2-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="537d2-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="537d2-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="537d2-111">Child Elements</span></span>  
  
|<span data-ttu-id="537d2-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="537d2-112">Element</span></span>|<span data-ttu-id="537d2-113">Popis</span><span class="sxs-lookup"><span data-stu-id="537d2-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="537d2-114">\<applicationPool ></span><span class="sxs-lookup"><span data-stu-id="537d2-114">\<applicationPool></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|<span data-ttu-id="537d2-115">Určuje nastavení konfigurace pro fondy aplikací služby IIS v soubor aspnet.config.</span><span class="sxs-lookup"><span data-stu-id="537d2-115">Specifies configuration settings for IIS application pools in an aspnet.config file.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="537d2-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="537d2-116">Parent Elements</span></span>  
  
|<span data-ttu-id="537d2-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="537d2-117">Element</span></span>|<span data-ttu-id="537d2-118">Popis</span><span class="sxs-lookup"><span data-stu-id="537d2-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="537d2-119">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="537d2-119">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="537d2-120">Určuje kořenový element v každém konfiguračním souboru, který je používán modul common language runtime a [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="537d2-120">Specifies the root element in every configuration file that is used by the common language runtime and [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="537d2-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="537d2-121">Remarks</span></span>  
 <span data-ttu-id="537d2-122">`system.web` Elementu a jeho podřízené `applicationPool` element byly přidány do [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] od [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="537d2-122">The `system.web` element and its child `applicationPool` element were added to the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] as of [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span></span> <span data-ttu-id="537d2-123">Při spuštění [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] nebo novější verze v integrovaném režimu, tato kombinace element vám umožní nakonfigurovat jak ASP.NET spravuje vláken a jak ho fronty požadavků při ASP.NET je hostovaná ve fondu aplikací služby IIS.</span><span class="sxs-lookup"><span data-stu-id="537d2-123">When you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or later versions in Integrated mode, this element combination lets you configure how ASP.NET manages threads and how it queues requests when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="537d2-124">Pokud spustíte [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] nebo novější verze v režimu Classic nebo ISAPI, tato nastavení ignorují.</span><span class="sxs-lookup"><span data-stu-id="537d2-124">If you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or later versions in Classic or ISAPI mode, these settings are ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="537d2-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="537d2-125">Example</span></span>  
 <span data-ttu-id="537d2-126">Následující příklad ukazuje, jak nakonfigurovat chování procesy ASP.NET v souboru aspnet.config, pokud technologie ASP.NET je hostovaná ve fondu aplikací služby IIS.</span><span class="sxs-lookup"><span data-stu-id="537d2-126">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="537d2-127">Příklad předpokládá, že je služba IIS spuštěna v integrovaném režimu a zda je aplikace pomocí [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] nebo novější.</span><span class="sxs-lookup"><span data-stu-id="537d2-127">The example assumes that IIS is running in Integrated mode and that the application is using the [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] or a later version.</span></span> <span data-ttu-id="537d2-128">Toto chování se nevyskytuje ve verzích [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] starší než [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="537d2-128">This behavior does not occur in versions of the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] earlier than the [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span></span> <span data-ttu-id="537d2-129">Hodnoty v příkladu jsou výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="537d2-129">The values in the example are the default values.</span></span>  
  
```xml  
<configuration>  
  <system.web>  
    <applicationPool   
        maxConcurrentRequestsPerCPU="5000"   
        maxConcurrentThreadsPerCPU="0"   
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="537d2-130">Informace o elementu</span><span class="sxs-lookup"><span data-stu-id="537d2-130">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="537d2-131">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="537d2-131">Namespace</span></span>||  
|<span data-ttu-id="537d2-132">Název schématu</span><span class="sxs-lookup"><span data-stu-id="537d2-132">Schema Name</span></span>||  
|<span data-ttu-id="537d2-133">Ověření souboru</span><span class="sxs-lookup"><span data-stu-id="537d2-133">Validation File</span></span>||  
|<span data-ttu-id="537d2-134">Může být prázdný</span><span class="sxs-lookup"><span data-stu-id="537d2-134">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="537d2-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="537d2-135">See Also</span></span>  
 [<span data-ttu-id="537d2-136">\<applicationPool > – Element (webové nastavení)</span><span class="sxs-lookup"><span data-stu-id="537d2-136">\<applicationPool> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)