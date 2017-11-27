---
title: AsymmetricSecurityBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 104810fc24cfe7c4c6ddf7ee5ece9f16a345c80c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="asymmetricsecuritybindingelement"></a><span data-ttu-id="a37ba-102">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="a37ba-102">AsymmetricSecurityBindingElement</span></span>
<span data-ttu-id="a37ba-103">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="a37ba-103">AsymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a37ba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a37ba-104">Syntax</span></span>  
  
```  
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a37ba-105">Metody</span><span class="sxs-lookup"><span data-stu-id="a37ba-105">Methods</span></span>  
 <span data-ttu-id="a37ba-106">Třída AsymmetricSecurityBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="a37ba-106">The AsymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a37ba-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a37ba-107">Properties</span></span>  
 <span data-ttu-id="a37ba-108">Třída AsymmetricSecurityBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="a37ba-108">The AsymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="a37ba-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="a37ba-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="a37ba-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="a37ba-110">Data type: string</span></span>  
  
 <span data-ttu-id="a37ba-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a37ba-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a37ba-112">Pořadí zpráva šifrování a podepisování pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="a37ba-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="a37ba-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="a37ba-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="a37ba-114">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="a37ba-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="a37ba-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a37ba-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a37ba-116">Jestli vazby vyžaduje potvrzení podpisu.</span><span class="sxs-lookup"><span data-stu-id="a37ba-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a37ba-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a37ba-117">Requirements</span></span>  
  
|<span data-ttu-id="a37ba-118">MOF</span><span class="sxs-lookup"><span data-stu-id="a37ba-118">MOF</span></span>|<span data-ttu-id="a37ba-119">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="a37ba-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a37ba-120">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="a37ba-120">Namespace</span></span>|<span data-ttu-id="a37ba-121">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a37ba-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a37ba-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="a37ba-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>