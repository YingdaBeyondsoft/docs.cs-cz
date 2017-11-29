---
title: "Počet ztracených zpráv spolehlivého zasílání zpráv za sekundu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a11b0b80-b242-48e1-b0bb-7f756db5486b
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 06df77ae14dbe4980ae54cc09a0822f59731bf1c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="reliable-messaging-messages-dropped-per-second"></a><span data-ttu-id="d2f03-102">Počet ztracených zpráv spolehlivého zasílání zpráv za sekundu</span><span class="sxs-lookup"><span data-stu-id="d2f03-102">Reliable Messaging Messages Dropped Per Second</span></span>
<span data-ttu-id="d2f03-103">Název čítače: Vyřadit relací spolehlivého zasílání zpráv za sekundu.</span><span class="sxs-lookup"><span data-stu-id="d2f03-103">Counter Name: Reliable Messaging Sessions Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d2f03-104">Popis</span><span class="sxs-lookup"><span data-stu-id="d2f03-104">Description</span></span>  
 <span data-ttu-id="d2f03-105">Celkový počet zpráv spolehlivého zasílání zpráv, které byly vynechány v rámci této služby za sekundu.</span><span class="sxs-lookup"><span data-stu-id="d2f03-105">Total number of reliable messaging messages that have been dropped in this service in a second.</span></span>  
  
 <span data-ttu-id="d2f03-106">Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="d2f03-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="d2f03-107">(NE 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="d2f03-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>