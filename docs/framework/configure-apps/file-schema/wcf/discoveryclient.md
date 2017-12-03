---
title: '&lt;objekty discoveryClient&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 55c8b9a01eaf53105968e044aecb7e38ad691aac
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltdiscoveryclientgt"></a><span data-ttu-id="f3207-102">&lt;objekty discoveryClient&gt;</span><span class="sxs-lookup"><span data-stu-id="f3207-102">&lt;discoveryClient&gt;</span></span>
<span data-ttu-id="f3207-103">Element konfigurace pro vytvoření vlastní vazby, která umožňuje klientskou aplikaci, aby automaticky vyhledat zjistitelný službu a najděte jeho adresa za běhu.</span><span class="sxs-lookup"><span data-stu-id="f3207-103">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="f3207-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="f3207-104">\<system.serviceModel></span></span>  
<span data-ttu-id="f3207-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="f3207-105">\<bindings></span></span>  
<span data-ttu-id="f3207-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="f3207-106">\<customBinding></span></span>  
<span data-ttu-id="f3207-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="f3207-107">\<binding></span></span>  
<span data-ttu-id="f3207-108">\<objekty discoveryClient ></span><span class="sxs-lookup"><span data-stu-id="f3207-108">\<discoveryClient></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3207-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3207-109">Syntax</span></span>  
  
```xml  
<discoveryClient discoveryEndpoint="String" >
  <findCriteria duration="TimeSpan" maxResults="Integer" scopeMatchBy="Uri">
    <contractTypeNames>
      <add name="String" namespace="String" />
    <contractTypeNames>
    <extensions />
    <scopes>
      <add scope="URI"/>
    </scopes>
  </findCriteria>
</discoveryClient>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3207-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f3207-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f3207-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f3207-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3207-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="f3207-112">Attributes</span></span>  
  
|<span data-ttu-id="f3207-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="f3207-113">Attribute</span></span>|<span data-ttu-id="f3207-114">Popis</span><span class="sxs-lookup"><span data-stu-id="f3207-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f3207-115">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="f3207-115">discoveryEndpoint</span></span>|<span data-ttu-id="f3207-116">Řetězec, který obsahuje název koncového bodu zjišťování, který umožňuje klientskou aplikaci, aby automaticky vyhledat zjistitelný službu a najděte jeho adresa za běhu.</span><span class="sxs-lookup"><span data-stu-id="f3207-116">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3207-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f3207-117">Child Elements</span></span>  
  
|<span data-ttu-id="f3207-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="f3207-118">Element</span></span>|<span data-ttu-id="f3207-119">Popis</span><span class="sxs-lookup"><span data-stu-id="f3207-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3207-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="f3207-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="f3207-121">Konfigurace element, který poskytuje sadu kritérií používané klientskou aplikaci pro vyhledávání pro službu zjišťování.</span><span class="sxs-lookup"><span data-stu-id="f3207-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="f3207-122">Kritéria mohou být seskupeny do kritéria vyhledávání (určení služby, kterou hledáte) a najděte ukončení kritéria (jak dlouho by měl poslední hledání).</span><span class="sxs-lookup"><span data-stu-id="f3207-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f3207-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f3207-123">Parent Elements</span></span>  
  
|<span data-ttu-id="f3207-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="f3207-124">Element</span></span>|<span data-ttu-id="f3207-125">Popis</span><span class="sxs-lookup"><span data-stu-id="f3207-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3207-126">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="f3207-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="f3207-127">Definuje všechny možnosti vazba vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="f3207-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f3207-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3207-128">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>  
 <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>