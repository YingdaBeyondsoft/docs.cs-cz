---
title: MDAInfo – struktura
ms.date: 03/30/2017
api_name:
- MDAInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- MDAInfo
helpviewer_keywords:
- MDAInfo structure [.NET Framework hosting]
ms.assetid: fb8c14f7-d461-43d1-8b47-adb6723b9b93
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5164e85ecc97de99dcc493c2ba5efa8fc3468471
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443177"
---
# <a name="mdainfo-structure"></a>MDAInfo – struktura
Poskytuje podrobnosti o `Event_MDAFired` událost, která aktivuje vytvoření Pomocník spravovaného ladění (MDA).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`lpMDACaption`|Název aktuální (mda). Nadpis popisuje typ selhání, který aktivoval `Event_MDAFired` událostí.|  
|`lpMDAMessage`|Výstup zpráva, která poskytuje aktuální (mda).|  
  
## <a name="remarks"></a>Poznámky  
 Pomocníci spravovaného ladění (mda) jsou ladění pomůcek, které spolupracují se modul CLR (CLR) k provádění úloh, jako je identifikace neplatný podmínky v modulu runtime provádění nebo vypsání Další informace o stavu modul. Mda generování zpráv XML o událostech, které jsou jinak obtížné depeše. Jsou užitečné zejména pro ladění přechodů mezi spravovanými a nespravovanými kódu.  
  
 Modul runtime provede následující kroky, když je aktivována událost, která aktivuje vytvoření (mda):  
  
-   Pokud hostitel není registrován [iactiononclrevent –](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) instance voláním [iclroneventmanager::registeractiononevent –](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) upozornit `Event_MDAFired` události modulu runtime pokračuje v jeho výchozí chování bez hostitele.  
  
-   Pokud hostitel zaregistrovala obslužnou rutinu pro tuto událost, modul runtime zkontroluje, zda je pro proces připojen ladicí program. Pokud se jedná, modul runtime dělí do ladicího programu. Když ladicí program dál, zavolá do hostitele. Pokud je připojen ladicí žádné program, modul runtime zavolá `IActionOnCLREvent::OnEvent` a předá ukazatel na `MDAInfo` instance jako `data` parametr.  
  
 Hostiteli můžete k aktivaci mda a chcete být upozorněni, když se aktivuje (mda). To dává příležitost přepsat výchozí chování a abort spravované vlákno, které vyvolá událost, aby zabránil jeho poškozování stavu procesu hostitele. Další informace o používání mda najdete v tématu [diagnostikování chyb pomocí asistentů spravovaného ladění](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.idl  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Struktury pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
