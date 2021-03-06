---
title: ICorProfilerInfo4::GetReJITIDs – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetReJITIDs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetReJITIDs
helpviewer_keywords:
- GetReJITIDs method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetReJITIDs method [.NET Framework profiling]
ms.assetid: 634ac28c-a5b7-4fc3-af84-256c24ca8177
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1055366576f45a7ca137b6d8170d1786c2ba4492
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455338"
---
# <a name="icorprofilerinfo4getrejitids-method"></a>ICorProfilerInfo4::GetReJITIDs – metoda
Vrátí pole ID, které identifikují všechny překompilovat JIT verze zadaná funkce, které jsou pořád ještě přidělená. To zahrnuje překompilovat JIT verze funkcí, které bylo následně vrátili zpět, ale ještě nebyla uvolněno (například když doméně aplikace, která obsahuje funkci vrácený je stále používáno).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `functionId`  
 [v] `FunctionID` Instance funkce, pro které chcete vytvořit výčet verzí.  
  
 `cReJitIds`  
 [v] Počet ID překompilovat JIT přidělené v `reJitIds` pole.  
  
 `pcReJitIds`  
 [out] Skutečný počet překompilovat JIT ID.  
  
 `reJitIds`  
 [out] Volající přidělené pole, která bude obsahovat ID překompilovat JIT pro zadanou funkci.  
  
## <a name="remarks"></a>Poznámky  
 `GetReJITIDs` Vytvoří výčet active překompilovat JIT ID pro danou funkci instance. Ji používá se stejný vzor využití jako ostatní `ICorProfilerInfo` funkce, které přijímají volající přidělené vyrovnávací paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
