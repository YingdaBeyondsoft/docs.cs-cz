---
title: Vytváření bitových kopií Docker .NET Core
description: Seznámení s imagí Dockeru a .NET Core
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: e48a263334ebb93a5d281032336aeb4073d8467c
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/07/2018
ms.locfileid: "34827336"
---
# <a name="building-docker-images-for-net-core-applications"></a>Vytváření Imagí Dockeru pro aplikace .NET Core

 V tomto kurzu zaměříme na použití .NET Core na Docker. Nejdřív jsme prozkoumejte různé imagí Dockeru nabízí a spravován společností Microsoft a případy použití. Potom jsme zjistěte, jak vytvářet a dockerize aplikace ASP.NET Core.

V průběhu tohoto kurzu se seznámíte:
> [!div class="checklist"]
> * Další informace o rozhraní Microsoft .NET Core Docker obrázků 
> * Získat ukázkovou aplikaci k Dockerize ASP.NET Core
> * Místní spuštění ukázkové aplikace ASP.NET
> * Sestavení a spuštění vzorového Linux kontejnerů pomocí Docker
> * Sestavení a spuštění vzorového s kontejnery Docker pro Windows

## <a name="docker-image-optimizations"></a>Optimalizace na obrázku docker

Při vytváření imagí Dockeru pro vývojáře, zaměřili jsme se na třech hlavních scénářích:

* Obrázků použitých k vývoji aplikací .NET Core
* Bitové kopie sloužící k vytvoření aplikace .NET Core
* Bitové kopie používá ke spouštění aplikací .NET Core

Proč tři Image?
Při vyvíjení, vytváření a běh aplikací kontejnerizované, máme různých priorit.

* **Vývoj:** se zaměřuje priority na rychle iterovat změny a možnost ladění změny. Velikost bitové kopie není jako důležité, místo můžete provádět změny kódu a rychle vidět?

* **Sestavení:** tato bitová kopie obsahuje vše potřebné ke kompilaci aplikace, která zahrnuje kompilátor a další závislosti za účelem optimalizace binární soubory.  Bitovou kopii sestavení použijete k vytvoření prostředků, které umístíte do bitové kopie produkční. Sestavení image se použije pro nepřetržitou integraci, nebo v prostředí sestavení. Tento přístup umožňuje sestavení agenta pro zkompilování a vybuildování aplikace (s všechny požadované závislosti) v instanci sestavení bitové kopie. Agenta sestavení pouze musí vědět, jak spustit tento Docker image.

* **Produkční:** rychlost můžete nasadit a spustit image? Tento image je malý, takže je optimalizován výkon sítě z registru Docker do hostitelů Docker. Obsah je připraven ke spuštění povolení nejrychlejší čas z Docker spustit, aby se zpracování výsledků. Kompilace dynamický kód není potřeba mít ve Docker model. Obsah, který můžete umístit na tomto obrázku bude omezeno na binární soubory a obsah potřebné ke spuštění aplikace.

    Například `dotnet publish` výstup obsahuje:

    * kompilované binární soubory
    * soubory .js a .css


Z důvodu zahrnout `dotnet publish` výstupu příkazu v bitové kopii produkčního je zachování jeho velikost na minimum.

Některé obrázky, .NET Core sdílet vrstvy mezi různé značky, stahuje nejnovější značky je relativně jednoduché proces. Pokud již máte starší verze na počítači, sníží tato architektura místo na disku potřebné.

Když se více aplikací používat běžné bitové kopie na stejném počítači, paměti jsou sdílena mezi běžné bitové kopie. Image se musí shodovat s ke sdílení.

## <a name="docker-image-variations"></a>Variace docker bitové kopie

K dosažení výše uvedené cíle, poskytujeme variant bitové kopie v rámci [ `microsoft/dotnet` ](https://hub.docker.com/r/microsoft/dotnet/).

* `microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.1-sdk`) Tato bitová kopie obsahuje .NET Core SDK, která zahrnuje .NET Core a nástroje příkazového řádku (CLI). Tuto bitovou kopii se mapuje **vývoj scénář**. Můžete použít tuto bitovou kopii pro místní vývoj, ladění a testování částí. Tuto bitovou kopii lze také použít pro vaše **sestavení** scénáře. Pomocí `microsoft/dotnet:sdk` vždy obsahuje nejnovější verzi.

> [!TIP]
> Pokud si nejste jistí o vašim potřebám, kterou chcete použít `microsoft/dotnet:<version>-sdk` bitové kopie. Jako "de facto" bitovou kopii, je určený pro použití jako throw tokeny kontejneru (připojit zdrojový kód a spusťte kontejner a spusťte aplikaci) a jako základní bitovou kopii k vytvoření jiných obrázků z.

* `microsoft/dotnet:<version>-runtime`: Tento image obsahuje .NET Core (runtime a knihovny) a je optimalizovaná pro spouštění aplikací .NET Core **produkční**.

## <a name="alternative-images"></a>Alternativní bitové kopie

Kromě optimalizované scénářů vývoj, sestavení a produkční poskytujeme další bitové kopie:

