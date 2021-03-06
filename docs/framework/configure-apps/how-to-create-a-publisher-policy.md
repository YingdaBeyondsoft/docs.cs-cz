---
title: 'Postupy: Vytváření zásad vydavatele'
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 91971e4d41c3a54fa72ae73a3655dab650019676
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758123"
---
# <a name="how-to-create-a-publisher-policy"></a>Postupy: Vytváření zásad vydavatele
Dodavatelé sestavení může stavu, že aplikace by měly používat na novější verzi sestavení zahrnutím souboru zásad vydavatele s upgradovaná sestavením. Soubor zásad vydavatele určuje sestavení – přesměrování a základní nastavení kódu a používá stejný formát jako konfiguračního souboru aplikace. Soubor zásad vydavatele je zkompilován do sestavení a umístit do globální mezipaměti sestavení.  
  
 Součástí procesu vytváření zásad vydavatele existují tři kroky:  
  
1.  Vytvořte soubor zásad vydavatele.  
  
2.  Vytvořte sestavení zásady vydavatele.  
  
3.  Sestavení zásady vydavatele přidáte do globální mezipaměti sestavení.  
  
 Schéma pro vydavatele zásady je popsáno v [přesměrování verzí sestavení](../../../docs/framework/configure-apps/redirect-assembly-versions.md). Následující příklad ukazuje vydavatel soubor zásad, který přesměruje jednu verzi `myAssembly` do jiného.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
       <dependentAssembly>  
         <assemblyIdentity name="myAssembly"  
                           publicKeyToken="32ab4ba45e0a69a1"  
                           culture="en-us" />  
         <!-- Redirecting to version 2.0.0.0 of the assembly. -->  
         <bindingRedirect oldVersion="1.0.0.0"  
                          newVersion="2.0.0.0"/>  
       </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 Další informace o zadání základu kódu najdete v tématu [určení umístění sestavení](../../../docs/framework/configure-apps/specify-assembly-location.md).  
  
## <a name="creating-the-publisher-policy-assembly"></a>Vytváření sestavení zásady vydavatele  
 Použití [Linker sestavení (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) vytvořit sestavení zásady vydavatele.  
  
#### <a name="to-create-a-publisher-policy-assembly"></a>Chcete-li vytvořit sestavení zásady vydavatele  
  
1.  Na příkazovém řádku zadejte následující příkaz:  
  
     **Al/Link:** *publisherPolicyFile* **/out:** *publisherPolicyAssemblyFile* **/keyfile:**  *keyPairFile* **/Platform:** *processorArchitecture*  
  
     V tomto příkazu:  
  
    -   *PublisherPolicyFile* argument je název souboru zásad vydavatele.  
  
    -   *PublisherPolicyAssemblyFile* argument je název sestavení zásady vydavatele, který je výsledkem tohoto příkazu. Název souboru sestavení musí mít formát:  
  
         **zásady.** *majorNumber* **.** *minorNumber* **.** *mainAssemblyName* **.dll**  
  
    -   *KeyPairFile* argument je název souboru, který obsahuje pár klíčů. Musíte se odhlásit sestavení a sestavení zásady vydavatele pomocí stejného páru klíčů.  
  
    -   *ProcessorArchitecture* argument identifikuje platformou cílem sestavení specifické pro procesor.  
  
        > [!NOTE]
        >  Možnost cíle architekturu konkrétní procesoru je v rozhraní .NET Framework verze 2.0 nová.  
  
     Následující příkaz vytvoří volána sestavení zásady vydavatele `policy.1.0.myAssembly` ze souboru zásad vydavatele názvem `pub.config`, přiřadí silné název sestavení pomocí páru klíčů jako `sgKey.snk` souboru a určuje, že sestavení cílí x86 Architektura procesoru.  
  
    ```  
    al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86  
    ```  
  
     Sestavení zásady vydavatele musí odpovídat architektuře procesoru sestavení, které se vztahuje na. Proto pokud má vaše sestavení <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> hodnotu <xref:System.Reflection.ProcessorArchitecture.MSIL>, sestavení zásady vydavatele pro toto sestavení musí být vytvořeny s `/platform:anycpu`. Je nutné zadat samostatné sestavení zásady vydavatele pro každé sestavení specifické pro procesor.  
  
     Důsledkem tohoto pravidla je, aby bylo možné změnit na architektuře procesoru pro sestavení, musíte změnit komponentu hlavních nebo vedlejších číslo verze, takže můžete zadat nové sestavení zásady vydavatele s správnou architekturu procesoru. Původní sestavení zásady vydavatele nemůže obsloužit váš sestavení po vaší sestavení má jinou architekturu procesoru.  
  
     Jiné důsledkem je, že verze 2.0 linkeru nelze použít k vytvoření sestavení zásady vydavatele pro sestavení zkompilovaného pomocí starší verze rozhraní .NET Framework, protože vždy určuje architekturu procesoru.  
  
## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Přidání sestavení zásady vydavatele do globální mezipaměti sestavení  
 Použití [nástroj globální mezipaměti sestavení (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) sestavení zásady vydavatele přidat do globální mezipaměti sestavení.  
  
#### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Sestavení zásady vydavatele přidat do globální mezipaměti sestavení  
  
1.  Na příkazovém řádku zadejte následující příkaz:  
  
     **Gacutil /i***publisherPolicyAssemblyFile*   
  
     Následující příkaz přidá `policy.1.0.myAssembly.dll` do globální mezipaměti sestavení.  
  
    ```  
    gacutil /i policy.1.0.myAssembly.dll  
    ```  
  
    > [!IMPORTANT]
    >  Sestavení zásady vydavatele nelze přidat do globální mezipaměti sestavení, pokud se původní soubor zásad vydavatele nachází ve stejném adresáři jako sestavení.  
  
## <a name="see-also"></a>Viz také  
 [Programování se sestaveními](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Konfigurace aplikací](../../../docs/framework/configure-apps/index.md)  
 [Konfigurace aplikací rozhraní .NET Framework](http://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)  
 [Schéma nastavení běhového prostředí](../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma konfiguračního souboru](../../../docs/framework/configure-apps/file-schema/index.md)  
 [Přesměrování verzí sestavení](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
