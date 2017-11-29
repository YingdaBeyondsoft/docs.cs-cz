---
title: "ICorDebugModule::GetEditAndContinueSnapshot – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.GetEditAndContinueSnapshot
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::GetEditAndContinueSnapshot
helpviewer_keywords:
- ICorDebugModule::GetEditAndContinueSnapshot method [.NET Framework debugging]
- GetEditAndContinueSnapshot method [.NET Framework debugging]
ms.assetid: fad94e1e-78be-440f-aa43-e0c66e0b102e
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 68525be87c322626c5b922299bce333f778cf365
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodulegeteditandcontinuesnapshot-method"></a><span data-ttu-id="ccce0-102">ICorDebugModule::GetEditAndContinueSnapshot – metoda</span><span class="sxs-lookup"><span data-stu-id="ccce0-102">ICorDebugModule::GetEditAndContinueSnapshot Method</span></span>
<span data-ttu-id="ccce0-103">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="ccce0-103">Deprecated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccce0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ccce0-104">Syntax</span></span>  
  
```  
HRESULT GetEditAndContinueSnapshot(  
    [out] ICorDebugEditAndContinueSnapshot **ppEditAndContinueSnapshot  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="ccce0-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ccce0-105">Requirements</span></span>  
 <span data-ttu-id="ccce0-106">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ccce0-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccce0-107">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ccce0-107">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ccce0-108">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ccce0-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ccce0-109">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccce0-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>