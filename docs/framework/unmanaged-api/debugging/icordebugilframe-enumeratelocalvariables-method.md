---
title: ICorDebugILFrame::EnumerateLocalVariables – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.EnumerateLocalVariables
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateLocalVariables
helpviewer_keywords:
- EnumerateLocalVariables method [.NET Framework debugging]
- ICorDebugILFrame::EnumerateLocalVariables method [.NET Framework debugging]
ms.assetid: 1a67fa1b-2419-4cd0-aad4-6f46a0719b4b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6fd7694901534ad6897bbf78239081af6314e4bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415465"
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a>ICorDebugILFrame::EnumerateLocalVariables – metoda
Získá enumerátor pro místní proměnné do tohoto rámce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumerateLocalVariables(   
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppValueEnum`  
 [out] Ukazatel na adresu ICorDebugValueEnum objekt, který je enumerátor pro místní proměnné do tohoto rámce.  
  
## <a name="remarks"></a>Poznámky  
 `EnumerateLocalVariables` Získá enumerátor, který může být uveden lokální proměnné, které jsou k dispozici v rámci volání, která je reprezentována tento objekt ICorDebugILFrame. V seznamu nemusí zahrnovat všechny lokální proměnné ve funkci spuštěné, protože některé z nich nemusí být aktivní.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
