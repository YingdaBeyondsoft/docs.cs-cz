---
title: '&lt;basicHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: basicHttpBinding Element
ms.assetid: 85cf1a4f-26c2-48c7-bda6-6c960d5d3fb3
caps.latest.revision: "43"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5956969c5d308ca075923a2d41630496bf0f7d78
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltbasichttpbindinggt"></a><span data-ttu-id="0e0bd-102">&lt;basicHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="0e0bd-102">&lt;basicHttpBinding&gt;</span></span>
<span data-ttu-id="0e0bd-103">Představuje vazbu, [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] služby můžete použít ke konfiguraci a vystavit koncové body, které jsou schopni komunikovat se na základě ASMX webových služeb a klientů a dalším službám, které odpovídají WS-I Basic Profile 1.1.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-103">Represents a binding that a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service can use to configure and expose endpoints that are able to communicate with ASMX-based Web services and clients and other services that conform to the WS-I Basic Profile 1.1.</span></span>  
  
 <span data-ttu-id="0e0bd-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="0e0bd-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0e0bd-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="0e0bd-105">\<bindings></span></span>  
<span data-ttu-id="0e0bd-106">\<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="0e0bd-106">\<basicHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e0bd-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e0bd-107">Syntax</span></span>  
  
```xml  
<basicHttpBinding>  
   <binding   
       allowCookies="Boolean"  
       bypassProxyOnLocal="Boolean"  
       closeTimeout="TimeSpan"   
       envelopeVersion="None/Soap11/Soap12"  
       hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
       maxBufferPoolSize="Integer"  
       maxBufferSize="Integer"  
       maxReceivedMessageSize="Integer"  
       messageEncoding="Text/Mtom"  
              name="string"   
       openTimeout="TimeSpan"   
       proxyAddress="URI"  
        receiveTimeout="TimeSpan"  
       sendTimeout="TimeSpan"  
              textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
              transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
       useDefaultWebProxy="Boolean"  
       <security mode="None/Transport/Message/TransportWithMessageCredential/TransportCredentialOnly">  
           <transport clientCredentialType="None/Basic/Digest/Ntlm/Windows/Certificate"  
                  proxyCredentialType="None/Basic/Digest/Ntlm/Windows"  
                                    realm="string" />  
           <message   
                 algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
                            clientCredentialType="UserName/Certificate"/>  
       </security>  
       <readerQuotas   
            maxArrayLength="Integer"  
            maxBytesPerRead="Integer"  
            maxDepth="Integer"             maxNameTableCharCount="Integer"                maxStringContentLength="Integer" />  
   </binding>  
</basicHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0e0bd-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0e0bd-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0e0bd-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0e0bd-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="0e0bd-110">Attributes</span></span>  
  
|<span data-ttu-id="0e0bd-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="0e0bd-111">Attribute</span></span>|<span data-ttu-id="0e0bd-112">Popis</span><span class="sxs-lookup"><span data-stu-id="0e0bd-112">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="0e0bd-113">Logická hodnota, která určuje, zda klient přijímá soubory cookie a rozšiřuje je na dalších požadavků.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-113">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="0e0bd-114">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-114">The default is `false`.</span></span><br /><br /> <span data-ttu-id="0e0bd-115">Tuto vlastnost lze použít při používání ASMX webové služby, které používají soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-115">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="0e0bd-116">Tímto způsobem mohou být jisti, že soubory cookie, kterou vrátil server se automaticky zkopírují do všechny budoucí požadavky pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-116">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="0e0bd-117">Logická hodnota, která označuje, zda Nepoužívat proxy server pro místní adresy.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-117">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="0e0bd-118">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-118">The default is `false`.</span></span><br /><br /> <span data-ttu-id="0e0bd-119">Internetových prostředků je místní, pokud má místní adresy.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-119">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="0e0bd-120">Místní adresa je ten, který je na stejném počítači, místní síti LAN nebo intranetu a identifikuje, syntakticky, absenci tečkou (.) jako identifikátory URI "http://webserver/" a "http://localhost/".</span><span class="sxs-lookup"><span data-stu-id="0e0bd-120">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs "http://webserver/" and "http://localhost/".</span></span><br /><br /> <span data-ttu-id="0e0bd-121">Nastavení tento atribut určuje, zda koncové body nakonfigurované BasicHttpBinding používat proxy server při přístupu k místním prostředkům.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-121">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="0e0bd-122">Pokud tento atribut je `true`, požadavky k místním prostředkům Internetu Nepoužívat proxy server.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-122">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="0e0bd-123">Použijte název hostitele (místo localhost), pokud chcete klientům jít přes proxy server při posuzování ke službám ve stejném počítači, když tento atribut je nastaven na `true`.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-123">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="0e0bd-124">Když tento atribut je `false`, jsou vytvářeny všechny požadavky Internetu prostřednictvím proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-124">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="0e0bd-125">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="0e0bd-126">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0e0bd-127">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-127">The default is 00:01:00.</span></span>|  
|`envelopeVersion`|<span data-ttu-id="0e0bd-128">Určuje verzi protokolu SOAP, která se používá pro zprávy zpracovávané touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-128">Specifies the version of SOAP that is used for messages that are processed by this binding.</span></span> <span data-ttu-id="0e0bd-129">Jediná platná hodnota je Soap11.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-129">The only valid value is Soap11.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="0e0bd-130">Určuje režim porovnání hostname HTTP použitá k analýze identifikátory URI.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-130">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="0e0bd-131">Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode>, což naznačuje, zda se ke zpřístupnění služby při shodujícím v identifikátoru URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-131">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="0e0bd-132">Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, který ignoruje název hostitele se shodují.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-132">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="0e0bd-133">Celočíselná hodnota, která určuje maximální množství paměti přidělené pro použití správcem vyrovnávacích pamětí zpráv, které přijímají zprávy z tohoto kanálu.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-133">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="0e0bd-134">Výchozí hodnota je 524288 (0x80000) bajtů.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-134">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="0e0bd-135">Správci vyrovnávacích minimalizuje náklady na používání vyrovnávací paměti pomocí fondu vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-135">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="0e0bd-136">Vyrovnávací paměti se vyžadují zpracování zpráv službou, při které pocházejí z kanálu.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-136">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="0e0bd-137">Pokud ve fondu vyrovnávací paměti při zpracování zprávy zatížení není dostatek paměti, musí správce vyrovnávací paměť přidělit další paměť z haldy CLR, což zvyšuje režii kolekce paměti.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-137">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="0e0bd-138">Rozsáhlé přidělení z paměti haldy CLR je jako ukazatel toho, že je příliš malá velikost fondu vyrovnávací paměti a že výkon lze zvýšit pomocí větší přidělení zvýšením limit určený tento atribut.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-138">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="0e0bd-139">Celočíselná hodnota, která určuje maximální velikost v bajtech vyrovnávací paměti, která ukládá zprávy, když jsou zpracovávány pro koncovým bodem nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-139">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="0e0bd-140">Výchozí hodnota je 65 536 bajtů.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-140">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="0e0bd-141">Kladné celé číslo, které definuje maximální velikost zprávy, v bajtech, včetně záhlaví zprávy, která lze přijímat pomocí kanálu nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-141">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="0e0bd-142">Odesílatel obdrží chybu protokolu SOAP, pokud zpráva je příliš velké vzhledem k příjemce.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-142">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="0e0bd-143">Příjemce zahodí zprávy a vytvoří položku události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-143">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="0e0bd-144">Výchozí hodnota je 65 536 bajtů.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-144">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="0e0bd-145">Definuje kodér použitá ke kódování zprávu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-145">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="0e0bd-146">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="0e0bd-146">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="0e0bd-147">-Text: Pomocí kodéru text zprávy.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-147">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="0e0bd-148">-Mtom: Pomocí kodéru zpráv přenosu organizace mechanismus 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="0e0bd-148">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="0e0bd-149">Výchozí hodnota je Text.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-149">The default is Text.</span></span> <span data-ttu-id="0e0bd-150">Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-150">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="0e0bd-151">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-151">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="0e0bd-152">Tato hodnota musí být jedinečný, protože je používán jako identifikaci pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-152">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="0e0bd-153">Má každou vazbu `name` a `namespace` atributů, které společně jednoznačně identifikovat v metadatech služby.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-153">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="0e0bd-154">Kromě toho je tento název jedinečný mezi vazby stejného typu.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-154">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="0e0bd-155">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-155">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="0e0bd-156">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="0e0bd-156">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`namespace`|<span data-ttu-id="0e0bd-157">Určuje obor názvů XML vazby.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-157">Specifies the XML namespace of the binding.</span></span> <span data-ttu-id="0e0bd-158">Výchozí hodnota je "http://tempuri.org/Bindings".</span><span class="sxs-lookup"><span data-stu-id="0e0bd-158">The default value is "http://tempuri.org/Bindings".</span></span> <span data-ttu-id="0e0bd-159">Má každou vazbu `name` a `namespace` atributů, které společně jednoznačně identifikovat v metadatech služby.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-159">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span>|  
|`openTimeout`|<span data-ttu-id="0e0bd-160">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro otevřete na dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="0e0bd-161">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0e0bd-162">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-162">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="0e0bd-163">Identifikátor URI, který obsahuje adresu proxy serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-163">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="0e0bd-164">Pokud `useSystemWebProxy` je nastaven na `true`, toto nastavení musí být `null`.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-164">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="0e0bd-165">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-165">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="0e0bd-166">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro na dokončení operace příjmu.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-166">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="0e0bd-167">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-167">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0e0bd-168">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-168">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="0e0bd-169">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-169">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="0e0bd-170">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-170">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0e0bd-171">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-171">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="0e0bd-172">Nastaví znak, nastavení kódování, který se má použít pro vysílání zpráv v vazby.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-172">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="0e0bd-173">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="0e0bd-173">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="0e0bd-174">-BigEndianUnicode: Unicode BigEndian kódování.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-174">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="0e0bd-175">-Unicode: 16bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-175">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="0e0bd-176">-UTF8: kódování 8bitové</span><span class="sxs-lookup"><span data-stu-id="0e0bd-176">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="0e0bd-177">Výchozí hodnota je UTF8.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-177">The default is UTF8.</span></span> <span data-ttu-id="0e0bd-178">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-178">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="0e0bd-179">Platná <xref:System.ServiceModel.TransferMode> hodnotu, která určuje, zda jsou zprávy do vyrovnávací paměti nebo prostřednictvím datového proudu na požadavek nebo odpověď.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-179">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="0e0bd-180">Logická hodnota, která určuje, zda má být použita automatické konfigurace proxy serveru HTTP systému, pokud je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-180">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="0e0bd-181">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-181">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0e0bd-182">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0e0bd-182">Child Elements</span></span>  
  
|<span data-ttu-id="0e0bd-183">Prvek</span><span class="sxs-lookup"><span data-stu-id="0e0bd-183">Element</span></span>|<span data-ttu-id="0e0bd-184">Popis</span><span class="sxs-lookup"><span data-stu-id="0e0bd-184">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0e0bd-185">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="0e0bd-185">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|<span data-ttu-id="0e0bd-186">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-186">Defines the security settings for the binding.</span></span> <span data-ttu-id="0e0bd-187">Tento element je typu <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-187">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="0e0bd-188">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="0e0bd-188">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="0e0bd-189">Definuje omezení na složitosti protokolu SOAP zprávy, které lze zpracovat koncovými body, které jsou konfigurovány pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-189">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="0e0bd-190">Tento element je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-190">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0e0bd-191">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0e0bd-191">Parent Elements</span></span>  
  
|<span data-ttu-id="0e0bd-192">Prvek</span><span class="sxs-lookup"><span data-stu-id="0e0bd-192">Element</span></span>|<span data-ttu-id="0e0bd-193">Popis</span><span class="sxs-lookup"><span data-stu-id="0e0bd-193">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0e0bd-194">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="0e0bd-194">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="0e0bd-195">Tento prvek obsahuje kolekci standardní a vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-195">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e0bd-196">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0e0bd-196">Remarks</span></span>  
 <span data-ttu-id="0e0bd-197">BasicHttpBinding využívá protokol HTTP jako přenosu pro odesílání zpráv SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-197">The BasicHttpBinding uses HTTP as the transport for sending SOAP 1.1 messages.</span></span> <span data-ttu-id="0e0bd-198">Službu můžete použít tuto vazbu ke zveřejnění koncové body, které odpovídají WS-I BP 1.1, jako jsou ty, které využívají klienti ASMX.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-198">A service can use this binding to expose endpoints that conform to WS-I BP 1.1, such as those that ASMX clients consume.</span></span> <span data-ttu-id="0e0bd-199">Podobně, může klient používat BasicHttpBinding komunikovat se službami vystavení koncové body, které odpovídají WS-I BP 1.1, jako je například ASMX webové služby nebo služby, které jsou nakonfigurované BasicHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-199">Similarly, a client can use the BasicHttpBinding to communicate with services exposing endpoints that conform to WS-I BP 1.1, such as ASMX Web services or services configured with the BasicHttpBinding.</span></span>  
  
 <span data-ttu-id="0e0bd-200">Zabezpečení je ve výchozím nastavení vypnuté, ale můžete přidat nastavení atribut režimu [ \<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) podřízený element hodnotu jinou než `None`.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-200">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="0e0bd-201">"Text" kódování a UTF-8 text zprávy kódování ve výchozím nastavení používá.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-201">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e0bd-202">Příklad</span><span class="sxs-lookup"><span data-stu-id="0e0bd-202">Example</span></span>  
 <span data-ttu-id="0e0bd-203">Následující příklad ukazuje použití <xref:System.ServiceModel.BasicHttpBinding> , poskytuje HTTP komunikace a maximální vzájemnou funkční spolupráci s první - a second - generation webové služby.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-203">The following example demonstrates the use of <xref:System.ServiceModel.BasicHttpBinding> that provides HTTP communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="0e0bd-204">Vazba je zadána v konfiguračních souborech pro klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-204">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="0e0bd-205">Typ vazby je zadán pomocí `binding` atribut `<endpoint>` elementu.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-205">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="0e0bd-206">Pokud chcete nakonfigurovat základní vazby a některá z jeho nastavení změnit, je nutné definovat Konfigurace vazeb.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-206">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="0e0bd-207">Koncový bod musí odkazovat Konfigurace vazeb podle názvu pomocí `bindingConfiguration` atribut `<endpoint>` elementu, jak je znázorněno v následujícím kódu konfigurace pro službu.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-207">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
```xml  
<system.serviceModel>   
  <services>  
    <service   
        type="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
       <endpoint address=""  
             binding="basicHttpBinding"  
             bindingConfiguration="Binding1"   
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
     <basicHttpBinding>  
        <binding name="Binding1"   
               hostNameComparisonMode="StrongWildcard"   
               receiveTimeout="00:10:00"  
               sendTimeout="00:10:00"  
               openTimeout="00:10:00"  
               closeTimeout="00:10:00"  
               maxReceivedMessageSize="65536"   
               maxBufferSize="65536"   
               maxBufferPoolSize="524288"   
               transferMode="Buffered"   
               messageEncoding="Text"   
               textEncoding="utf-8"  
               bypassProxyOnLocal="false"  
               useDefaultWebProxy="true" >  
              <security mode="None" />  
         </binding>  
     </basicHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
