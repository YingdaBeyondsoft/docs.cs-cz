---
title: x:Property – direktiva
ms.date: 03/30/2017
ms.assetid: 618555a8-c893-455c-810f-ac54cd24ef10
ms.openlocfilehash: 0d554d8ba4d69b4c2d4cc01f3965ade7e508bb0e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563692"
---
# <a name="xproperty-directive"></a>x:Property – direktiva
Deklaruje vlastnost XAML v kódu.  
  
## <a name="xaml-object-element-usage"></a>Použití elementu objektu XAML  
  
```  
<object x:Class="className">  
  <x:Members>  
    <x:Property Name="propertyName" Type="propertyType/>  
    additionalProperties  
  </x:Members>  
</object>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`className`|Název základní třídy nebo částečné třídy pro produkční XAML.|  
|`propertyName`|Název člena vlastnosti definovaný.|  
|`propertyType`|Název typu (nebo jiné formy řetězec konkrétní rozhraní) určující typ této vlastnosti.|  
  
## <a name="remarks"></a>Poznámky  
 V implementaci rozhraní .NET Framework XAML Services. `x:Property` nemá přímé typ zálohování, ale podporuje <xref:System.Windows.Markup.PropertyDefinition> třídy. V datový proud uzlu XAML `x:Property` element je reprezentován jako člen s názvem `Property`, z oboru názvů jazyka XAML jazyka XAML. Člen `Property` uložení atributů deklarovaná značek.  
  
 Význam `Name` a `Type` nejsou přiřazeny na úrovni rozhraní .NET Framework XAML Services. Jsou uložené v počáteční datový proud uzlu XAML jako řetězcové hodnoty budou interpretovat později v části pravidla, která může být způsobené konkrétní rozhraní. Význam může zarovnat na XAML název a typ jazyka XAML, což znamená, nebo může být pouze platné ve základní typ systému, v závislosti na implementaci.  
  
 Pro podporu praktické využití `x:Members` jako prostředek k zadávání definice člen v kódu, musí být přidružen třídu, která je možné upravit členy. Je určený model, který `x:Members` existuje jako člena typu, který určuje `x:Class`. Tento mechanismus pro přidružení typy a členy nebo pro vytvoření definice dynamického člena však není podporován na úrovni rozhraní .NET Framework XAML Services. To je zleva jednotlivé rozhraní, které mají modelů aplikace, které podporují definice člena z XAML. Obvykle MSBUILD sestavení akce, které kompilace kódu XAML a buď ji integrovat s nástrojem kódu nebo produktu čistě z XAML sestavení jsou potřeba k podpoře této funkce.  
  
## <a name="xproperty-for-windows-workflow-foundation"></a>x: Property pro Windows Workflow Foundation  
 Pro Windows Workflow Foundation `x:Property` definuje členy vlastní aktivita tvoří zcela v jazyce XAML, nebo XAML – definované dynamické členy pro Návrhář aktivity s kódem v pozadí. `x:Class` musí být zadaná také v kořenovém elementu provozních XAML. To není požadavek na úrovni rozhraní .NET Framework XAML Services, ale při načtení provozní XAML akcemi MSBUILD sestavení, které podporují vlastní aktivity a Windows Workflow Foundation XAML obecně se změní na požadavek. Windows Workflow Foundation nepoužívá jako jeho určená hodnota pro název typu čistý XAML `x:Property` `Type` atribut a místo toho používá názvů, který není dokumentováno sem. Další informace najdete v tématu [dynamické vytvoření aktivity](http://msdn.microsoft.com/library/dd807392.aspx).
