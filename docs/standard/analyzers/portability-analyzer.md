---
title: Analyzátor přenositelnost .NET - rozhraní .NET
description: Naučte se používat nástroj Analyzátor přenositelnost .NET vyhodnotit, jak přenosné váš kód je mezi různé implementace rozhraní .NET, včetně .NET Core, .NET Standard, UWP a Xamarin.
author: blackdwarf
ms.author: mairaw
ms.date: 07/26/2017
ms.technology: dotnet-standard
ms.assetid: 0375250f-5704-4993-a6d5-e21c499cea1e
ms.openlocfilehash: f310e5fe45315dfa41d596c92d9412dc6b3bc125
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567559"
---
# <a name="the-net-portability-analyzer"></a>Analyzátor přenositelnost rozhraní .NET

Chcete vytvořit více platformami knihovnách? Chcete zobrazit, kolik práce je požadováno, aby vaše aplikace kompatibilní s jinými implementace rozhraní .NET a profily, včetně .NET Core, .NET Standard, UWP a Xamarin pro iOS, Android a Mac? [.NET přenositelnost analyzátor](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer) je nástroj, který vám poskytne podrobnou zprávu o tom, jak flexibilní váš program je v rámci implementace rozhraní .NET analýzou sestavení. Přenositelnost Analyzátor je nabízena jako rozšíření Visual Studio a jako konzolové aplikace.

## <a name="new-targets"></a>Nové cíle

* [.NET core](../../core/index.md): má modulárnímu návrhu, aktivuje vedle sebe a cílem mezi různými platformami. Souběžně sdílená umožňuje přijmout nové verze .NET Core, aniž by vás jiné aplikace.
* [ASP.NET Core](/aspnet/core): je moderní webové – architektura založená na .NET Core a umožňuje vývojářům tak stejné výhody.
* [Univerzální platformu Windows](https://blogs.msdn.microsoft.com/dotnet/2014/04/24/net-native-performance): výkon vaší aplikace Windows Store, které běží na x64 a ARM počítačů pomocí .NET Native statické kompilace. 
* .NET core a rozšíření platformy: Zahrnuje rozhraní API .NET Core kromě jiná rozhraní API v ekosystému .NET například WCF, ASP.NET Core, FSharp a Azure.
* .NET standard + rozšíření platformy: Obsahuje standardní rozhraní API .NET kromě jiných ekosystém .NET, například WCF, ASP.NET Core, FSharp a Azure.

## <a name="how-to-use-portability-analyzer"></a>Postup použití analyzátoru přenositelnost

Pokud chcete začít používat analyzátor přenositelnost .NET, musíte nejprve stáhnout a nainstalovat rozšíření z [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer). V sadě Visual Studio 2015 a Visual Studio 2017 pracuje. Můžete ji nakonfigurovat v sadě Visual Studio prostřednictvím **analyzovat** > **přenositelnost Analyzátor nastavení** a vyberte cílové platformy.

![Snímek obrazovky přenositelnost](./media/portability-analyzer/portability-screenshot.png)

Chcete-li analyzovat celý projekt, klikněte pravým tlačítkem na projekt v **Průzkumníku řešení** a vyberte **analyzovat přenositelnost sestavení**. Jinak přejděte na **analyzovat** nabídku a vyberte **analyzovat přenositelnost sestavení**. Tam pak vyberete vašeho projektu spustitelný soubor nebo DLL.

![Průzkumník řešení přenositelnost](./media/portability-analyzer/portability-solution-explorer.png)

Po spuštění analýzy, zobrazí se sestavy přenositelnost .NET. Pouze typy, které nepodporuje Cílová platforma zobrazí v seznamu a vy můžete zkontrolovat doporučení v **zprávy** ve **seznam chyb**. Můžete také přejít na problémových oblastí přímo z **zprávy** kartě.

![Přenositelnost sestavy](./media/portability-analyzer/portability-report.png)

Nechcete použít Visual Studio? Můžete také použít analyzátor přenositelnost z příkazového řádku. Stáhnout pouze [rozhraní API přenositelnost analyzátor](http://www.microsoft.com/download/details.aspx?id=42678).

*   Zadejte následující příkaz k analýze aktuálním adresáři: `\...\ApiPort.exe analyze -f .`
*   K analýze konkrétní seznamu souborů DLL, zadejte následující příkaz: `\...\ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`

Přenositelnost sestavy .NET je uloženo jako soubor aplikace Excel (*XLSX*) v aktuálním adresáři. **Podrobnosti** karta v sešitu aplikace Excel obsahuje další informace.

Další informace o analyzátoru přenositelnost .NET, naleznete [Githubu dokumentace](https://github.com/Microsoft/dotnet-apiport#documentation) a [A stručný podívejte se na analyzátor přenositelnost .NET](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) video Channel 9.
