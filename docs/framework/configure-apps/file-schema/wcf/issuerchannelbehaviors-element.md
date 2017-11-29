---
title: Element &lt;issuerChannelBehaviors&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 051525738f0138955358587a8fd25272dfdb9d28
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltissuerchannelbehaviorsgt-element"></a><span data-ttu-id="a2094-102">Element &lt;issuerChannelBehaviors&gt;</span><span class="sxs-lookup"><span data-stu-id="a2094-102">&lt;issuerChannelBehaviors&gt; Element</span></span>
<span data-ttu-id="a2094-103">Obsahuje kolekci [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] chování klienta koncový bod (definovanou v konfiguraci) má být použit při komunikaci s určeným službám tokenu služby.</span><span class="sxs-lookup"><span data-stu-id="a2094-103">Contains a collection of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="a2094-104">Chování definované nemůže obsahovat žádné [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="a2094-104">The defined behaviors cannot include any [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elements.</span></span>  
  
 <span data-ttu-id="a2094-105">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="a2094-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="a2094-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="a2094-106">\<behaviors></span></span>  
<span data-ttu-id="a2094-107">část endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="a2094-107">endpointBehaviors section</span></span>  
<span data-ttu-id="a2094-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="a2094-108">\<behavior></span></span>  
<span data-ttu-id="a2094-109">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="a2094-109">\<clientCredentials></span></span>  
<span data-ttu-id="a2094-110">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="a2094-110">\<issuedToken></span></span>  
<span data-ttu-id="a2094-111">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="a2094-111">\<issuerChannelBehaviors></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2094-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2094-112">Syntax</span></span>  
  
```xml  
<issuerChannelBehaviors>  
      <add behaviorConfiguraton="string"  
                issuerAddress="string" />  
</issuerChannelBehaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a2094-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a2094-113">Attributes and Elements</span></span>  
 <span data-ttu-id="a2094-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a2094-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a2094-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="a2094-115">Attributes</span></span>  
 <span data-ttu-id="a2094-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="a2094-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a2094-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a2094-117">Child Elements</span></span>  
  
|<span data-ttu-id="a2094-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="a2094-118">Element</span></span>|<span data-ttu-id="a2094-119">Popis</span><span class="sxs-lookup"><span data-stu-id="a2094-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a2094-120">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="a2094-120">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-issuerchannelbehaviors.md)|<span data-ttu-id="a2094-121">Chování přidá do kolekce.</span><span class="sxs-lookup"><span data-stu-id="a2094-121">Adds a behavior to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a2094-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a2094-122">Parent Elements</span></span>  
  
|<span data-ttu-id="a2094-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="a2094-123">Element</span></span>|<span data-ttu-id="a2094-124">Popis</span><span class="sxs-lookup"><span data-stu-id="a2094-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a2094-125">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="a2094-125">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="a2094-126">Určuje vlastní token používaný k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="a2094-126">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2094-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a2094-127">Remarks</span></span>  
 <span data-ttu-id="a2094-128">Pomocí tohoto prvku, pokud žádné chování (než chování, které zahrnují `<clientCredentials>` elementy) musí používat ke komunikaci se službou.</span><span class="sxs-lookup"><span data-stu-id="a2094-128">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="a2094-129">Například pokud [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) chování element musí být zahrnut.</span><span class="sxs-lookup"><span data-stu-id="a2094-129">For example, if a [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) behavior element must be included.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2094-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="a2094-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>  
 [<span data-ttu-id="a2094-131">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="a2094-131">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="a2094-132">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="a2094-132">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="a2094-133">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="a2094-133">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="a2094-134">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="a2094-134">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="a2094-135">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="a2094-135">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="a2094-136">Postupy: vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="a2094-136">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="a2094-137">Postupy: Konfigurace místního vystavitele</span><span class="sxs-lookup"><span data-stu-id="a2094-137">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="a2094-138">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="a2094-138">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)