---
title: Obecné pokyny
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Obecné pokyny
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: ccaae99f4c46fe739041f9b9e907a702303e62f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592571"
---
# <a name="general-guidance"></a>Obecné pokyny

Tato část obsahuje souhrn kdy zvolte .NET Core nebo rozhraní .NET Framework. Poskytujeme další podrobnosti o těchto možnostech v následujících částech.

.NET Core byste měli používat se systémem Linux nebo Windows kontejnery, pro aplikaci kontejnerizované server Docker při:

-   Máte potřebám napříč platformami. Například chcete použít, Linux a Windows kontejnery.

-   Architektuře aplikace je založena na mikroslužeb.

-   Budete muset rychlého spuštění kontejnery a aby bylo možné snížit náklady na chcete malé nároky na kontejneru zajistit lepší hustotu nebo více kontejnerů na jednotku hardwaru.

Stručně řečeno když vytvoříte nové kontejnerizované aplikací .NET, měli byste zvážit .NET Core jako výchozí volba. Má řadu výhod a nejlépe vyhovuje filosofie kontejnery a styl práci.

Další výhodou používání .NET Core je, že můžete spustit vedle sebe verze rozhraní .NET pro aplikace v rámci stejného počítače. Tuto výhodu je důležitější pro servery nebo virtuální počítače, které nepoužívají kontejnery, protože kontejnery izolovat verze rozhraní .NET, které aplikace potřebuje. (Za předpokladu, jsou kompatibilní s základního operačního systému.)

Rozhraní .NET Framework, byste měli použít s kontejnery Windows pro vaše kontejnerizované serverová aplikace Docker při:

-   Vaše aplikace právě používá rozhraní .NET Framework a má silné závislosti v systému Windows.

-   Budete muset použít rozhraní API systému Windows, který nepodporuje .NET Core.

-   Budete muset použít knihovny .NET třetích stran nebo balíčky NuGet, které nejsou k dispozici pro .NET Core.

Pomocí rozhraní .NET Framework na Docker lze vylepšit své zkušenosti nasazení minimalizovat problémy při nasazení. To [ *"navýšení a posunutí" scénář* ](https://aka.ms/liftandshiftwithcontainersebook) je důležité pro containerizing starší aplikace, které byly původně vyvinuté s tradiční rozhraní .NET Framework jako webových formulářů ASP.NET, MVC webových aplikací nebo WCF ( Služby Windows Communication Foundation).

### <a name="additional-resources"></a>Další zdroje

-   **elektronická kniha: modernizovat existující aplikace rozhraní .NET Framework s Azure a Windows kontejnery**
    [*https://aka.ms/liftandshiftwithcontainersebook*](https://aka.ms/liftandshiftwithcontainersebook)

-   **Ukázkové aplikace: modernizace starší verze webové aplikace ASP.NET pomocí Windows kontejnery**
    [*https://aka.ms/eshopmodernizing*](https://aka.ms/eshopmodernizing)


>[!div class="step-by-step"]
[Předchozí] (index.md) [Další] (net – základní – kontejner scenarios.md)
