---
title: "Webové služby Obecné serializace technologie ukázky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cdc15ea4-f678-4729-8ebe-188ae720bef7
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a0ec4f05fd68c523bcffcb9173de7e66d0dcc9a0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="web-services-generics-serialization-technology-sample"></a><span data-ttu-id="2a547-102">Webové služby Obecné serializace technologie ukázky</span><span class="sxs-lookup"><span data-stu-id="2a547-102">Web Services Generics Serialization Technology Sample</span></span>
[<span data-ttu-id="2a547-103">Stažení ukázky</span><span class="sxs-lookup"><span data-stu-id="2a547-103">Download Sample</span></span>](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/GenericsSerialization.zip.exe)  
  
 <span data-ttu-id="2a547-104">Tento příklad ukazuje, jak používat a řízení serializace obecných typů ve webové služby ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="2a547-104">This sample shows how to use and control the serialization of generics in ASP.NET Web Services.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="2a547-105">K vytvoření vzorku pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2a547-105">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="2a547-106">Otevřete Visual Studio a vyberte **nový web** z **souboru** nabídky.</span><span class="sxs-lookup"><span data-stu-id="2a547-106">Open Visual Studio and select **New Web Site** from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="2a547-107">V **nový web** dialogové okno, v levém podokně vyberte požadovaný programovací jazyk a pak v pravém podokně vyberte **webovou službu ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="2a547-107">In the **New Web Site** dialog, select from the left pane your desired programming language, then from the right pane, select **ASP.NET Web Service**.</span></span>  
  
3.  <span data-ttu-id="2a547-108">Klikněte na tlačítko **Procházet** a přejděte do podadresáři \CS\GenericsService.</span><span class="sxs-lookup"><span data-stu-id="2a547-108">Click **Browse** and navigate to the \CS\GenericsService subdirectory.</span></span>  
  
4.  <span data-ttu-id="2a547-109">Vyberte Service.asmx k otevření souboru v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2a547-109">Select Service.asmx to open the file in Visual Studio.</span></span>  
  
5.  <span data-ttu-id="2a547-110">Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="2a547-110">On the **Build** menu, click **Build Solution**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a547-111">Prvních pět kroků v tomto seznamu jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="2a547-111">The first five steps in this list are optional.</span></span> <span data-ttu-id="2a547-112">Modul runtime rozhraní .NET Framework, bude automaticky generovat webové služby první čas, kdy je požadována služba.</span><span class="sxs-lookup"><span data-stu-id="2a547-112">The .NET Framework runtime will automatically generate the Web service the first time the service is requested.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a547-113">Následující kroky jsou nutné k vytvoření vzorku.</span><span class="sxs-lookup"><span data-stu-id="2a547-113">The following steps are required to build the sample.</span></span>  
  
1.  <span data-ttu-id="2a547-114">Otevřít [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] a přejděte do podadresáře \CS.</span><span class="sxs-lookup"><span data-stu-id="2a547-114">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to the \CS subdirectory.</span></span>  
  
2.  <span data-ttu-id="2a547-115">Klikněte pravým tlačítkem myši na ikonu podadresáři GenericsService a vyberte **sdílení a zabezpečení**.</span><span class="sxs-lookup"><span data-stu-id="2a547-115">Right-click the icon for the GenericsService subdirectory, and select **Sharing and Security**.</span></span>  
  
3.  <span data-ttu-id="2a547-116">V **sdílení na webu** vyberte **Sdílejte tuto složku**.</span><span class="sxs-lookup"><span data-stu-id="2a547-116">In the **Web Sharing** tab, select **Share this Folder**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2a547-117">Poznamenejte si název virtuálního adresáře, který je uvedený v **aliasy** podokně, protože jeho spuštění ukázky budete potřebovat.</span><span class="sxs-lookup"><span data-stu-id="2a547-117">Take note of the virtual directory name that is listed in the **Aliases** pane, because you will need it to run the sample.</span></span>  
  
### <a name="to-build-the-sample-using-internet-information-services"></a><span data-ttu-id="2a547-118">K vytvoření vzorku pomocí Internetové informační služby</span><span class="sxs-lookup"><span data-stu-id="2a547-118">To build the sample using Internet Information Services</span></span>  
  
