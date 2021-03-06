---
title: '&lt;Kritéria hledání&gt;'
ms.date: 03/30/2017
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
ms.openlocfilehash: fc9cd3b87d0f47ae0f16b5c5bfcaa4a1167bae9f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748643"
---
# <a name="ltfindcriteriagt"></a>&lt;Kritéria hledání&gt;
Konfigurace element, který poskytuje sadu kritérií používané klientskou aplikaci pro vyhledávání pro službu zjišťování. Kritéria mohou být seskupeny do kritéria vyhledávání (určení služby, kterou hledáte) a najděte ukončení kritéria (jak dlouho by měl poslední hledání).  
  
 \<system.ServiceModel>  
\<standardEndpoints >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan" maxResults="Integer" scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String" namespace="String" />
            <contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI" />
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      </standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|doba trvání|Hodnota časového rozpětí, která určuje maximální dobu čekání na odpovědi od služby v síti. Výchozí doba je 20 sekund...|  
|shluku|Celé číslo, které určuje maximální počet odpovědí čekat, služby v síti nebo Internetu. Pokud jsou odpovědi maximální obdrženy předtím, než hodnota zadaná v `duration` atribut uplynul, skončení operace hledání.|  
|scopeMatchBy|Identifikátor URI, který zadejte odpovídající algoritmus použitý při odpovídající obory ve zprávě test s u koncového bodu.<br /><br /> Existují pravidla pět odpovídající oboru podporované. Pokud nezadáte oboru odpovídající pravidlo, `ScopeMatchByPrefix` se používá. Další informace o tomto naleznete v tématu <xref:System.ServiceModel.Discovery.FindCriteria>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<contractTypeNames >](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|Kolekci elementů konfigurace, které obsahují názvy typů kontraktu služby pracovního postupu...|  
|\<Rozšíření > z \<kritéria hledání >|Kolekce objektů elementu XML, které poskytují rozšíření.|  
|[\<obory >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|Kolekce objektů, které obsahují absolutní identifikátory URI, které se používají během operace hledání pro vyhledání konkrétní služby nebo služby.<br /><br /> Pokud je nalezen konkrétní službu, byl proveden úspěšně shody mezi URI služby a identifikátor URI oboru, někdy pomocí pravidel rozsahu, které zpracovávají komplikace odpovídajících.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Obsahuje nastavení vyžadovaná aplikace k účasti v procesu zjišťování služby jako klient.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