## <a name="example"></a><span data-ttu-id="0e0bd-208">Příklad</span><span class="sxs-lookup"><span data-stu-id="0e0bd-208">Example</span></span>  
 <span data-ttu-id="0e0bd-209">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-209">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="0e0bd-210">Funkce z předchozího příkladu můžete provést bindingConfiguration odebráním adresa koncového bodu a název frm vazby.</span><span class="sxs-lookup"><span data-stu-id="0e0bd-210">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name frm the binding.</span></span>  
  
```xml  
<system.serviceModel>   
  <services>  
    <service   
        type="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
       <endpoint address=""  
             binding="basicHttpBinding"  
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
     <basicHttpBinding>  
        <binding   
               hostNameComparisonMode="StrongWildcard"   
               receiveTimeout="00:10:00"  
               sendTimeout="00:10:00"  
               openTimeout="00:10:00"  
               closeTimeout="00:10:00"  
               maxReceivedMessageSize="65536"   
               maxBufferSize="65536"   
               maxBufferPoolSize="524288"   
               transferMode="Buffered"   
               messageEncoding="Text"   
               textEncoding="utf-8"  
               bypassProxyOnLocal="false"  
               useDefaultWebProxy="true" >  
              <security mode="None" />  
         </binding>  
     </basicHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="0e0bd-211">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="0e0bd-211">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e0bd-212">Viz také</span><span class="sxs-lookup"><span data-stu-id="0e0bd-212">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="0e0bd-213">Vazby</span><span class="sxs-lookup"><span data-stu-id="0e0bd-213">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="0e0bd-214">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="0e0bd-214">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="0e0bd-215">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="0e0bd-215">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="0e0bd-216">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="0e0bd-216">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)