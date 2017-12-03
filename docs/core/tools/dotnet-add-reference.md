---
title: "DotNet – přidat odkaz na příkaz - .NET Core rozhraní příkazového řádku"
description: "Dotnet přidat odkaz na příkaz poskytuje vhodnou možnost přidat odkazy na projekt na projekt."
author: mairaw
ms.author: mairaw
ms.date: 09/19/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 9c6b0f434a9d6b1431e375ec6a437497aaddfc61
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-add-reference"></a><span data-ttu-id="14413-103">DotNet – přidání odkazu</span><span class="sxs-lookup"><span data-stu-id="14413-103">dotnet-add reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="14413-104">Název</span><span class="sxs-lookup"><span data-stu-id="14413-104">Name</span></span>

<span data-ttu-id="14413-105">`dotnet add reference`-Přidá odkazy na projekt na projekt (P2P).</span><span class="sxs-lookup"><span data-stu-id="14413-105">`dotnet add reference` - Adds project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="14413-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="14413-106">Synopsis</span></span>

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="14413-107">Popis</span><span class="sxs-lookup"><span data-stu-id="14413-107">Description</span></span>

<span data-ttu-id="14413-108">`dotnet add reference` Příkaz poskytuje vhodnou možnost přidat odkazy na projekt na projekt.</span><span class="sxs-lookup"><span data-stu-id="14413-108">The `dotnet add reference` command provides a convenient option to add project references to a project.</span></span> <span data-ttu-id="14413-109">Po spuštění příkazu [ `<ProjectReference>` ](/visualstudio/msbuild/common-msbuild-project-items) prvky jsou přidány do souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="14413-109">After running the command, the [`<ProjectReference>`](/visualstudio/msbuild/common-msbuild-project-items) elements are added to the project file.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a><span data-ttu-id="14413-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="14413-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="14413-111">Určuje soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="14413-111">Specifies the project file.</span></span> <span data-ttu-id="14413-112">Pokud není zadaný, hledá příkaz aktuální adresář pro jednu.</span><span class="sxs-lookup"><span data-stu-id="14413-112">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="14413-113">Chcete-li přidat odkazuje na projekt na projekt (P2P).</span><span class="sxs-lookup"><span data-stu-id="14413-113">Project-to-project (P2P) references to add.</span></span> <span data-ttu-id="14413-114">Zadejte jeden nebo více projektů.</span><span class="sxs-lookup"><span data-stu-id="14413-114">Specify one or more projects.</span></span> <span data-ttu-id="14413-115">[Vzory glob](https://en.wikipedia.org/wiki/Glob_(programming)) jsou podporovány v systémech UNIX/Linux.</span><span class="sxs-lookup"><span data-stu-id="14413-115">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux-based systems.</span></span>

## <a name="options"></a><span data-ttu-id="14413-116">Možnosti</span><span class="sxs-lookup"><span data-stu-id="14413-116">Options</span></span>

`-h|--help`

<span data-ttu-id="14413-117">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="14413-117">Prints out a short help for the command.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="14413-118">Přidá odkazy na projekt jenom při cílení na konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="14413-118">Adds project references only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="14413-119">Příklady</span><span class="sxs-lookup"><span data-stu-id="14413-119">Examples</span></span>

<span data-ttu-id="14413-120">Přidáte odkaz na projekt:</span><span class="sxs-lookup"><span data-stu-id="14413-120">Add a project reference:</span></span>

`dotnet add app/app.csproj reference lib/lib.csproj`

<span data-ttu-id="14413-121">Přidání více odkazy na projekt na projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="14413-121">Add multiple project references to the project in the current directory:</span></span>

`dotnet add reference lib1/lib1.csproj lib2/lib2.csproj`

<span data-ttu-id="14413-122">Přidání více odkazů projektu pomocí vzoru expanze názvů v systému Linux nebo Unix:</span><span class="sxs-lookup"><span data-stu-id="14413-122">Add multiple project references using a globbing pattern on Linux/Unix:</span></span>

`dotnet add app/app.csproj reference **/*.csproj`