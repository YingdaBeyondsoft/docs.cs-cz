---
title: příkaz úložiště DotNet.
description: Příkaz 'dotnet úložiště, ukládá na zadaná sestavení v úložišti balíček modulu runtime.
author: bleroy
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 54654522207157f7d49bb86223b7986acccf51ee
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696322"
---
# <a name="dotnet-store"></a>úložiště DotNet.

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a>Název

`dotnet store` -Ukládá na zadaná sestavení v [úložiště balíčku runtime](../deploying/runtime-store.md).

## <a name="synopsis"></a>Stručný obsah

`dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]`

## <a name="description"></a>Popis

`dotnet store` ukládá na zadaná sestavení v [úložiště balíčku runtime](../deploying/runtime-store.md). Ve výchozím nastavení jsou sestavení optimalizované pro cílový modul runtime a framework. Další informace najdete v tématu [úložiště balíčku runtime](../deploying/runtime-store.md) tématu.

## <a name="required-options"></a>Požadované možnosti

`-f|--framework <FRAMEWORK>`

Určuje, [cílové rozhraní](../../standard/frameworks.md).

`-m|--manifest <PATH_TO_MANIFEST_FILE>`

*Souboru manifestu balíčku úložiště* je soubor XML, který obsahuje seznam balíčků pro uložení. Formát souboru manifestu není kompatibilní s formátem stylu SDK projektu. Ano, dá použít soubor projektu, který odkazuje na požadované balíčky s `-m|--manifest` možnost ukládat sestavení v úložišti balíček modulu runtime. Pokud chcete zadat více souborů manifestu, opakujte pro každý soubor možnost a cestu. Příklad: `--manifest packages1.csproj --manifest packages2.csproj`.

`-r|--runtime <RUNTIME_IDENTIFIER>`

[Runtime identifikátor](../rid-catalog.md) k cíli.

## <a name="optional-options"></a>Volitelné možnosti

`--framework-version <FRAMEWORK_VERSION>`

Určuje verzi rozhraní .NET Core SDK. Tato možnost umožňuje vybrat konkrétní framework verze mimo rámec určeného `-f|--framework` možnost.

`-h|--help`

Zobrazí nápovědu informace.

`-o|--output <OUTPUT_DIRECTORY>`

Určuje cestu k úložišti balíček modulu runtime. Pokud není zadáno, výchozí hodnota *ukládání* podadresáři instalační adresář uživatelského profilu .NET Core.

`--skip-optimization`

Přeskočí fázi optimalizace.

`--skip-symbols`

Přeskočí symbolů generace. V současné době můžete vygenerovat pouze symboly v systému Windows a Linux.

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.

`-w|--working-dir <INTERMEDIATE_WORKING_DIRECTORY>`

Pracovní adresář využívá příkaz. Pokud není zadaný, použije *obj* podadresáři aktuálního adresáře.

## <a name="examples"></a>Příklady

Ukládat balíčky v zadané *packages.csproj* soubor projektu pro .NET Core 2.0.0:

`dotnet store --manifest packages.csproj --framework-version 2.0.0`

Ukládat balíčky v zadané *packages.csproj* bez optimalizace:

`dotnet store --manifest packages.csproj --skip-optimization`

## <a name="see-also"></a>Viz také:

[Úložiště balíčků modulu runtime](../deploying/runtime-store.md)