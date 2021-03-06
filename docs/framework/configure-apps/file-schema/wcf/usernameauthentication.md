---
title: '&lt;UserNameAuthentication&gt;'
ms.date: 03/30/2017
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
ms.openlocfilehash: d81bf3441f4999683b9dc9ab956fff517c20e80e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754860"
---
# <a name="ltusernameauthenticationgt"></a>&lt;UserNameAuthentication&gt;
Určuje pověření služby na základě uživatelského jména a hesla.  
  
 \<system.ServiceModel>  
\<chování >  
\<serviceBehaviors >  
\<chování >  
\<– serviceCredentials >  
\<userNameAuthentication >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<userNameAuthentication  
   cacheLogonTokenLifetime="TimeSpan"  
   cacheLogonTokens="Boolean"   
   customUserNamePasswordValidatorType="String"  
   includeWindowsGroups="Boolean"   
   maxCacheLogonTokens="Integer"  
   membershipProviderName="String"  
   userNamePasswordValidationMode="Windows/MembershipProvider/Custom" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`cacheLogonTokenLifetime`|A <xref:System.TimeSpan> , určuje maximální délku doby token se uloží do mezipaměti. Výchozí hodnota je 00:15:00.|  
|`cacheLogonTokens`|Logická hodnota, která určuje, zda jsou tokeny přihlášení do mezipaměti. Výchozí hodnota je `false`.|  
|`customUserNamePasswordValidatorType`|Řetězec, který určuje typ validátor hesel vlastní uživatelské jméno, který se má použít. Výchozí hodnota je prázdný řetězec.|  
|`includeWindowsGroups`|Logická hodnota, která určuje, zda skupiny systému Windows jsou zahrnuty v kontextu zabezpečení. Výchozí hodnota je `true`.<br /><br /> Nastavení tohoto atributu na `true` má dopad na výkon, jako je výsledkem rozšíření skupiny úplné. Tuto vlastnost nastavit na `false` Pokud není potřeba vytvořit seznam skupin uživatel patří do.|  
|`maxCacheLogonTokens`|Celé číslo, které určuje maximální počet tokeny přihlášení do mezipaměti. Tato hodnota by měla být větší než nula. Výchozí hodnota je 128.|  
|`membershipProviderName`|Když `clientCredentialType` atribut vazby je nastaven na `username`, uživatelské jméno je namapována na účty v systému Windows. Můžete přepsat toto chování pomocí tento atribut, který je řetězec, který obsahuje název <xref:System.Web.Security.MembershipProvider> hodnotu, která poskytuje mechanismus ověřování příslušné heslo.|  
|`userNamePasswordValidationMode`|Určuje způsob, které uživatelské jméno je ověřit heslo. Platné hodnoty jsou:<br /><br /> -Windows<br />-MembershipProvider<br />-Vlastní<br /><br /> Výchozí hodnota je Windows. Tento atribut je typu <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<– serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Určí pověření, které mají být použity v ověřování služby, a ověření přihlašovacích údajů klienta související nastavení.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud žádná vazby používá služba je nakonfigurována pro ověřování založené na jméno/heslo uživatele, se ignorují atributy pro tento element. Mezi ně patří `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, a `userNamePasswordValidationMode`.  
  
 Pokud žádná z vazby používané služby je nakonfigurovaný na použití ověřování systému Windows pro uživatelské jméno a heslo, nastavení související s ukládání do mezipaměti tokenů přihlášení se ignorují. Patří mezi ně `cacheLogonTokenLifetime`, `cacheLogonTokens`, a `maxCacheLogonTokens`.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.UserNameServiceElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>
