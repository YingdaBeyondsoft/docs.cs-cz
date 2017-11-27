---
title: "Koncový bod: Počet volání s chybou"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 271e6284-9c4b-465f-b619-069e1555a5e4
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d62eb1ad10c7112696d8fa2a358db4c88ee86cb3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="endpoint-calls-faulted"></a><span data-ttu-id="1f104-102">Koncový bod: Počet volání s chybou</span><span class="sxs-lookup"><span data-stu-id="1f104-102">Endpoint: Calls Faulted</span></span>
<span data-ttu-id="1f104-103">Název čítače: Počet volání s chybou.</span><span class="sxs-lookup"><span data-stu-id="1f104-103">Counter Name: Calls Faulted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1f104-104">Popis</span><span class="sxs-lookup"><span data-stu-id="1f104-104">Description</span></span>  
 <span data-ttu-id="1f104-105">Počet volání k tomuto koncovému bodu, které mají vrátila chyby.</span><span class="sxs-lookup"><span data-stu-id="1f104-105">Number of calls to this endpoint that have returned faults.</span></span> <span data-ttu-id="1f104-106">V [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] aplikace, metody služeb komunikaci pomocí protokolu SOAP zprávy selhání informace o chybě zpracování.</span><span class="sxs-lookup"><span data-stu-id="1f104-106">In [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="1f104-107">Chyb SOAP jsou typy zpráv, které jsou součástí metadat pro operace služby a proto vytvoření kontraktu selhání, který můžou klienti používat, aby jejich spuštění více robustní nebo interaktivní.</span><span class="sxs-lookup"><span data-stu-id="1f104-107">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="1f104-108">Vzhledem k tomu, že chyb SOAP jsou vyjádřeny klientům ve formátu XML, jsou vysoce umožňuje vzájemnou spolupráci.</span><span class="sxs-lookup"><span data-stu-id="1f104-108">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f104-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="1f104-109">See Also</span></span>  
 [<span data-ttu-id="1f104-110">Určování a zpracování chyb v kontraktech a službách</span><span class="sxs-lookup"><span data-stu-id="1f104-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)