1.  <span data-ttu-id="2a547-119">Otevřete **Internetová informační služba** správy modulu snap-in a rozbalte **weby**.</span><span class="sxs-lookup"><span data-stu-id="2a547-119">Open the **Internet Information Services** management snap-in and expand **Web Sites**.</span></span>  
  
2.  <span data-ttu-id="2a547-120">Klepnutí levým tlačítkem myši **Default Web Site**, vyberte **nový**a potom vyberte **virtuální adresář?** vytvořit **Průvodce vytvořením virtuálního adresáře**.</span><span class="sxs-lookup"><span data-stu-id="2a547-120">Left-click **Default Web Site**, select **New**, and then select **Virtual Directory?** to create the **Virtual Directory Creation Wizard**.</span></span>  
  
3.  <span data-ttu-id="2a547-121">Klikněte na tlačítko **Další**zadejte veřejný alias pro virtuální adresář a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="2a547-121">Click **Next**, enter the public alias for your virtual directory, and click **Next**.</span></span>  
  
4.  <span data-ttu-id="2a547-122">Zadejte cestu k adresáři, kam jste uložili ukázkové (obvykle podadresáři \CS\GenericsService) a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="2a547-122">Enter the path to the directory where you saved the sample (normally the \CS\GenericsService subdirectory) and click **Next**.</span></span> <span data-ttu-id="2a547-123">Klikněte na tlačítko **Další** ukončíte průvodce.</span><span class="sxs-lookup"><span data-stu-id="2a547-123">Click **Next** to finish the wizard.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2a547-124">Poznamenejte si název virtuálního adresáře, který je uvedený v **Alias** podokně, protože jeho spuštění ukázky budete potřebovat.</span><span class="sxs-lookup"><span data-stu-id="2a547-124">Take note of the virtual directory name that is listed in the **Alias** pane, because you will need it to run the sample.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="2a547-125">Chcete-li spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="2a547-125">To run the sample</span></span>  
  
1.  <span data-ttu-id="2a547-126">Otevřete okno prohlížeče a vyberte jeho adresa.</span><span class="sxs-lookup"><span data-stu-id="2a547-126">Open a browser window and select its address bar.</span></span>  
  
2.  <span data-ttu-id="2a547-127">Typ **http://localhost/ [virtuální directory]/Service.asmx**, kde [virtuálního adresáře] představuje virtuální adresář, který jste vytvořili, když jste vytvořili vzorku.</span><span class="sxs-lookup"><span data-stu-id="2a547-127">Type **http://localhost/[virtual directory]/Service.asmx**, where [virtual directory] represents the virtual directory you created when you built the sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a547-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2a547-128">Remarks</span></span>  
 <span data-ttu-id="2a547-129">Ukázka zobrazí výchozí stránka technologie ASP.NET, která obsahuje odkazy na definice webové služby.</span><span class="sxs-lookup"><span data-stu-id="2a547-129">The sample displays a default ASP.NET page that contains links to the definition of the Web Service.</span></span> <span data-ttu-id="2a547-130">Můžete přizpůsobit zobrazení kromě Změna zdrojového kódu webové služby.</span><span class="sxs-lookup"><span data-stu-id="2a547-130">You can customize the display in addition to modifying the source code for the Web service.</span></span> <span data-ttu-id="2a547-131">Další informace najdete v tématu [klienty vytváření XML webové služby](http://msdn.microsoft.com/en-us/c606f3cb-4111-45b4-ae42-9300420fa16c).</span><span class="sxs-lookup"><span data-stu-id="2a547-131">For more information, see [Building XML Web Service Clients](http://msdn.microsoft.com/en-us/c606f3cb-4111-45b4-ae42-9300420fa16c).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a547-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="2a547-132">See Also</span></span>  
 <xref:System.Collections.Generic>  
 <xref:System.Web.Services>  
 <xref:System.Xml.Serialization>  
 [<span data-ttu-id="2a547-133">Serializace</span><span class="sxs-lookup"><span data-stu-id="2a547-133">Serialization</span></span>](../../../docs/standard/serialization/index.md)  
 [<span data-ttu-id="2a547-134">Webové služby XML vytvořený pomocí technologie ASP.NET a klienty webové služby XML</span><span class="sxs-lookup"><span data-stu-id="2a547-134">XML Web Services Created Using ASP.NET and XML Web Service Clients</span></span>](http://msdn.microsoft.com/en-us/1e64af78-d705-4384-b08d-591a45f4379c)