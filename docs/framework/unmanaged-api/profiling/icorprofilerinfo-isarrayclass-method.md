---
title: "ICorProfilerInfo::IsArrayClass – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.IsArrayClass
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::IsArrayClass
helpviewer_keywords:
- IsArrayClass method [.NET Framework profiling]
- ICorProfilerInfo::IsArrayClass method [.NET Framework profiling]
ms.assetid: 7f230961-23a6-4d56-ad2d-7a876d65705f
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cd07541095158d17b80333b83015d6b1f33a5dcc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfoisarrayclass-method"></a><span data-ttu-id="12828-102">ICorProfilerInfo::IsArrayClass – metoda</span><span class="sxs-lookup"><span data-stu-id="12828-102">ICorProfilerInfo::IsArrayClass Method</span></span>
<span data-ttu-id="12828-103">Určuje, zda je pro zadanou třídu třídu pole.</span><span class="sxs-lookup"><span data-stu-id="12828-103">Determines whether the specified class is an array class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12828-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12828-104">Syntax</span></span>  
  
```  
HRESULT IsArrayClass(  
    [in]  ClassID        classId,  
    [out] CorElementType *pBaseElemType,  
    [out] ClassID        *pBaseClassId,  
    [out] ULONG          *pcRank);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="12828-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="12828-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="12828-106">[v] ID třídy prověřit.</span><span class="sxs-lookup"><span data-stu-id="12828-106">[in] The ID of the class to be examined.</span></span>  
  
 `pBaseElemType`  
 <span data-ttu-id="12828-107">[out] Ukazatel na hodnotu CorElementType – výčet, který určuje typ prvků pole.</span><span class="sxs-lookup"><span data-stu-id="12828-107">[out] A pointer to a value of the CorElementType enumeration that indicates the type of the array elements.</span></span>  
  
 `pBaseClassId`  
 <span data-ttu-id="12828-108">[out] Ukazatel na ID třídy prvků pole, pokud je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="12828-108">[out] A pointer to the class ID of the array elements, when available.</span></span>  
  
 `pcRank`  
 <span data-ttu-id="12828-109">[out] Ukazatel na celé číslo, které určuje pořadí pole (tj, počet dimenzí).</span><span class="sxs-lookup"><span data-stu-id="12828-109">[out] A pointer to an integer that indicates the rank (that is, number of dimensions) of the array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12828-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="12828-110">Remarks</span></span>  
 <span data-ttu-id="12828-111">Pokud pro zadanou třídu je třída pole, `IsArrayClass` metoda vrátí S_OK HRESULT a hodnoty pro všechny nesmí být nulová výstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="12828-111">If the specified class is an array class, the `IsArrayClass` method returns an S_OK HRESULT and values for any non-null output parameters.</span></span> <span data-ttu-id="12828-112">V opačném případě vrátí S_FALSE.</span><span class="sxs-lookup"><span data-stu-id="12828-112">Otherwise, it returns S_FALSE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12828-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="12828-113">Requirements</span></span>  
 <span data-ttu-id="12828-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12828-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12828-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="12828-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="12828-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12828-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12828-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12828-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12828-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="12828-118">See Also</span></span>  
 [<span data-ttu-id="12828-119">Icorprofilerinfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="12828-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)