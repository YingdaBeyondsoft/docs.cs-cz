---
title: '&lt;x509SecurityTokenHandlerRequirement&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
caps.latest.revision: "3"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 66d4e0d6a121f807f5f372b3f39577b0bb3c4ca6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltx509securitytokenhandlerrequirementgt"></a><span data-ttu-id="d6ae1-102">&lt;x509SecurityTokenHandlerRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="d6ae1-102">&lt;x509SecurityTokenHandlerRequirement&gt;</span></span>
<span data-ttu-id="d6ae1-103">Poskytuje volitelné konfigurace pro <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> třídu nebo odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="d6ae1-103">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="d6ae1-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="d6ae1-104">\<system.identityModel></span></span>  
<span data-ttu-id="d6ae1-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="d6ae1-105">\<identityConfiguration></span></span>  
<span data-ttu-id="d6ae1-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="d6ae1-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="d6ae1-107">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="d6ae1-107">\<add></span></span>  
<span data-ttu-id="d6ae1-108">\<x509SecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="d6ae1-108">\<x509SecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6ae1-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6ae1-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
        <x509SecurityTokenHandlerRequirement>  
          mapToWindows=xs:boolean  
          certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
          certificateValidator="Namespace.Class, Assembly"  
          revocationMode="NoCheck||Offline||Online"  
          trustedStoreLocation="CurrentUser||LocalMachine"  
        </x509SecurityTokenHandlerRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6ae1-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d6ae1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d6ae1-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d6ae1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6ae1-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="d6ae1-112">Attributes</span></span>  
  
|<span data-ttu-id="d6ae1-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="d6ae1-113">Attribute</span></span>|<span data-ttu-id="d6ae1-114">Popis</span><span class="sxs-lookup"><span data-stu-id="d6ae1-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d6ae1-115">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="d6ae1-115">certificateValidationMode</span></span>|<span data-ttu-id="d6ae1-116"><xref:System.ServiceModel.Security.X509CertificateValidationMode> Hodnotu, která určuje režim ověřování pro certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="d6ae1-116">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="d6ae1-117">Výchozí hodnota je "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="d6ae1-117">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="d6ae1-118">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="d6ae1-118">mapToWindows</span></span>|<span data-ttu-id="d6ae1-119">Určuje, zda obslužná rutina tokenu by měl mapovat ověřování tokenu účet systému Windows pomocí příchozí deklarace identity UPN.</span><span class="sxs-lookup"><span data-stu-id="d6ae1-119">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="d6ae1-120">Výchozí hodnota je "false".</span><span class="sxs-lookup"><span data-stu-id="d6ae1-120">The default is "false".</span></span>|  
|<span data-ttu-id="d6ae1-121">revocationMode</span><span class="sxs-lookup"><span data-stu-id="d6ae1-121">revocationMode</span></span>|<span data-ttu-id="d6ae1-122"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Hodnotu, která určuje režim odvolaných certifikátů pro certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="d6ae1-122">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="d6ae1-123">Výchozí hodnota je "Online".</span><span class="sxs-lookup"><span data-stu-id="d6ae1-123">The default value is "Online".</span></span>|  
|<span data-ttu-id="d6ae1-124">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="d6ae1-124">trustedStoreLocation</span></span>|<span data-ttu-id="d6ae1-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> hodnotu, která určuje úložišti certifikátů X.509.</span><span class="sxs-lookup"><span data-stu-id="d6ae1-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="d6ae1-126">Výchozí hodnota je "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="d6ae1-126">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="d6ae1-127">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="d6ae1-127">certificateValidator</span></span>|<span data-ttu-id="d6ae1-128">Vlastního typu, který je odvozen od <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="d6ae1-128">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="d6ae1-129">Pokud `certificateValidationMode` atribut je "Vlastní", instance tohoto typu se používá k ověření vystavitele certifikátu.</span><span class="sxs-lookup"><span data-stu-id="d6ae1-129">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d6ae1-130">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d6ae1-130">Child Elements</span></span>  
 <span data-ttu-id="d6ae1-131">Žádné</span><span class="sxs-lookup"><span data-stu-id="d6ae1-131">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d6ae1-132">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d6ae1-132">Parent Elements</span></span>  
  
|<span data-ttu-id="d6ae1-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="d6ae1-133">Element</span></span>|<span data-ttu-id="d6ae1-134">Popis</span><span class="sxs-lookup"><span data-stu-id="d6ae1-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d6ae1-135">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="d6ae1-135">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="d6ae1-136">Obslužná rutina tokenu zabezpečení zadaný přidá do kolekce obslužná rutina tokenu.</span><span class="sxs-lookup"><span data-stu-id="d6ae1-136">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d6ae1-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6ae1-137">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"   
                                         certificateValidationMode="PeerOrChainTrust"   
                                         revocationMode="Online"   
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```