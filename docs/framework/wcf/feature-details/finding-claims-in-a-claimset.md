---
title: "Hledání deklarací v sadě deklarací"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- claims [WCF], finding in a claimset
- claims [WCF]
ms.assetid: a76ce107-aeb3-47d0-bfa9-134c53664e20
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ca3f296f46f2a1603f275a92b25ffb09c3025230
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="finding-claims-in-a-claimset"></a><span data-ttu-id="89b2f-102">Hledání deklarací v sadě deklarací</span><span class="sxs-lookup"><span data-stu-id="89b2f-102">Finding Claims in a ClaimSet</span></span>
<span data-ttu-id="89b2f-103">Zkoumání obsahu <xref:System.IdentityModel.Claims.ClaimSet> pro konkrétní typy deklarací identity je běžné úlohy při použití ověřování na základě deklarace.</span><span class="sxs-lookup"><span data-stu-id="89b2f-103">Examining the content of a <xref:System.IdentityModel.Claims.ClaimSet> for particular types of claims is a common task when using claim-based authorization.</span></span> <span data-ttu-id="89b2f-104">K prozkoumání <xref:System.IdentityModel.Claims.ClaimSet> přítomnost konkrétních deklarací identit, použijte <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="89b2f-104">To examine a <xref:System.IdentityModel.Claims.ClaimSet> for the presence of particular claims, use the <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> method.</span></span> <span data-ttu-id="89b2f-105">Tato metoda poskytuje lepší výkon než iterování přímo přes <xref:System.IdentityModel.Claims.ClaimSet>.</span><span class="sxs-lookup"><span data-stu-id="89b2f-105">This method provides better performance than iterating directly over the <xref:System.IdentityModel.Claims.ClaimSet>.</span></span> <span data-ttu-id="89b2f-106">Následující příklad ukazuje toto použití.</span><span class="sxs-lookup"><span data-stu-id="89b2f-106">The following example demonstrates this usage.</span></span> <span data-ttu-id="89b2f-107">Všimněte si, že `claimType` a `claimRight` může být parametry `null`.</span><span class="sxs-lookup"><span data-stu-id="89b2f-107">Note that the `claimType` and `claimRight` parameters can be `null`.</span></span> <span data-ttu-id="89b2f-108">V takovém případě bude parametry odpovídají všechny typy deklarací identity a deklarací identity práva.</span><span class="sxs-lookup"><span data-stu-id="89b2f-108">In that case, the parameters will match all claim types and claim rights.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89b2f-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="89b2f-109">Example</span></span>  
 [!code-csharp[c_FindClaimsPerf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_findclaimsperf/cs/c_findclaimsperf.cs#2)]
 [!code-vb[c_FindClaimsPerf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_findclaimsperf/vb/c_findclaimsperf.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="89b2f-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="89b2f-110">See Also</span></span>  
 [<span data-ttu-id="89b2f-111">Správa deklarací a autorizace s modelem Identity</span><span class="sxs-lookup"><span data-stu-id="89b2f-111">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)