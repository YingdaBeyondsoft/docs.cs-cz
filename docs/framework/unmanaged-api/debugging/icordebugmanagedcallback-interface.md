---
title: "ICorDebugManagedCallback – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback
helpviewer_keywords: ICorDebugManagedCallback interface [.NET Framework debugging]
ms.assetid: b47f1d61-c7dc-4196-b926-0b08c94f7041
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1b72a2814ee2276363152052c7bf734104d4f395
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallback-interface"></a>ICorDebugManagedCallback – rozhraní
Poskytuje metody pro zpětná volání procesu ladicího programu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[BREAK – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-break-method.md)|Upozorní ladicího programu při <xref:System.Reflection.Emit.OpCodes.Break> provedení instrukcí v datovém proudu kódu.|  
|[Breakpoint – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-breakpoint-method.md)|Ladicí program upozorní, když je došlo zarážky.|  
|[Breakpointseterror – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-breakpointseterror-method.md)|Upozorní ladicího programu, modul CLR (CLR) se nepodařilo přesně vazby zarážku nastavený před funkci v běhu (JIT) zkompilovat.|  
|[Controlctrap – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-controlctrap-method.md)|Do pasti CTRL + C v procesu laděné upozorní ladicího programu.|  
|[Createappdomain – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createappdomain-method.md)|Upozorní ladicího programu vytvořený domény aplikace.|  
|[CreateProcess – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)|Ladicí program upozorní, když proces byl připojen nebo při prvním spuštění.|  
|[CreateThread – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md)|Upozorní ladicí program, že vlákno byla spuštěna spravovaného kódu.|  
|[Debuggererror – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-debuggererror-method.md)|Upozorní ladicí program, že došlo k chybě při pokusu o zpracování události z modulu CLR.|  
|[Editandcontinueremap – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md)|Zastaralé Upozorní ladicí program, že přemapování událostí byl odeslán do prostředí IDE.|  
|[Evalcomplete – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalcomplete-method.md)|Upozorní ladicí program dokončí zkušební verzi.|  
|[Evalexception – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalexception-method.md)|Upozorní ladicí program, že zkušební verzi byla ukončena s k neošetřené výjimce.|  
|[Exception – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md)|Upozorní ladicí program, že byla vyvolána výjimka ze spravovaného kódu.|  
|[Exitappdomain – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md)|Upozorní ladicí program, aby byl ukončen domény aplikace.|  
|[Exitprocess – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md)|Upozorní ladicího programu, proces byl ukončen.|  
|[ExitThread – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md)|Upozorní ladicí program, aby byl ukončen vláken, která byla spuštěna spravovaného kódu.|  
|[Loadassembly – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)|Sestavení CLR byl úspěšně načíst upozorní ladicího programu.|  
|[Loadclass – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)|Načtení třídy upozorní ladicího programu.|  
|[LoadModule – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)|Upozorní ladicí program, že modul CLR byl úspěšně načten.|  
|[LogMessage – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md)|Ladicí program upozorní, že vlákno CLR spravované volal metodu <xref:System.Diagnostics.EventLog> třída do protokolu událostí.|  
|[Logswitch – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logswitch-method.md)|Ladicí program upozorní, že vlákno CLR spravované volal metodu <xref:System.Diagnostics.Switch> třída k vytvoření, úpravě nebo odstranění přepínač ladění nebo trasování.|  
|[NameChange – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-namechange-method.md)|Upozorní ladicí program, že došlo ke změně názvu domény aplikace nebo přístup z více vláken.|  
|[Stepcomplete – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)|Aby byla dokončena krok upozorní ladicího programu.|  
|[Unloadassembly – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadassembly-method.md)|Sestavení CLR byl odpojen upozorní ladicího programu.|  
|[Unloadclass – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)|Odpojení třídy upozorní ladicího programu.|  
|[Unloadmodule – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadmodule-method.md)|Modul CLR (DLL) byl odpojen upozorní ladicího programu.|  
|[Updatemodulesymbols – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md)|Upozorní ladicí program, že došlo ke změně symboly pro modul CLR.|  
  
## <a name="remarks"></a>Poznámky  
 Všechny zpětná volání jsou serializovat, názvem ve stejném vlákně, v a volána s procesu synchronizovaného stavu.  
  
 Každá implementace zpětného volání musí volat [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) Chcete-li pokračovat v provádění. Pokud `ICorDebugController::Continue` není volána před zpětné volání vrátí, proces zůstane zastaven a zpětná volání žádné další události dojde až `ICorDebugController::Continue` je volána.  
  
 Ladicí program musí implementovat [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) pokud ho je ladění aplikací rozhraní .NET Framework verze 2.0. Instance `ICorDebugManagedCallback` nebo `ICorDebugManagedCallback2` se předá jako objekt zpětného volání, který má [icordebug::setmanagedhandler –](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).  
  
> [!NOTE]
>  Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebug – rozhraní rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [ICorDebugManagedCallback2 – rozhraní rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [Ladění v rozhraní](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)