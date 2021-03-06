---
title: Rozhraní ICorDebugILFrame4
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame4
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1e739183-3e05-49e5-846f-4075256e41de
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b57289e1d96a56bc4ab5cb8c07cbcac4b1d98b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416576"
---
# <a name="icordebugilframe4-interface"></a>Rozhraní ICorDebugILFrame4
[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]  
  
 Poskytuje metody, které vám umožní přístup k místní proměnné a kódu v zásobníku kódu převodní jazyk (IL). Parametr určuje, zda ladicí program má přístup k proměnné a kódu přidaném v ReJIT instrumentace profileru.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumerateLocalVariablesEx – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)|Vrátí seznam hodnot lokální proměnné, které jsou dostupné v aktuálním snímku.|  
|[GetCodeEx – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)|Vrátí kód, který je spuštěn tento rámec zásobníku.|  
|[GetLocalVariableEx – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)|Vrátí hodnotu místní proměnné v rámci IL.|  
  
## <a name="remarks"></a>Poznámky  
 Tyto metody nabízejí funkce k těm, které poskytuje [enumeratelocalvariables –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md), [getcode –](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md), a [getlocalvariable –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) metody. Každá metoda zahrnuje `flags` parametr, který určuje, zda jsou viditelné další místní proměnné nebo kód definované profileru ReJIT požadavku.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
