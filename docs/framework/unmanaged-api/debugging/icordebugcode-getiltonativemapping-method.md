---
title: ICorDebugCode::GetILToNativeMapping – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetILToNativeMapping
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetILToNativeMapping
helpviewer_keywords:
- GetILToNativeMapping method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetILToNativeMapping method [.NET Framework debugging]
ms.assetid: a8ecd8c8-9627-4356-9c6f-bd05e24637c0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13ec60999db88b9d7191a3866fcebe8098b4edee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411383"
---
# <a name="icordebugcodegetiltonativemapping-method"></a>ICorDebugCode::GetILToNativeMapping – metoda
Získá pole instancí "cor_debug_il_to_native_map –", která představuje mapování nativní posuny od společnosti Microsoft posune (MSIL intermediate language).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetILToNativeMapping (  
    [in]  ULONG32    cMap,  
    [out] ULONG32    *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cMap`  
 [v] Velikost `map` pole.  
  
 `pcMap`  
 [out] Ukazatel na skutečný počet elementy, vrátí se v `map` pole.  
  
 `map`  
 [out] Pole `COR_DEBUG_IL_TO_NATIVE_MAP` stuctures, z nichž každý představuje mapování z MSIL posun na nativní posun.  
  
 Není žádný řazení do pole elementů vrátila.  
  
## <a name="remarks"></a>Poznámky  
 `GetILToNativeMapping` Metoda vrací výsledky, smysl pouze v případě, že tato instance "ICorDebugCode" představuje nativního kódu, který byl právě za běhu (JIT) zkompilovat z MSIL kódu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugCode – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)
