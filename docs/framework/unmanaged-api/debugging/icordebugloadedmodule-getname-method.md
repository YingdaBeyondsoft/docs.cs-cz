---
title: Metoda ICorDebugLoadedModule::GetName
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: aee475dfc425eea32ce4a1e5b4a081593574ba64
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugloadedmodulegetname-method"></a><span data-ttu-id="423d2-102">Metoda ICorDebugLoadedModule::GetName</span><span class="sxs-lookup"><span data-stu-id="423d2-102">ICorDebugLoadedModule::GetName Method</span></span>
<span data-ttu-id="423d2-103">Získá název načíst modulu.</span><span class="sxs-lookup"><span data-stu-id="423d2-103">Gets the name of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="423d2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="423d2-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="423d2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="423d2-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="423d2-106">[v] Počet znaků `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="423d2-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="423d2-107">[out] Ukazatel na počet znaků, které jsou ve skutečnosti zapsána do `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="423d2-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="423d2-108">[out] Pole znaků, které obsahují název načíst modulu.</span><span class="sxs-lookup"><span data-stu-id="423d2-108">[out] An array of characters that contain the name of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="423d2-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="423d2-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="423d2-110">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="423d2-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="423d2-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="423d2-111">Requirements</span></span>  
 <span data-ttu-id="423d2-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="423d2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="423d2-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="423d2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="423d2-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="423d2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="423d2-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="423d2-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="423d2-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="423d2-116">See Also</span></span>  
 [<span data-ttu-id="423d2-117">Rozhraní ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="423d2-117">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [<span data-ttu-id="423d2-118">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="423d2-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)