---
title: 'Postupy: Registrace primárních sestavení spolupráce'
ms.date: 03/30/2017
helpviewer_keywords:
- registering primary interop assemblies
- primary interop assemblies, registering
ms.assetid: 4b2fcf8a-429d-43ce-8334-e026040be8bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f54d77be130d57c39319e81d58ad5af7815e548
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33390858"
---
# <a name="how-to-register-primary-interop-assemblies"></a>Postupy: Registrace primárních sestavení spolupráce
Třídy mohou být zařazena pouze pomocí zprostředkovatele komunikace s objekty COM a jsou vždycky zařazené jako rozhraní. V některých případech rozhraní sloužící k zařazování třídy se nazývá rozhraní třídy. Informace o přepsání třídy rozhraní s rozhraním zvoleného najdete v tématu [obálka volatelná aplikacemi COM](../../../docs/framework/interop/com-callable-wrapper.md).  
  
 Přestože všechny vývojáře, který chce používat typy modelu COM z aplikace rozhraní .NET Framework můžete vygenerovat sestavení spolupráce, to proto vytvoří problém. Pokaždé, když vývojář importuje a podepisuje knihovny typů modelu COM, která vývojáře vytvoří sadu jedinečné typy, které nejsou kompatibilní s těmi, importovat a podepsaný jiné developer. Řešení tohoto problému nekompatibilita typ je pro každý vývojář získat dodavatele a podepsaný primární spolupracující sestavení.  
  
 Pokud máte v plánu vystavit typy modelu COM třetích stran k ostatním aplikacím, vždy používejte primární spolupracující sestavení od stejného vydavatele jako knihovny typů, který definuje. Kromě zajištění kompatibility zaručenou typu, jsou často přizpůsobit primární spolupracující sestavení dodavatel zlepšení interakce.  
  
 I v případě, že neplánujete vystavit typy modelu COM třetích stran, můžete pomocí primární spolupracující sestavení usnadňují úlohy vzájemné spolupráci se službou COM – součásti. Tato strategie však poskytuje žádná izolace z změny, které typy definované v primární spolupracující sestavení může provést dodavatele. Pokud vaše aplikace vyžaduje tyto izolace, generovat vlastní sestavení vzájemné spolupráce místo použití primární spolupracující sestavení.  
  
 Je nutné zaregistrovat všechny získal primární spolupracující sestavení ve svém vývojovém počítači předtím, než můžete odkazovat pomocí [!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)]. Visual Studio vyhledává a používá primární spolupracující sestavení poprvé odkazovat na typ z knihovny typů COM. Pokud Visual Studio nemůže najít primární spolupracující sestavení přidružené ke knihovně typů, vás vyzve, abyste ho získat nebo nabízí místo vytvoření spolupráce sestavení. Podobně [Importér knihovny typů (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) také používá registru k vyhledání primární spolupracující sestavení.  
  
 Ačkoli to není potřeba registrace primárních sestavení spolupráce, pokud máte v úmyslu použít Visual Studio, poskytne mu nástroj registrace dvě výhody:  
  
-   Registrovaný primární spolupracující sestavení je přehledně označen v klíči registru původní knihovny typů. Registrace je nejlepší způsob vyhledejte primární spolupracující sestavení v počítači.  
  
-   Omylem generování a použití nového sestavení vzájemné spolupráce, pokud někdy v budoucnu, pomocí sady Visual Studio odkazovat na typ, pro které máte registrace sestavení primární spolupráce se můžete vyhnout.  
  
 Použití [nástroj pro registraci sestavení (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) registrace primárních sestavení vzájemné spolupráce.  
  
### <a name="to-register-a-primary-interop-assembly"></a>Registrace primárních sestavení vzájemné spolupráce  
  
1.  V příkazovém řádku zadejte příkaz:  
  
     **modul RegAsm** *assemblyname*  
  
     V tomto příkazu *assemblyname* je název souboru sestavení, které je registrované. RegAsm.exe přidá položku pro primární spolupracující sestavení v klíči registru jako původní knihovny typů.  
  
## <a name="example"></a>Příklad  
 Zaregistruje v následujícím příkladu `CompanyA.UtilLib.dll` primární spolupracující sestavení.  
  
```console  
regasm CompanyA.UtilLib.dll  
```  
  
## <a name="see-also"></a>Viz také  
 [Programování s primární spolupráce – sestavení](https://msdn.microsoft.com/library/306fa1d6-0703-4004-9e93-d0a57f1be81e(v=vs.100))  
 [Vyhledání primární spolupráce – sestavení](https://msdn.microsoft.com/library/d6768e4b-cd80-414d-a4f8-05d979eb393b(v=vs.100))  
 [Redistribuce primární spolupráce – sestavení](https://msdn.microsoft.com/library/e76384f0-d631-474c-bdbd-13884cba0265(v=vs.100))
