---
title: "Koncový bod: Počet volání za sekundu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ca0fc06d-d68f-4236-bd5f-c7ff6214acdd
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: aeeedd05c0da46bc210f6f93e6806e3ea72ca862
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="endpoint-calls-per-second"></a><span data-ttu-id="cc11d-102">Koncový bod: Počet volání za sekundu</span><span class="sxs-lookup"><span data-stu-id="cc11d-102">Endpoint: Calls Per Second</span></span>
<span data-ttu-id="cc11d-103">Název čítače: Počet volání za sekundu.</span><span class="sxs-lookup"><span data-stu-id="cc11d-103">Counter Name: Calls Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="cc11d-104">Popis</span><span class="sxs-lookup"><span data-stu-id="cc11d-104">Description</span></span>  
 <span data-ttu-id="cc11d-105">Počet volání k tomuto koncovému bodu za sekundu.</span><span class="sxs-lookup"><span data-stu-id="cc11d-105">Number of calls to this endpoint in a second.</span></span>  
  
 <span data-ttu-id="cc11d-106">Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="cc11d-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="cc11d-107">(NE 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="cc11d-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>