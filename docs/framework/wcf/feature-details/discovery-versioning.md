---
title: "Správa verzí zjišťování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f91c6d0a-3af2-45c5-9a5c-e75390619836
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bb9855f590fd02cc11448568b211f85ee6a951cd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="discovery-versioning"></a><span data-ttu-id="bc9e5-102">Správa verzí zjišťování</span><span class="sxs-lookup"><span data-stu-id="bc9e5-102">Discovery Versioning</span></span>
<span data-ttu-id="bc9e5-103">Toto téma obsahuje stručný přehled implementace některé nové funkce zjišťování.</span><span class="sxs-lookup"><span data-stu-id="bc9e5-103">This topic provides a brief overview of the implementation of some new discovery features.</span></span> <span data-ttu-id="bc9e5-104">Také nabízí přehled o tom, jak vybrat zjišťování verze se má použít.</span><span class="sxs-lookup"><span data-stu-id="bc9e5-104">It also gives an overview on how to select the discovery version to use.</span></span>  
  
## <a name="discovery-versioning"></a><span data-ttu-id="bc9e5-105">Správa verzí zjišťování</span><span class="sxs-lookup"><span data-stu-id="bc9e5-105">Discovery Versioning</span></span>  
 <span data-ttu-id="bc9e5-106">Funkci zjišťování zahrnuje podporu pro tři verze WS_Discovery protokolu.</span><span class="sxs-lookup"><span data-stu-id="bc9e5-106">The discovery feature includes support for three versions of the WS_Discovery protocol.</span></span> <span data-ttu-id="bc9e5-107">Zjišťování rozhraní API lze vybrat možnost, která verze protokolu, kterou chcete použít.</span><span class="sxs-lookup"><span data-stu-id="bc9e5-107">The discovery APIs allow you to select which version of the protocol you want to use.</span></span> <span data-ttu-id="bc9e5-108">Tento dokument stručně popisuje nastavení týkající se správy verzí.</span><span class="sxs-lookup"><span data-stu-id="bc9e5-108">This document briefly describes the versioning-related settings.</span></span>  
  
 <span data-ttu-id="bc9e5-109">Následující třídy zjišťování teď mají <xref:System.ServiceModel.Discovery.DiscoveryVersion> vlastnost a proveďte <xref:System.ServiceModel.Discovery.DiscoveryVersion> argument v jejich konstruktory:</span><span class="sxs-lookup"><span data-stu-id="bc9e5-109">The following Discovery classes now have a <xref:System.ServiceModel.Discovery.DiscoveryVersion> property and take a <xref:System.ServiceModel.Discovery.DiscoveryVersion> argument in their constructors:</span></span>  
  
-   <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
  
### <a name="discoveryversionwsdiscoveryapril2005"></a><span data-ttu-id="bc9e5-110">DiscoveryVersion.WSDiscoveryApril2005</span><span class="sxs-lookup"><span data-stu-id="bc9e5-110">DiscoveryVersion.WSDiscoveryApril2005</span></span>  
 <span data-ttu-id="bc9e5-111">Poskytnutí <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryApril2005> jako konstruktor parametr díky implementace použít April2005 verze protokolu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="bc9e5-111">Providing <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryApril2005> as a constructor parameter makes the implementation use the April2005 version of the WS-Discovery protocol.</span></span> <span data-ttu-id="bc9e5-112">Tato verze odpovídá na publikovanou verzi specifikace protokolu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="bc9e5-112">This version corresponds to the published version of the WS-Discovery protocol specification.</span></span> <span data-ttu-id="bc9e5-113">Tato verze by měl používat pro spolupráci s využitím April2005 verzi WS-Discovery starší verzi aplikace.</span><span class="sxs-lookup"><span data-stu-id="bc9e5-113">This version should be used to interoperate with legacy application utilizing the April2005 version of WS-Discovery.</span></span>  
  
### <a name="discoveryversionwsdiscovery11"></a><span data-ttu-id="bc9e5-114">DiscoveryVersion.WSDiscovery11</span><span class="sxs-lookup"><span data-stu-id="bc9e5-114">DiscoveryVersion.WSDiscovery11</span></span>  
 <span data-ttu-id="bc9e5-115">Výchozí verze zjišťování používá rozhraní API je <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscovery11>.</span><span class="sxs-lookup"><span data-stu-id="bc9e5-115">The default discovery version used by the APIs is <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscovery11>.</span></span> <span data-ttu-id="bc9e5-116">Toto je aktuální standardizované verzi protokolu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="bc9e5-116">This is the current standardized version of the WS-Discovery protocol.</span></span>  
  
## <a name="discoveryversionwsdiscoverycd1"></a><span data-ttu-id="bc9e5-117">DiscoveryVersion.WSDiscoveryCD1</span><span class="sxs-lookup"><span data-stu-id="bc9e5-117">DiscoveryVersion.WSDiscoveryCD1</span></span>  
 <span data-ttu-id="bc9e5-118">Poskytnutí <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryCD1> jako parametr konstruktoru vytvoří implementace použít výbor koncept 1 verze protokolu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="bc9e5-118">Providing <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryCD1> as a constructor parameter makes the implementation use the committee draft 1 version of the WS-Discovery protocol.</span></span> <span data-ttu-id="bc9e5-119">Tato verze protokolu by měl používat pro spolupráci s implementací č.1 verze protokolu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="bc9e5-119">This version of the protocol should be used to interoperate with implementations running the CD1 version of the WS-Discovery protocol.</span></span>  
  
## <a name="supporting-multiple-udp-discovery-endpoints-for-different-discovery-versions-on-a-single-service-host"></a><span data-ttu-id="bc9e5-120">Podpora víc koncových bodů UDP zjišťování pro zjišťování různé verze na hostiteli jedné služby</span><span class="sxs-lookup"><span data-stu-id="bc9e5-120">Supporting Multiple UDP Discovery Endpoints for Different Discovery Versions on a Single Service Host</span></span>  
 <span data-ttu-id="bc9e5-121">Chcete vystavit několik koncových bodů UDP zjišťování pro zjišťování různé verze na hostiteli jedné služby.</span><span class="sxs-lookup"><span data-stu-id="bc9e5-121">You may want to expose multiple UDP Discovery Endpoints for different discovery versions on a single service host.</span></span> <span data-ttu-id="bc9e5-122">K tomu musíte zadat adresu jedinečný pro každý koncový bod zjišťování UDP.</span><span class="sxs-lookup"><span data-stu-id="bc9e5-122">To do this you must specify a unique address for each UDP discovery endpoint.</span></span> <span data-ttu-id="bc9e5-123">Následující příklad ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="bc9e5-123">The following example shows how to do this.</span></span>  
  
```  
UdpDiscoveryEndpoint newVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscovery11);  
UdpDiscoveryEndpoint oldVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscoveryApril2005);  
  
newVersionUdpEndpoint.Address = new EndpointAddress(newVersionUdpEndpoint.Address.Uri.ToString() + "/version11");  
oldVersionUdpEndpoint.Address = new EndpointAddress(oldVersionUdpEndpoint.Address.Uri.ToString() + "/versionAril2005");  
  
serviceHost.AddServiceEndpoint(newVersionUdpEndpoint);  
serviceHost.AddServiceEndpoint(oldVersionUdpEndpoint);  
```