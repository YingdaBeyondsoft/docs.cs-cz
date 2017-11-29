---
title: "ICorProfilerInfo4 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4
helpviewer_keywords: ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 80a5308e-c22f-4201-ba89-31cc8562515b
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: db91347ad2c951c28ea7b653336450929d37bdcb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo4-interface"></a>ICorProfilerInfo4 – rozhraní
Poskytuje metody, které profilery kódu se používají ke komunikaci s modul common language runtime (CLR) k řízení sledování událostí a informace o požadavku. . `ICorProfilerInfo4` Rozhraní je rozšířením dalších `ICorProfilerInfo` rozhraní. Poskytuje nové metody pro podporu rekompilace v běhu (JIT), přidán do [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Enumjitedfunctions2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)|Vrátí enumerátor pro všechny funkce, které byly dříve kompilována a překompilovat JIT.|  
|[Enumthreads – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumthreads-method.md)|Získá enumerátor, který poskytuje metody pro postupně iteraci prostřednictvím kolekce všech spravovaných vláken v procesu PROFILOVANÉHO.|  
|[Getcodeinfo3 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)|Získá rozsah nativního kódu přidružené verze překompilovat JIT zadanou funkci.|  
|[Getfunctionfromip2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getfunctionfromip2-method.md)|Ukazatel instrukce spravovaného kódu se mapuje na verzi překompilovat JIT zadanou funkci.|  
|[Getiltonativemapping2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)|Získá mapu od společnosti Microsoft (MSIL intermediate language) posune do nativní posunutí pro kód obsažené ve verzi překompilovat JIT zadanou funkci.|  
|[Getobjectsize2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)|Vrátí velikost zadaný objekt.|  
|[Getrejitids – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getrejitids-method.md)|Vrátí pole ID, které identifikují všechny překompilovat JIT verze zadaná funkce, které jsou pořád ještě přidělená.|  
|[Initializecurrentthread – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-initializecurrentthread-method.md)|Inicializuje aktuální vlákno předem následné profileru, které volání rozhraní API ve stejném vlákně, takže se vyhnout této vzájemného zablokování.|  
|[Requestrejit – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)|Požadavky JIT rekompilace všech instancí určených funkcí.|  
|[Requestrevert – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)|Vrátí všechny výskyty určených funkcí jejich původní verze.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR implementuje metody `ICorProfilerInfo4` rozhraní pomocí modelu podprocesy. Každá metoda vrátí HRESULT indikující úspěch nebo selhání. Seznam možných návratové kódy naleznete v souboru CorError.h.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Icorprofilerinfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)