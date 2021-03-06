---
title: 'Postupy: Vyhledání sestavení pomocí mechanismu DEVPATH'
ms.date: 03/30/2017
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 918acf069c63d3aa8187f0f04e1f6c55ec961458
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755458"
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a>Postupy: Vyhledání sestavení pomocí mechanismu DEVPATH
Vývojáři mohou chtít Ujistěte se, že se sdílené sestavení, na které se sestavení s více aplikacemi funguje správně. Místo průběžně uvedení sestavení v globální mezipaměti sestavení během cyklu vývoje, můžete vytvořit vývojář mechanismu DEVPATH proměnné prostředí, která odkazuje na výstupního adresáře sestavení pro sestavení.  
  
 Předpokládejme například, že vytváříte sdílené sestavení nazvané MySharedAssembly a výstupní adresář je C:\MySharedAssembly\Debug. Můžete vložit C:\MySharedAssembly\Debug mechanismu DEVPATH proměnné. Pak musíte zadat [ \<developmentmode – >](../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md) element v konfiguračním souboru počítače. Tento element informuje modul common language runtime vyhledávat sestavení pomocí mechanismu DEVPATH.  
  
 Sdílené sestavení musí být zjistitelný modulem runtime.  K určení privátní adresář pro použití odkazů na sestavení řešení [ \<codeBase > Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) nebo [ \<zjišťování > Element](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) v konfiguračním souboru, jak je popsáno v [Určení umístění sestavení](../../../docs/framework/configure-apps/specify-assembly-location.md).  Můžete taky umístit sestavení v podadresáři adresář aplikace. Další informace najdete v tématu [jak modul Runtime vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
> [!NOTE]
>  Toto je pokročilá funkce, určena pouze pro vývoj.  
  
 Následující příklad ukazuje, jak způsobí modulu runtime pro vyhledání sestavení v zadaném proměnnou prostředí DEVPATH adresáře.  
  
## <a name="example"></a>Příklad  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 Toto nastavení výchozí nastavení na hodnotu false.  
  
> [!NOTE]
>  Toto nastavení používejte pouze v době vývoj. Modul runtime nekontroluje verze na sestavení se silným názvem v mechanismu DEVPATH nalezen. Jednoduše použije první sestavení, které najde.  
  
## <a name="see-also"></a>Viz také  
 [Konfigurace aplikací rozhraní .NET Framework](http://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
