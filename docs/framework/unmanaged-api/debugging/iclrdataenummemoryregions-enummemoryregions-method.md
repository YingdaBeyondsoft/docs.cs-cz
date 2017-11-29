---
title: "ICLRDataEnumMemoryRegions::EnumMemoryRegions – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataEnumMemoryRegions.EnumMemoryRegions
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataEnumMemoryRegions::EnumMemoryRegions
helpviewer_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions method [.NET Framework debugging]
- EnumMemoryRegions method [.NET Framework debugging]
ms.assetid: 22d2e339-f174-40b5-a478-0b744501566f
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1393c5c803020339ef998a57b87ad495220c1046
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a><span data-ttu-id="e9539-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions – metoda</span><span class="sxs-lookup"><span data-stu-id="e9539-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions Method</span></span>
<span data-ttu-id="e9539-103">Vytvoří výčet zadané oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="e9539-103">Enumerates specified areas of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9539-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9539-104">Syntax</span></span>  
  
```  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e9539-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9539-105">Parameters</span></span>  
 `callback`  
 <span data-ttu-id="e9539-106">[v] Ukazatel na [iclrdataenummemoryregionscallback –](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance, která je volána, tato metoda pro každou oblast paměti ve výčtu oznámit ladicí program výsledku.</span><span class="sxs-lookup"><span data-stu-id="e9539-106">[in] A pointer to an [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance that is called by this method for each memory region being enumerated to notify the debugger of the result.</span></span>  
  
 <span data-ttu-id="e9539-107">Vytvoření výčtu oblasti paměti pokračovat i v případě, že zpětné volání znamená chybu.</span><span class="sxs-lookup"><span data-stu-id="e9539-107">The enumeration of memory regions continues even if the callback indicates a failure.</span></span>  
  
 `miniDumpFlags`  
 <span data-ttu-id="e9539-108">[v] Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="e9539-108">[in] Not used.</span></span>  
  
 `clrFlags`  
 <span data-ttu-id="e9539-109">[v] Hodnota [CLRDataEnumMemoryFlags](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md) výčet, který určuje oblasti paměti na vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="e9539-109">[in] A value of the [CLRDataEnumMemoryFlags](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md) enumeration that specifies the regions of memory to be enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9539-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e9539-110">Remarks</span></span>  
 <span data-ttu-id="e9539-111">Tato metoda používá zadaný [iclrdataenummemoryregionscallback –](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance oznámit volajícímu výsledků.</span><span class="sxs-lookup"><span data-stu-id="e9539-111">This method uses the specified [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance to notify the caller of results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9539-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e9539-112">Requirements</span></span>  
 <span data-ttu-id="e9539-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9539-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9539-114">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="e9539-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="e9539-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9539-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9539-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9539-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9539-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9539-117">See Also</span></span>  
 [<span data-ttu-id="e9539-118">Iclrdataenummemoryregions – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e9539-118">ICLRDataEnumMemoryRegions Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)