---
title: Funkce GetDemultiplexedStub (referenční dokumentace nespravovaného rozhraní API)
description: Funkce GetDemultiplexedStub vytvoří předávání podřízený objekt klienta jako pomůcku při přijímání asynchronní volání od Správa systému Windows.
ms.date: 11/06/2017
api_name:
- GetDemultiplexedStub
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetDemultiplexedStub
helpviewer_keywords:
- GetDemultiplexedStub function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b195d3a512c537ca409bd2039add9e69abaf4df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33456359"
---
# <a name="getdemultiplexedstub-function"></a>GetDemultiplexedStub – funkce
Vytvoří předávání podřízený objekt klienta jako pomůcku při přijímání asynchronní volání od Správa systému Windows.
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetDemultiplexedStub (
   [in] IUnknown*    pObject, 
   [in] boolean      isLocal, 
   [out] IUnknown**  ppObject
); 
```  

## <a name="parameters"></a>Parametry

`pObject`  
[v] Ukazatel na implementaci klienta v rámci procesu [IWbemObjectSink](https://msdn.microsoft.com/library/aa391787(v=vs.85).aspx).

`isLocal`  
[v] Příznak, který určuje, zda je místní události (`true`), jinak hodnota `false`.

`ppObject`  
[out] Podřízený objekt předávání klienta jako pomůcku při přijímání asynchronní volání od Správa systému Windows.

## <a name="return-value"></a>Návratová hodnota

Pokud funkci úspěšné, je vrácenou hodnotu `S_OK` (0).

V případě selhání funkce návratovou hodnotu je kód chyby nulová. Chcete-li získat rozšířené informace o chybě, zavolejte [GetErrorInfo –](geterrorinfo.md) funkce.
    
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také  
[Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
