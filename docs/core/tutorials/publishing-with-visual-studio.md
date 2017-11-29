---
title: "Publikování aplikace Hello World s Visual Studio 2017"
description: "Publikování vytvoří sadu souborů, které jsou potřebné ke spuštění vaší aplikace."
keywords: "Konzolové aplikace .NET, .NET core, publikování, nasazení"
author: BillWagner
ms.author: wiwagn
ms.date: 10/05/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a19545d3-24af-4a32-9778-cfb5ae938287
ms.openlocfilehash: a3e5bda5c99144c9ab5bbaf5e2f5566261af4813
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="publish-your-hello-world-application-with-visual-studio-2017"></a><span data-ttu-id="41001-104">Publikování aplikace Hello World s Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="41001-104">Publish your Hello World application with Visual Studio 2017</span></span>

<span data-ttu-id="41001-105">V [sestavení C# Hello, World aplikace s .NET Core ve Visual Studio 2017](with-visual-studio.md) nebo [sestavení aplikace Visual Basic Hello World s .NET Core ve Visual Studio 2017](vb-with-visual-studio.md), jste vytvořili konzolovou aplikaci Hello World .</span><span class="sxs-lookup"><span data-stu-id="41001-105">In [Build a C# Hello World application with .NET Core in Visual Studio 2017](with-visual-studio.md) or [Build a Visual Basic Hello World application with .NET Core in Visual Studio 2017](vb-with-visual-studio.md), you built a Hello World console application.</span></span> <span data-ttu-id="41001-106">V [ladění aplikace C# Hello, World s Visual Studio 2017](debugging-with-visual-studio.md), můžete otestovat pomocí ladicího programu sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="41001-106">In [Debug your C# Hello World application with Visual Studio 2017](debugging-with-visual-studio.md), you tested it using the Visual Studio debugger.</span></span> <span data-ttu-id="41001-107">Teď, když jste si jisti, že funguje podle očekávání, můžete publikovat tak, aby mohli ostatní uživatelé spouštět.</span><span class="sxs-lookup"><span data-stu-id="41001-107">Now that you're sure that it works as expected, you can publish it so that other users can run it.</span></span> <span data-ttu-id="41001-108">Publikování vytvoří sadu souborů, které jsou potřebné ke spuštění vaší aplikace a soubory můžete nasadit jejich zkopírováním do cílového počítače.</span><span class="sxs-lookup"><span data-stu-id="41001-108">Publishing creates the set of files that are needed to run your application, and you can deploy the files by copying them to a target machine.</span></span>

<span data-ttu-id="41001-109">K publikování a spuštění aplikace:</span><span class="sxs-lookup"><span data-stu-id="41001-109">To publish and run your application:</span></span> 

1. <span data-ttu-id="41001-110">Ujistěte se, že Visual Studio vytváří verzi vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="41001-110">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="41001-111">V případě potřeby změňte nastavení konfigurace sestavení na panelu nástrojů z **ladění** k **verze**.</span><span class="sxs-lookup"><span data-stu-id="41001-111">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   ![Panel nástrojů Visual Studio](media/publishing-with-visual-studio/toolbar.png)

1. <span data-ttu-id="41001-113">Klikněte pravým tlačítkem na **HelloWorld** projektu (ne HelloWorld řešení) a vyberte **publikovat** z nabídky.</span><span class="sxs-lookup"><span data-stu-id="41001-113">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span> <span data-ttu-id="41001-114">Můžete také vybrat **publikování HelloWorld** z hlavní sady Visual Studio **sestavení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="41001-114">You can also select **Publish HelloWorld** from the main Visual Studio **Build** menu.</span></span>

   ![Panel nástrojů Visual Studio](media/publishing-with-visual-studio/publish1.png)


   ![Panel nástrojů Visual Studio](media/publishing-with-visual-studio/publishwindow.png)

1. <span data-ttu-id="41001-117">Otevřete okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="41001-117">Open a console window.</span></span> <span data-ttu-id="41001-118">Například v **typ pro hledání** textové pole na hlavním panelu systému Windows, zadejte `Command Prompt` (nebo `cmd` pro zkrácení) a otevřete okno konzoly můžete buď **příkazového řádku** plochy aplikace nebo stisknutím klávesy Enter, pokud je vybrána ve výsledcích hledání.</span><span class="sxs-lookup"><span data-stu-id="41001-118">For example in the **Type here to search** text box in the Windows taskbar, enter `Command Prompt` (or `cmd` for short), and open a console window by either selecting the **Command Prompt** desktop app or pressing Enter if it's selected in the search results.</span></span>

1. <span data-ttu-id="41001-119">Přejděte k publikované aplikaci v `bin\release\PublishOutput` podadresáři adresáře projektu vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="41001-119">Navigate to the published application in the `bin\release\PublishOutput` subdirectory of your application's project directory.</span></span> <span data-ttu-id="41001-120">Jak ukazuje následující obrázek, publikované výstup obsahuje následující čtyři soubory:</span><span class="sxs-lookup"><span data-stu-id="41001-120">As the following figure shows, the published output includes the following four files:</span></span>

      * <span data-ttu-id="41001-121">*HelloWorld.deps.json*</span><span class="sxs-lookup"><span data-stu-id="41001-121">*HelloWorld.deps.json*</span></span>

         <span data-ttu-id="41001-122">Soubor modulu runtime závislosti aplikace.</span><span class="sxs-lookup"><span data-stu-id="41001-122">The application's runtime dependencies file.</span></span> <span data-ttu-id="41001-123">Definuje součásti .NET Core a knihovny (včetně knihovnu DLL, která obsahuje aplikaci) potřebné ke spuštění vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="41001-123">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run your application.</span></span> <span data-ttu-id="41001-124">Další informace najdete v tématu [souborů konfigurace modulu Runtime](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="41001-124">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>
 
      * <span data-ttu-id="41001-125">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="41001-125">*HelloWorld.dll*</span></span>

         <span data-ttu-id="41001-126">Soubor, který obsahuje vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="41001-126">The file that contains your application.</span></span> <span data-ttu-id="41001-127">Je knihovnu DLL, kterou lze provést zadáním `dotnet HelloWorld.dll` příkazu v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="41001-127">It is a dynamic link library that can be executed by entering the `dotnet HelloWorld.dll` command in a console window.</span></span> 

      * <span data-ttu-id="41001-128">*HelloWorld.pdb* (pro nasazení volitelné)</span><span class="sxs-lookup"><span data-stu-id="41001-128">*HelloWorld.pdb* (optional for deployment)</span></span>

         <span data-ttu-id="41001-129">Soubor, který obsahuje symboly ladění.</span><span class="sxs-lookup"><span data-stu-id="41001-129">A file that contains debug symbols.</span></span> <span data-ttu-id="41001-130">Není nutné k nasazení tohoto souboru spolu s vaší aplikace, i když byste měli uložit v případě, že budete muset ladění publikovanou verzi vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="41001-130">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

      * <span data-ttu-id="41001-131">*HelloWorld.runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="41001-131">*HelloWorld.runtimeconfig.json*</span></span>

         <span data-ttu-id="41001-132">Konfigurační soubor modulu runtime pro aplikace.</span><span class="sxs-lookup"><span data-stu-id="41001-132">The application's runtime configuration file.</span></span> <span data-ttu-id="41001-133">Identifikuje verzi .NET Core, který vaše aplikace byla vytvořena za účelem spuštění.</span><span class="sxs-lookup"><span data-stu-id="41001-133">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="41001-134">Další informace najdete v tématu [souborů konfigurace modulu Runtime](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="41001-134">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>  

   ![Okno konzoly zobrazující publikované soubory](media/publishing-with-visual-studio/publishedfiles.png)

<span data-ttu-id="41001-136">Proces publikování vytvoří nasazení závislé na framework, což je typ nasazení, kde je publikovaná aplikace poběží na žádnou platformu podporovanou nástrojem .NET Core s .NET Core nainstalované v systému.</span><span class="sxs-lookup"><span data-stu-id="41001-136">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application will run on any platform supported by .NET Core with .NET Core installed on the system.</span></span> <span data-ttu-id="41001-137">Uživatelé mohou spouštět aplikaci po vydání `dotnet HelloWorld.dll` příkazu v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="41001-137">Users can run your application by issuing the `dotnet HelloWorld.dll` command from a console window.</span></span>

<span data-ttu-id="41001-138">Další informace o publikování a nasazení aplikací .NET Core, najdete v části [nasazení aplikace .NET Core](../../core/deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="41001-138">For more information on publishing and deploying .NET Core applications, see [.NET Core Application Deployment](../../core/deploying/index.md).</span></span>