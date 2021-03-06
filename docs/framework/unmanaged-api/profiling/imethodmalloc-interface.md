---
title: IMethodMalloc – rozhraní
ms.date: 03/30/2017
api_name:
- IMethodMalloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc
helpviewer_keywords:
- IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8c8ab5dc-557c-473a-82f2-6e403eca7dac
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b11cf0fadc9142ee291115cf9f0d84e6429834fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455114"
---
# <a name="imethodmalloc-interface"></a>IMethodMalloc – rozhraní
Poskytuje metodu pro přidělení paměti pro nový tělo funkce (MSIL intermediate language) společnosti Microsoft.  
  
> [!NOTE]
>  `IMethodMalloc` Rozhraní je přidělení jednoduché paměti. Umožní vám přidělit paměť, ale nechcete ho volné.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Alloc – metoda](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|Pokusí se přidělit zadanou velikost paměti pro nový tělo funkce MSIL.|  
  
## <a name="remarks"></a>Poznámky  
 Každý allocator je modulů a zajistí, že tělo funkce bude v kladné posun od základní modulu. Paměť nad základní modulu může být drahocenný, takže přidělujícího modulu se má použít k přidělení paměti pouze pro tělo funkce.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
