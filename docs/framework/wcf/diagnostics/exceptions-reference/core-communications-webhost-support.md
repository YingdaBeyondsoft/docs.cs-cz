---
title: "Základní komunikace: Podpora webového hostitele"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 034c501f-96f9-4ef7-9602-3ac21788fd3e
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6697df69f7397514972e64d6845298c090af379f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="core-communications-webhost-support"></a><span data-ttu-id="b6c83-102">Základní komunikace: Podpora webového hostitele</span><span class="sxs-lookup"><span data-stu-id="b6c83-102">Core Communications: Webhost Support</span></span>
<span data-ttu-id="b6c83-103">Toto téma uvádí všechny výjimky generované podpora webového hostitele.</span><span class="sxs-lookup"><span data-stu-id="b6c83-103">This topic lists all exceptions generated by Webhost Support.</span></span>  
  
## <a name="exception-list"></a><span data-ttu-id="b6c83-104">Seznam výjimek</span><span class="sxs-lookup"><span data-stu-id="b6c83-104">Exception List</span></span>  
  
|<span data-ttu-id="b6c83-105">Kód prostředku</span><span class="sxs-lookup"><span data-stu-id="b6c83-105">Resource Code</span></span>|<span data-ttu-id="b6c83-106">Řetězec prostředku</span><span class="sxs-lookup"><span data-stu-id="b6c83-106">Resource String</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="b6c83-107">Hosting_CompatibilityServiceNotHosted</span><span class="sxs-lookup"><span data-stu-id="b6c83-107">Hosting_CompatibilityServiceNotHosted</span></span>|<span data-ttu-id="b6c83-108">Tato služba vyžaduje režim kompatibility ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b6c83-108">This service requires ASP.NET compatibility.</span></span> <span data-ttu-id="b6c83-109">Musí být také hostované ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="b6c83-109">It must also be hosted in IIS.</span></span> <span data-ttu-id="b6c83-110">Buď hostitele služby IIS s režim kompatibility ASP.NET v souboru Web.config povolena, nebo nastavte vlastnost AspNetCompatibilityRequirementsAttribute.AspNetCompatibilityRequirementsMode jiné než požadovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b6c83-110">Either host the service in IIS with ASP.NET compatibility turned on in Web.config or set the AspNetCompatibilityRequirementsAttribute.AspNetCompatibilityRequirementsMode property to a value other than Required.</span></span>|  
|<span data-ttu-id="b6c83-111">Hosting_ListenerNotFoundForActivationInRecycling</span><span class="sxs-lookup"><span data-stu-id="b6c83-111">Hosting_ListenerNotFoundForActivationInRecycling</span></span>|<span data-ttu-id="b6c83-112">Žádný kanál aktivně naslouchá na zadané adrese.</span><span class="sxs-lookup"><span data-stu-id="b6c83-112">No channel is actively listening at the specified address.</span></span> <span data-ttu-id="b6c83-113">Pokud je recyklace aplikace, služby je zavřený.</span><span class="sxs-lookup"><span data-stu-id="b6c83-113">If an application is recycling, the service is closed.</span></span>|  
|<span data-ttu-id="b6c83-114">Hosting_NonHTTPInCompatibilityMode</span><span class="sxs-lookup"><span data-stu-id="b6c83-114">Hosting_NonHTTPInCompatibilityMode</span></span>|<span data-ttu-id="b6c83-115">Pouze protokoly, které jsou podporovány v rámci režim kompatibility ASP.NET jsou HTTP a HTTPS.</span><span class="sxs-lookup"><span data-stu-id="b6c83-115">The only protocols that are supported under ASP.NET compatibility are HTTP and HTTPS.</span></span> <span data-ttu-id="b6c83-116">Odeberte zadaný koncový bod, nebo zakázat režim kompatibility ASP.NET pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b6c83-116">Remove the specified endpoint or disable ASP.NET compatibility for the application.</span></span>|  
|<span data-ttu-id="b6c83-117">Hosting_ProcessNotExecutingUnderHostedContext</span><span class="sxs-lookup"><span data-stu-id="b6c83-117">Hosting_ProcessNotExecutingUnderHostedContext</span></span>|<span data-ttu-id="b6c83-118">Zadaný hostitelský processcannot být volána v rámci aktuální hostitelské prostředí.</span><span class="sxs-lookup"><span data-stu-id="b6c83-118">The specified hosting processcannot be invoked within the current hosting environment.</span></span> <span data-ttu-id="b6c83-119">Toto rozhraní API vyžaduje, že je volající aplikace hostovat v Internetové informační služby nebo aktivační služba procesů systému Windows.</span><span class="sxs-lookup"><span data-stu-id="b6c83-119">This API requires that the calling application be hosted in Internet Information Services or Windows Process Activation Service.</span></span>|  
|<span data-ttu-id="b6c83-120">Hosting_ServiceCompatibilityRequire</span><span class="sxs-lookup"><span data-stu-id="b6c83-120">Hosting_ServiceCompatibilityRequire</span></span>|<span data-ttu-id="b6c83-121">Službu nelze aktivovat, protože vyžaduje režim kompatibility ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b6c83-121">The service cannot be activated because it requires ASP.NET compatibility.</span></span> <span data-ttu-id="b6c83-122">Režim kompatibility ASP.NET není povoleno pro tuto aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b6c83-122">ASP.NET compatibility is not enabled for this application.</span></span> <span data-ttu-id="b6c83-123">Buď povolte režim kompatibility ASP.NET v souboru Web.config, nebo nastavte AspNetCompatibilityRequirementsAttribute.AspNetCompatibility.</span><span class="sxs-lookup"><span data-stu-id="b6c83-123">Either enable ASP.NET compatibility in Web.config file or set the AspNetCompatibilityRequirementsAttribute.AspNetCompatibility.</span></span>|