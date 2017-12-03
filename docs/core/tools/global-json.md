---
title: odkaz na Global.JSON
description: "Najdete v části schéma pro global.json souboru, který umožňuje nastavení verze nástrojů .NET Core."
keywords: "Rozhraní .NET, .NET core"
author: blackdwarf
ms.author: mairaw
ms.date: 04/05/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 96102f96-d403-4385-8ef6-5d80e406eb0c
ms.openlocfilehash: ffa97164736fc7f3edc450682d23bdf499b6eb34
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="globaljson-reference"></a><span data-ttu-id="1b569-104">odkaz na Global.JSON</span><span class="sxs-lookup"><span data-stu-id="1b569-104">global.json reference</span></span>

<span data-ttu-id="1b569-105">*Global.json* souboru umožňuje výběr verze nástrojů .NET Core používá prostřednictvím `sdk` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1b569-105">The *global.json* file allows selection of the .NET Core tools version being used through the `sdk` property.</span></span>

<span data-ttu-id="1b569-106">Nástrojů příkazového řádku .NET core vyhledejte tento soubor v aktuálním pracovním adresáři (který není nutně stejná jako adresáři projektu) nebo jednoho z jeho nadřazené adresáře.</span><span class="sxs-lookup"><span data-stu-id="1b569-106">.NET Core CLI tools look for this file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="sdk"></a><span data-ttu-id="1b569-107">Sada SDK</span><span class="sxs-lookup"><span data-stu-id="1b569-107">sdk</span></span>
<span data-ttu-id="1b569-108">Typ: objekt</span><span class="sxs-lookup"><span data-stu-id="1b569-108">Type: Object</span></span>

<span data-ttu-id="1b569-109">Určuje informace o sadě SDK.</span><span class="sxs-lookup"><span data-stu-id="1b569-109">Specifies information about the SDK.</span></span>

### <a name="version"></a><span data-ttu-id="1b569-110">verze</span><span class="sxs-lookup"><span data-stu-id="1b569-110">version</span></span>
<span data-ttu-id="1b569-111">Typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="1b569-111">Type: String</span></span>

<span data-ttu-id="1b569-112">Verze sady SDK k použití.</span><span class="sxs-lookup"><span data-stu-id="1b569-112">The version of the SDK to use.</span></span>

<span data-ttu-id="1b569-113">Příklad:</span><span class="sxs-lookup"><span data-stu-id="1b569-113">For example:</span></span>

```json
{
  "sdk": {
    "version": "1.0.0-preview2-003121"
  }
}
```