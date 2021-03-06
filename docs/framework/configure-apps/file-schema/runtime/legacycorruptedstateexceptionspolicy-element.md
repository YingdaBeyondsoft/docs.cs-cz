---
title: '&lt;legacycorruptedstateexceptionspolicy –&gt; – Element'
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6228aaf4c7da70337d9d1a99adcb78f71a0039b2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744613"
---
# <a name="ltlegacycorruptedstateexceptionspolicygt-element"></a>&lt;legacycorruptedstateexceptionspolicy –&gt; – Element
Určuje, zda modul common language runtime umožňuje spravovaného kódu k zachycení narušení přístupu a ostatní výjimky v poškozeném stavu.  
  
 \<Konfigurace >  
\<modul runtime >  
\<legacycorruptedstateexceptionspolicy – >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, že aplikace zachytí poškozování stavu výjimky selhání například porušení přístupu.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Aplikace nebude catch poškozování stavu výjimky selhání například porušení přístupu. Toto nastavení je výchozí.|  
|`true`|Aplikace zachytí poškozování stavu výjimky selhání například porušení přístupu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 V rozhraní .NET Framework verze 3.5 a starší modul common language runtime povoleno spravovaného kódu k zachycení výjimky, které byly vyvolány státy poškozená procesu. Narušení přístupu je příklad tohoto typu výjimky.  
  
 Počínaje [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]spravovaný kód už zachytí tyto typy výjimek v `catch` bloky. Můžete však přepsat tuto změnu a udržovat ošetření výjimky v poškozeném stavu dvěma způsoby:  
  
-   Nastavte `<legacyCorruptedStateExceptionsPolicy>` elementu `enabled` atribut `true`. Toto nastavení je použité processwide a ovlivňuje všechny metody.  
  
 -nebo-  
  
-   Použít <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> atribut metodu, která obsahuje výjimky `catch` bloku.  
  
 Tento element konfigurace je k dispozici pouze v [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] a novější.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak určit, že aplikace by měla vrátit k chování před [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]a catch všechny poskozeny stavu výjimky selhání.  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>  
 [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