* `microsoft/dotnet:<version>-runtime-deps`: **Runtime deps** bitová kopie obsahuje operační systém s všechny nativní závislosti vyžaduje .NET Core. Tento image je pro [nezávislý aplikace](../deploying/index.md).

Nejnovější verze jednotlivých variant:

* `microsoft/dotnet` nebo `microsoft/dotnet:latest` (alias pro bitovou kopii sady SDK)
* `microsoft/dotnet:sdk`
* `microsoft/dotnet:runtime`
* `microsoft/dotnet:runtime-deps`

## <a name="samples-to-explore"></a>Ukázky a prozkoumejte

* [Tato ukázka ASP.NET Core Docker](https://github.com/dotnet/dotnet-docker/tree/master/samples/aspnetapp) ukazuje osvědčených postupů vzor pro vytváření imagí Dockeru pro ASP.NET Core aplikace pro produkční prostředí. Ukázka funguje s kontejnery Linux a Windows.

* Tento příklad .NET Core Docker znázorňuje osvědčených postupů vzor [vytváření imagí Dockeru pro aplikace .NET Core pro produkční prostředí.](https://github.com/dotnet/dotnet-docker/tree/master/samples/dotnetapp)

## <a name="your-first-aspnet-core-docker-app"></a>První aplikace ASP.NET Core Docker

V tomto kurzu umožňuje použití ukázkové aplikace ASP.NET Core Docker pro aplikaci, kterou chceme dockerize. Tato ukázková aplikace ASP.NET Core Docker představuje nejlepší postup vzor pro vytváření imagí Dockeru pro ASP.NET Core aplikace pro produkční prostředí. Ukázka funguje s kontejnery Linux a Windows.

Ukázkový soubor Docker vytvoří image Docker aplikace ASP.NET Core na základě technologie ASP.NET Core Runtime Docker základní bitovou kopii.

Použije [Docker více fáze sestavení funkce](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) na:

* sestavit ukázku v kontejneru na základě **větší** základní image ASP.NET Core sestavení Docker 
* zkopíruje do Docker image na základě výsledku poslední sestavení **menší** základní image ASP.NET Core Docker Runtime

> [!NOTE]
> Sestavení bitová kopie obsahuje požadované nástroje k vytváření aplikací při bitovou kopii runtime neexistuje.

### <a name="prerequisites"></a>Požadavky

Sestavení a spuštění, nainstalujte následující položky:

#### <a name="net-core-21-sdk"></a>.NET core 2.1 SDK

* Nainstalujte [.NET Core SDK 2.1](https://www.microsoft.com/net/core).

* Pokud jste to ještě neudělali, nainstalujte editor vaše oblíbené kódu.

> [!TIP]
> Je potřeba nainstalovat editor kódu? Zkuste [sady Visual Studio](https://visualstudio.com/downloads)!

#### <a name="installing-docker-client"></a>Instalace klienta Docker

Nainstalujte [Docker 18.03](https://docs.docker.com/release-notes/docker-ce/) nebo novější Docker klienta.

Klient Docker může být nainstalován v:

* Distribuce systému Linux

   * [CentOS](https://www.docker.com/docker-centos-distribution)

   * [Debian](https://www.docker.com/docker-debian)

   * [Fedora](https://www.docker.com/docker-fedora)

   * [Ubuntu](https://www.docker.com/docker-ubuntu)

* [macOS](https://docs.docker.com/docker-for-mac/)

* [Windows](https://docs.docker.com/docker-for-windows/).

#### <a name="installing-git-for-sample-repository"></a>Instalace Gitu pro ukázkové úložiště

* Nainstalujte [git](https://git-scm.com/download) Pokud chcete klonovat úložiště.

### <a name="getting-the-sample-application"></a>Získávání ukázkové aplikace

Nejjednodušší způsob, jak získat ukázce je klonováním [úložiště .NET Core Docker](https://github.com/dotnet/dotnet-docker) s gitem, pomocí následujících pokynů: 

```console
git clone https://github.com/dotnet/dotnet-docker
```

Můžete také stáhnout úložiště (je malý) jako zip z úložiště .NET Core Docker.

### <a name="run-the-aspnet-app-locally"></a>Místní spuštění aplikace ASP.NET

Jako referenční bod před jsme containerize aplikace, nejprve spustíte aplikaci místně.

Můžete sestavit a spustit aplikaci místně pomocí .NET SDK 2.1 základní pomocí následujících příkazů (pokyny předpokládají kořenovém adresáři úložiště):

```console
cd dotnet-docker
cd samples
cd aspnetapp // solution scope where the dockerfile is located
cd aspnetapp // project scope

dotnet run
```

Po spuštění aplikace, navštivte **http://localhost:5000** ve webovém prohlížeči.

### <a name="build-and-run-the-sample-with-docker-for-linux-containers"></a>Sestavení a spuštění vzorového Linux kontejnerů pomocí Docker

Můžete sestavit a spustit ukázku v Docker použití kontejnerů Linux pomocí následujících příkazů (pokyny předpokládají kořenovém adresáři úložiště):

```console
cd dotnet-docker
cd samples
cd aspnetapp // solution scope where the dockerfile is located

docker build -t aspnetapp .
docker run -it --rm -p 5000:80 --name aspnetcore_sample aspnetapp
```

> [!NOTE]
> `docker run` '-P' argument port 5000 na místním počítači na port 80 v kontejneru mapy (formulář mapování portů `host:container`). Další informace najdete v tématu [docker spustit](https://docs.docker.com/engine/reference/commandline/exec/) odkazu na parametry příkazového řádku.

Po spuštění aplikace, navštivte **http://localhost:5000** ve webovém prohlížeči.

### <a name="build-and-run-the-sample-with-docker-for-windows-containers"></a>Sestavení a spuštění vzorového s kontejnery Docker pro Windows

Můžete sestavit a spustit ukázku v Docker použití Windows kontejnerů pomocí následujících příkazů (pokyny předpokládají kořenovém adresáři úložiště):

```console
cd dotnet-docker
cd samples
cd aspnetapp // solution scope where the dockerfile is located

docker build -t aspnetapp .
docker run -it --rm --name aspnetcore_sample aspnetapp
```

> [!IMPORTANT]
> Je nutné na Přejít **kontejneru IP adresu** (Naproti tomu http://localhost) v prohlížeči přímo při použití Windows kontejnerů. Můžete získat IP adresu vašeho kontejneru pomocí následujících kroků:

* Otevřete jiného příkazového řádku.
* Spustit `docker ps` zobrazíte spuštěných kontejnerů. Kontejner "aspnetcore_sample" by měla existovat.
* Run `docker exec aspnetcore_sample ipconfig`.
* IP adresa kontejneru zkopírujte a vložte do prohlížeče (například 172.29.245.43).

> [!NOTE]
> Docker exec podporuje identifikační kontejnery s názvem nebo hodnoty hash. V našem příkladu se používá název (aspnetcore_sample).

Podívejte se na následující příklad toho, jak získat IP adresu spuštěné kontejneru systému Windows.

```console
docker exec aspnetcore_sample ipconfig

Windows IP Configuration

Ethernet adapter Ethernet:

   Connection-specific DNS Suffix  . : contoso.com
   Link-local IPv6 Address . . . . . : fe80::1967:6598:124:cfa3%4
   IPv4 Address. . . . . . . . . . . : 172.29.245.43
   Subnet Mask . . . . . . . . . . . : 255.255.240.0
   Default Gateway . . . . . . . . . : 172.29.240.1
```

> [!NOTE]
> Docker exec spustí nový příkaz v běžící kontejneru. Další informace najdete v tématu [docker exec odkaz](https://docs.docker.com/engine/reference/commandline/exec/) na parametry příkazového řádku.

Může vytvářet aplikace, která je připravená k nasazení do produkčního prostředí místně pomocí [dotnet publikování](../tools/dotnet-publish.md) příkaz.

```console
dotnet publish -c Release -o published
```

> [!NOTE]
> - C argument verze sestavení aplikace v režimu vydání (výchozí hodnota je režim ladění). Další informace najdete v tématu [dotnet. Spusťte odkaz](../tools/dotnet-run.md) na parametry příkazového řádku.

Spuštění aplikace na **Windows** pomocí následujícího příkazu.

```console
dotnet published\aspnetapp.dll
```

Spuštění aplikace na **Linux** nebo **systému macOS** pomocí následujícího příkazu.

```bash
dotnet published/aspnetapp.dll
```

### <a name="docker-images-used-in-this-sample"></a>Docker obrázků použitých v této ukázce

V této ukázce soubor docker se používají následující imagí Dockeru.

* `microsoft/dotnet:2.1-sdk`
* `microsoft/dotnet:2.1-aspnetcore-runtime`

Blahopřejeme! máte právě:
> [!div class="checklist"]
> * Naučili o imagí Dockeru základní rozhraní Microsoft .NET
> * Tu ASP.NET Core ukázkové aplikaci Dockerize
> * Byla spuštěna místně ukázková aplikace ASP.NET
> * Vytvořené a spustil ukázku pomocí Docker pro Linux kontejnery
> * Vytvořené a spustil vzorku s kontejnery Docker pro Windows


**Další kroky**

Zde jsou některé další kroky, které můžete provést:

* [Práce s nástroji Visual Studio Docker](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [Nasazení bitových kopií Docker z registru kontejner Azure do Azure kontejner instancí](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [Ladění pomocí kódu v sadě Visual Studio](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) 
* [Načítání rukou pomocí sady Visual Studio pro Mac, kontejnery a bez serveru kódu v cloudu](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [Začínáme s Docker a Visual Studio pro Mac testovacího prostředí](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

> [!NOTE]
> Pokud nemáte předplatné Azure, [Přihlaste se ještě dnes](https://azure.microsoft.com/free/?b=16.48) bezplatný účet 30 dnů a 200 USD get v kredity Azure můžete vyzkoušet na libovolnou kombinaci služby Azure.
