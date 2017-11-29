---
title: "Částečná důvěryhodnost"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 489b1587-9909-4d0e-8c1a-5e83c8f8292b
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f3febf1f3703377806493c8067b50c149bce0108
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="partial-trust"></a><span data-ttu-id="14284-102">Částečná důvěryhodnost</span><span class="sxs-lookup"><span data-stu-id="14284-102">Partial Trust</span></span>
<span data-ttu-id="14284-103">Od verze [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)], částečně důvěryhodné volající přístup k veřejné typy a metody implementované v <xref:System.ServiceModel>, <xref:System.Runtime.Serialization>, a <xref:System.ServiceModel.Web>.</span><span class="sxs-lookup"><span data-stu-id="14284-103">Starting with the [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)], partially trusted callers can access public types and methods implemented in <xref:System.ServiceModel>, <xref:System.Runtime.Serialization>, and <xref:System.ServiceModel.Web>.</span></span> <span data-ttu-id="14284-104">Tato část popisuje podporované scénáře použití [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] v rámci částečně důvěryhodné aplikace a také omezenou podmnožinou [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] funkce, které jsou k dispozici pro aplikace spuštěné s nižší přístupová oprávnění zabezpečení (CA) kódu.</span><span class="sxs-lookup"><span data-stu-id="14284-104">This section describes supported scenarios for using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] within a partially trusted application as well as the limited subset of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] functionality available to applications running with reduced code access security (CAS) permissions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="14284-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="14284-105">In This Section</span></span>  
 [<span data-ttu-id="14284-106">Podporované scénáře nasazení</span><span class="sxs-lookup"><span data-stu-id="14284-106">Supported Deployment Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md)  
 <span data-ttu-id="14284-107">Popisuje scénáře hlavní částečné důvěryhodnosti pro spuštění [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="14284-107">Describes the main partial trust scenarios for running [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="14284-108">Kompatibilita funkcí s částečnou důvěryhodností</span><span class="sxs-lookup"><span data-stu-id="14284-108">Partial Trust Feature Compatibility</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust-feature-compatibility.md)  
 <span data-ttu-id="14284-109">Popisuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] funkce, které nelze použít s částečnou důvěryhodností.</span><span class="sxs-lookup"><span data-stu-id="14284-109">Describes the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] features that cannot be used with partial trust.</span></span>  
  
 [<span data-ttu-id="14284-110">Doporučené postupy s částečnou důvěryhodností</span><span class="sxs-lookup"><span data-stu-id="14284-110">Partial Trust Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md)  
 <span data-ttu-id="14284-111">Obsahuje osvědčené postupy pro použití [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] v částečně důvěryhodné aplikace.</span><span class="sxs-lookup"><span data-stu-id="14284-111">Contains best practices for using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] in partially trusted applications.</span></span>