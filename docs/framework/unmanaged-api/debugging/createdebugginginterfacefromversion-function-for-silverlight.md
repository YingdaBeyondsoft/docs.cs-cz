---
title: CreateDebuggingInterfaceFromVersion – funkce pro technologii Silverlight
ms.date: 03/30/2017
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 35c7a18f-133a-4584-bd25-bb338568b0c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 53571268391011cc1dc0ff112d484e1fa140057f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407711"
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a>CreateDebuggingInterfaceFromVersion – funkce pro technologii Silverlight
Přijímá běžné language runtime (CLR) verze řetězec, který je vrácena z [createversionstringfrommodule – funkce](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)a vrátí odpovídající rozhraní ladicího programu (obvykle [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szDebuggeeVersion`  
 [v] Řetězec verze modulu CLR cíl ladění, která je vrácena [createversionstringfrommodule – funkce](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md).  
  
 `ppCordb`  
 [out] Ukazatel na ukazatel na objekt COM (`IUnknown`). Tento objekt přetypovat [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) objektu před vrácením.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 `ppCordb` odkazuje na platný objekt, který implementuje [ICorDebug rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) rozhraní.  
  
 E_INVALIDARG  
 Buď `szDebuggeeVersion` nebo `ppCordb` má hodnotu null.  
  
 CORDBG_E_DEBUG_COMPONENT_MISSING  
 Součásti, které jsou nezbytné pro ladění CLR nelze najít. To znamená, že mscordbi.dll nebo mscordaccore.dll nebyl nalezen ve stejném adresáři jako cíl CoreCLR.dll.  
  
 CORDBG_E_INCOMPATIBLE_PROTOCOL  
 Mscordbi.dll nebo mscordaccore.dll není stejnou verzi jako cíl CoreCLR.dll.  
  
 E_FAIL (nebo ostatní návratové kódy E_)  
 Nelze vrátit [ICorDebug rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md).  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní, která je vrácena zajišťuje funkce pro připojení k CLR v Cílový proces a ladění spravovaného kódu, který je spuštěn modul CLR.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** dbgshim.h  
  
 **Knihovna:** dbgshim.dll  
  
 **Verze rozhraní .NET framework:** 3.5 SP1
