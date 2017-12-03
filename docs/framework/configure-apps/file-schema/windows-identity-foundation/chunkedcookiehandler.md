---
title: '&lt;chunkedCookieHandler&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 906a9e7cafca14dc4ee13dcb9eb9e59736464fd9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltchunkedcookiehandlergt"></a><span data-ttu-id="7f795-102">&lt;chunkedCookieHandler&gt;</span><span class="sxs-lookup"><span data-stu-id="7f795-102">&lt;chunkedCookieHandler&gt;</span></span>
<span data-ttu-id="7f795-103">Nakonfiguruje <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span><span class="sxs-lookup"><span data-stu-id="7f795-103">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="7f795-104">Tento element může být pouze existuje-li `mode` atribut `<cookieHandler>` element je "Výchozí" nebo "Blokové".</span><span class="sxs-lookup"><span data-stu-id="7f795-104">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>  
  
 <span data-ttu-id="7f795-105">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="7f795-105">\<system.identityModel.services></span></span>  
<span data-ttu-id="7f795-106">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="7f795-106">\<federationConfiguration></span></span>  
<span data-ttu-id="7f795-107">\<cookieHandler ></span><span class="sxs-lookup"><span data-stu-id="7f795-107">\<cookieHandler></span></span>  
<span data-ttu-id="7f795-108">\<chunkedCookieHandler ></span><span class="sxs-lookup"><span data-stu-id="7f795-108">\<chunkedCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f795-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f795-109">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Chunked||Default" >  
      <chunkedCookieHandler size=xs:int >  
      </chunkedCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f795-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7f795-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7f795-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7f795-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f795-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="7f795-112">Attributes</span></span>  
  
|<span data-ttu-id="7f795-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="7f795-113">Attribute</span></span>|<span data-ttu-id="7f795-114">Popis</span><span class="sxs-lookup"><span data-stu-id="7f795-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7f795-115">chunkSize</span><span class="sxs-lookup"><span data-stu-id="7f795-115">chunkSize</span></span>|<span data-ttu-id="7f795-116">Maximální velikost ve znacích dat souboru cookie HTTP pro všechny jednoho souboru cookie HTTP.</span><span class="sxs-lookup"><span data-stu-id="7f795-116">The maximum size, in characters, of the HTTP cookie data for any one HTTP cookie.</span></span> <span data-ttu-id="7f795-117">Musíte být opatrní při úpravě velikost bloku.</span><span class="sxs-lookup"><span data-stu-id="7f795-117">You must be careful when adjusting the chunk size.</span></span> <span data-ttu-id="7f795-118">Webových prohlížečů mají různé limity velikosti souborů cookie a počet povolený v každé doméně.</span><span class="sxs-lookup"><span data-stu-id="7f795-118">Web browsers have different limits on the size of cookies and number allowed per domain.</span></span> <span data-ttu-id="7f795-119">Například specifikace původní Netscape stanoveno, tato omezení: celkový 300 soubory cookie, 4096 bajtů za hlavička cookie (včetně metadata, ne jenom hodnoty souboru cookie) a 20 souborů cookie na jednu doménu.</span><span class="sxs-lookup"><span data-stu-id="7f795-119">For example, the original Netscape specification stipulated these limits: 300 cookies total, 4096 bytes per cookie header (including metadata, not just the cookie value), and 20 cookies per domain.</span></span> <span data-ttu-id="7f795-120">Výchozí hodnota je 2000.</span><span class="sxs-lookup"><span data-stu-id="7f795-120">The default is 2000.</span></span> <span data-ttu-id="7f795-121">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="7f795-121">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7f795-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7f795-122">Child Elements</span></span>  
 <span data-ttu-id="7f795-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="7f795-123">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7f795-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7f795-124">Parent Elements</span></span>  
  
|<span data-ttu-id="7f795-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="7f795-125">Element</span></span>|<span data-ttu-id="7f795-126">Popis</span><span class="sxs-lookup"><span data-stu-id="7f795-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f795-127">\<cookieHandler ></span><span class="sxs-lookup"><span data-stu-id="7f795-127">\<cookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|<span data-ttu-id="7f795-128">Nakonfiguruje <xref:System.IdentityModel.Services.CookieHandler> , <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) používá ke čtení a zápis souborů cookie.</span><span class="sxs-lookup"><span data-stu-id="7f795-128">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f795-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7f795-129">Remarks</span></span>  
 <span data-ttu-id="7f795-130">Pokud zadáte <xref:System.IdentityModel.Services.ChunkedCookieHandler> nastavením `mode` atribut `<cookieHandler>` element "Výchozí" nebo "Chunked", můžete zadat velikost bloku, který obslužná rutina souboru cookie používá číst a zapisovat soubory cookie zahrnutím `<chunkedCookieHandler>` podřízený element a nastavení jeho `chunkSize` atribut.</span><span class="sxs-lookup"><span data-stu-id="7f795-130">When you specify a <xref:System.IdentityModel.Services.ChunkedCookieHandler> by setting the `mode` attribute of the `<cookieHandler>` element to "Default" or "Chunked", you can specify the chunk size that the cookie handler uses to read and write cookies by including a `<chunkedCookieHandler>` child element and setting its `chunkSize` attribute.</span></span> <span data-ttu-id="7f795-131">Pokud `<chunkedCookieHandler>` element není k dispozici, je použita výchozí velikost bloku 2000 bajtů.</span><span class="sxs-lookup"><span data-stu-id="7f795-131">If the `<chunkedCookieHandler>` element is not present, the default chunk size of 2000 bytes is used.</span></span> <span data-ttu-id="7f795-132">Tento element nemůže být zadán, kdy `mode` je nastavena na hodnotu "Vlastní".</span><span class="sxs-lookup"><span data-stu-id="7f795-132">This element cannot be specified when the `mode` attribute is set to "Custom".</span></span>  
  
 <span data-ttu-id="7f795-133">`<chunkedCookieHandler>` Element je reprezentována <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="7f795-133">The `<chunkedCookieHandler>` element is represented by the <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f795-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="7f795-134">Example</span></span>  
 <span data-ttu-id="7f795-135">Následující příklad konfiguruje soubor cookie rozdělený obslužná rutina, která soubory cookie se zapisují bloky 3000 bajtů.</span><span class="sxs-lookup"><span data-stu-id="7f795-135">The following example configures a chunked cookie handler that writes cookies in chunks of 3000 bytes.</span></span>  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7f795-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="7f795-136">See Also</span></span>  
 <xref:System.IdentityModel.Services.ChunkedCookieHandler>