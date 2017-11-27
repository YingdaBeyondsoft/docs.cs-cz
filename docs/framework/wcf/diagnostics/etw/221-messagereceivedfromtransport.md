---
title: "221 – MessageReceivedFromTransport"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4995f0d5-c182-4d97-981f-6951da6df1fb
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4f977f938844f48182be6662f489506e8119fe67
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="221---messagereceivedfromtransport"></a><span data-ttu-id="9b2d3-102">221 – MessageReceivedFromTransport</span><span class="sxs-lookup"><span data-stu-id="9b2d3-102">221 - MessageReceivedFromTransport</span></span>
## <a name="properties"></a><span data-ttu-id="9b2d3-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="9b2d3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9b2d3-104">ID</span><span class="sxs-lookup"><span data-stu-id="9b2d3-104">ID</span></span>|<span data-ttu-id="9b2d3-105">221</span><span class="sxs-lookup"><span data-stu-id="9b2d3-105">221</span></span>|  
|<span data-ttu-id="9b2d3-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="9b2d3-106">Keywords</span></span>|<span data-ttu-id="9b2d3-107">EndToEndMonitoring, řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9b2d3-107">EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="9b2d3-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="9b2d3-108">Level</span></span>|<span data-ttu-id="9b2d3-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="9b2d3-109">Information</span></span>|  
|<span data-ttu-id="9b2d3-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="9b2d3-110">Channel</span></span>|<span data-ttu-id="9b2d3-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="9b2d3-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9b2d3-112">Popis</span><span class="sxs-lookup"><span data-stu-id="9b2d3-112">Description</span></span>  
 <span data-ttu-id="9b2d3-113">Tato událost je vygenerované, když Model služby přijme zprávu o z přenosu.</span><span class="sxs-lookup"><span data-stu-id="9b2d3-113">This event is emitted when the Service Model receives a message from the transport.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9b2d3-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="9b2d3-114">Message</span></span>  
 <span data-ttu-id="9b2d3-115">Dispečer přijala zprávu z přenosu.</span><span class="sxs-lookup"><span data-stu-id="9b2d3-115">The Dispatcher received a message from the transport.</span></span> <span data-ttu-id="9b2d3-116">ID korelace == '%1'.</span><span class="sxs-lookup"><span data-stu-id="9b2d3-116">Correlation ID == '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9b2d3-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="9b2d3-117">Details</span></span>  
  
|<span data-ttu-id="9b2d3-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="9b2d3-118">Data Item Name</span></span>|<span data-ttu-id="9b2d3-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="9b2d3-119">Data Item Type</span></span>|<span data-ttu-id="9b2d3-120">Popis</span><span class="sxs-lookup"><span data-stu-id="9b2d3-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9b2d3-121">ID korelace</span><span class="sxs-lookup"><span data-stu-id="9b2d3-121">Correlation ID</span></span>|`xs:GUID`|<span data-ttu-id="9b2d3-122">Aktivita ID použít ke korelaci `MessageSentToTransport` událostí ze služby nebo klienta na jeho odpovídající `MessageReceivedFromTransport` na druhém konci.</span><span class="sxs-lookup"><span data-stu-id="9b2d3-122">The activity ID used to correlate a `MessageSentToTransport` event from a service or client to its corresponding `MessageReceivedFromTransport` on the other end.</span></span>|  
|<span data-ttu-id="9b2d3-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="9b2d3-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="9b2d3-124">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="9b2d3-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="9b2d3-125">Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}.</span><span class="sxs-lookup"><span data-stu-id="9b2d3-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="9b2d3-126">Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="9b2d3-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="9b2d3-127">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="9b2d3-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="9b2d3-128">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="9b2d3-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|