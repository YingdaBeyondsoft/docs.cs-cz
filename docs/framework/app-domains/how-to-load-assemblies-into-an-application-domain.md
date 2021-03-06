---
title: 'Postupy: Načtení sestavení do domény aplikace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, loading assemblies
- loading assemblies
ms.assetid: 1432aa2d-bd83-4346-bf3b-a1b7920e2aa9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0925f7445c4451f61bd1c878cc66300d62bdc855
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32741903"
---
# <a name="how-to-load-assemblies-into-an-application-domain"></a>Postupy: Načtení sestavení do domény aplikace
Existuje několik způsobů načtení sestavení do domény aplikace. Doporučeným způsobem je použití `static` (`Shared` v jazyce Visual Basic) <xref:System.Reflection.Assembly.Load%2A> metodu <xref:System.Reflection.Assembly?displayProperty=nameWithType> třídy. Další způsoby, které lze načíst sestavení patří:  
  
-   <xref:System.Reflection.Assembly.LoadFrom%2A> Metodu <xref:System.Reflection.Assembly> třída načte sestavení zadané jeho umístění souboru. Načtení sestavení se tato metoda používá jiný zatížení kontextu.  
  
-   <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> a <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> metody načtení sestavení do kontextu pouze pro reflexi. Sestavení načtená do tohoto kontextu můžete zkontrolovat, ale nebyl proveden, povolení zkoumání sestavení, která cílí na jiných platformách. V tématu [postupy: načtení sestavení do kontextu pouze pro reflexi](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
> [!NOTE]
>  Kontext pouze pro reflexi je v rozhraní .NET Framework verze 2.0 nová.  
  
-   Metody, jako <xref:System.AppDomain.CreateInstance%2A> a <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> z <xref:System.AppDomain> třídy lze načíst sestavení do domény aplikace.  
  
-   <xref:System.Type.GetType%2A> Metodu <xref:System.Type> třída může načíst sestavení.  
  
-   <xref:System.AppDomain.Load%2A> Metodu <xref:System.AppDomain?displayProperty=nameWithType> třída může načíst sestavení, ale používá se především pro interoperabilita modelů COM. Není vhodné používat k načtení sestavení do domény aplikace než doménu aplikace, ze kterého se označuje jako.  
  
> [!NOTE]
>  Od verze rozhraní .NET Framework verze 2.0, modul runtime nenačte sestavení, které bylo kompilováno s verzi rozhraní .NET Framework, který má vyšší číslo verze než aktuálně načtených modulu runtime. To platí pro soubor součástí hlavní a vedlejší číslo verze.  
  
 Můžete zadat způsob, jakým v běhu (JIT) zkompilovaný kód z načíst sestavení jsou sdílena mezi aplikační domény. Další informace najdete v tématu [doménám a sestavením aplikací](http://msdn.microsoft.com/library/433b04ae-4ba8-4849-9dbd-79194f240346).  
  
## <a name="example"></a>Příklad  
 Následující kód načte sestavení s názvem "example.exe" nebo "example.dll" do aktuální domény aplikace získá typ s názvem `Example` od sestavení, získá metodu bez parametrů s názvem `MethodA` pro tohoto typu a provede metodu. Úplné informace o získání informací z načíst sestavení, najdete v části [dynamické načtení a použití typů](../../../docs/framework/reflection-and-codedom/dynamically-loading-and-using-types.md).  
  
 [!code-cpp[System.AppDomain.Load#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source2.cpp#2)]
 [!code-csharp[System.AppDomain.Load#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source2.cs#2)]
 [!code-vb[System.AppDomain.Load#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>  
 [Programování s doménami aplikací](application-domains.md#programming-with-application-domains)  
 [Reflexe](../../../docs/framework/reflection-and-codedom/reflection.md)  
 [Používání domén aplikací](../../../docs/framework/app-domains/use.md)  
 [Postupy: Načtení sestavení do kontextu pouze pro reflexi](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)  
 [Domény a sestavení aplikací](http://msdn.microsoft.com/library/433b04ae-4ba8-4849-9dbd-79194f240346)
