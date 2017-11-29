---
title: "Zpracování chyb aktivity v WF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24b68bd3-cef5-4413-ab82-2e2625f209aa
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bcb006f649fe0d2a92b4c789c435ba33916d140f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="error-handling-activities-in-wf"></a><span data-ttu-id="e9462-102">Zpracování chyb aktivity v WF</span><span class="sxs-lookup"><span data-stu-id="e9462-102">Error Handling Activities in WF</span></span>
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]<span data-ttu-id="e9462-103">poskytuje několik poskytované systémem aktivity pro implementace zpracování chyb a obnovení.</span><span class="sxs-lookup"><span data-stu-id="e9462-103"> provides several system-provided activities for implementing error handling and recovery.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="e9462-104">[Výjimky](../../../docs/framework/windows-workflow-foundation/exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="e9462-104"> [Exceptions](../../../docs/framework/windows-workflow-foundation/exceptions.md).</span></span>  
  
## <a name="error-handling-activities"></a><span data-ttu-id="e9462-105">Chyba zpracování aktivity</span><span class="sxs-lookup"><span data-stu-id="e9462-105">Error handling activities</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.Rethrow>|<span data-ttu-id="e9462-106">Znovu vyvolá poslední výjimky z uvnitř `TryCatch` aktivity.</span><span class="sxs-lookup"><span data-stu-id="e9462-106">Rethrows the last exception thrown from within a `TryCatch` activity.</span></span>|  
|<xref:System.Activities.Statements.Throw>|<span data-ttu-id="e9462-107">Vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="e9462-107">Throws an exception.</span></span>|  
|<xref:System.Activities.Statements.TryCatch>|<span data-ttu-id="e9462-108">Zpracovávání výjimek v jazyce implementuje.</span><span class="sxs-lookup"><span data-stu-id="e9462-108">Implements exception handling.</span></span>|