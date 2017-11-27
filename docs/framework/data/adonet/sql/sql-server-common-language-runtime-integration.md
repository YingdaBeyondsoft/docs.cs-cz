---
title: SQL Server Common Language Runtime Integration
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7a324c4-160d-44c2-b593-641af06eca61
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3705db8b9d359ce83c6c47bef58de327745bed44
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="sql-server-common-language-runtime-integration"></a><span data-ttu-id="6c382-102">SQL Server Common Language Runtime Integration</span><span class="sxs-lookup"><span data-stu-id="6c382-102">SQL Server Common Language Runtime Integration</span></span>
<span data-ttu-id="6c382-103">SQL Server 2005 zavedl integrace součást společné language runtime (CLR) rozhraní .NET Framework pro Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="6c382-103">SQL Server 2005 introduced the integration of the common language runtime (CLR) component of the .NET Framework for Microsoft Windows.</span></span> <span data-ttu-id="6c382-104">To znamená, že můžete napsat uložené procedury, triggery, uživatelem definované typy, uživatelem definované funkce, uživatelem definovaných agregacích a streamování funkce vracející tabulku pomocí žádný jazyk rozhraní .NET Framework, včetně Microsoft Visual Basic .NET a společnosti Microsoft Visual C#.</span><span class="sxs-lookup"><span data-stu-id="6c382-104">This means that you can write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, including Microsoft Visual Basic .NET and Microsoft Visual C#.</span></span> <span data-ttu-id="6c382-105"><xref:Microsoft.SqlServer.Server> Obor názvů obsahuje sadu nové aplikačními programovacími rozhraními (API) tak, aby spravovaný kód můžete spolupracovat s prostředím Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="6c382-105">The <xref:Microsoft.SqlServer.Server> namespace contains a set of new application programming interfaces (APIs) so that managed code can interact with the Microsoft SQL Server environment.</span></span>  
  
 <span data-ttu-id="6c382-106">Tato část popisuje funkce a chování, které jsou specifické pro systému SQL Server common language runtime (CLR) integrace a konkrétní rozšíření v procesu systému SQL Server pro technologii ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="6c382-106">This section describes features and behaviors that are specific to SQL Server common language runtime (CLR) integration and the SQL Server in-process specific extensions to ADO.NET.</span></span>  
  
 <span data-ttu-id="6c382-107">Tato část poskytuje jenom dostatek informací, abyste mohli začít programování s integrace modulu CLR SQL serveru a není určen jako komplexní.</span><span class="sxs-lookup"><span data-stu-id="6c382-107">This section is meant to provide only enough information to get started programming with SQL Server CLR integration, and is not meant to be comprehensive.</span></span> <span data-ttu-id="6c382-108">Podrobnější informace najdete v tématu verze SQL Server Books Online pro verzi systému SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="6c382-108">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="6c382-109">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="6c382-109">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="6c382-110">Běžné koncepty programování integrace Language Runtime (CLR)</span><span class="sxs-lookup"><span data-stu-id="6c382-110">Common Language Runtime (CLR) Integration Programming Concepts</span></span>](http://go.microsoft.com/fwlink/?LinkId=115240)  
  
## <a name="in-this-section"></a><span data-ttu-id="6c382-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="6c382-111">In This Section</span></span>  
 [<span data-ttu-id="6c382-112">Úvod do integrace modulu CLR SQL serveru</span><span class="sxs-lookup"><span data-stu-id="6c382-112">Introduction to SQL Server CLR Integration</span></span>](../../../../../docs/framework/data/adonet/sql/introduction-to-sql-server-clr-integration.md)  
 <span data-ttu-id="6c382-113">Poskytuje úvod do integrace modulu CLR SQL serveru.</span><span class="sxs-lookup"><span data-stu-id="6c382-113">Provides an introduction to SQL Server CLR integration.</span></span> <span data-ttu-id="6c382-114">Obsahuje odkazy na další témata.</span><span class="sxs-lookup"><span data-stu-id="6c382-114">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="6c382-115">Uživatelem definované funkce CLR</span><span class="sxs-lookup"><span data-stu-id="6c382-115">CLR User-Defined Functions</span></span>](../../../../../docs/framework/data/adonet/sql/clr-user-defined-functions.md)  
 <span data-ttu-id="6c382-116">Popisuje, jak k implementaci a použití různých typů CLR funkce: agregační funkce vracející tabulku, skalární a uživatelem definované.</span><span class="sxs-lookup"><span data-stu-id="6c382-116">Describes how to implement and use the various types of CLR functions: table-valued, scalar, and user-defined aggregate functions.</span></span>  
  
 [<span data-ttu-id="6c382-117">Uživatelem definované typy CLR</span><span class="sxs-lookup"><span data-stu-id="6c382-117">CLR User-Defined Types</span></span>](../../../../../docs/framework/data/adonet/sql/clr-user-defined-types.md)  
 <span data-ttu-id="6c382-118">Popisuje, jak k implementaci a použití uživatelem definované typy CLR.</span><span class="sxs-lookup"><span data-stu-id="6c382-118">Describes how to implement and use CLR user-defined types.</span></span> <span data-ttu-id="6c382-119">Obsahuje odkazy na další témata.</span><span class="sxs-lookup"><span data-stu-id="6c382-119">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="6c382-120">CLR uložené procedury</span><span class="sxs-lookup"><span data-stu-id="6c382-120">CLR Stored Procedures</span></span>](../../../../../docs/framework/data/adonet/sql/clr-stored-procedures.md)  
 <span data-ttu-id="6c382-121">Popisuje, jak k implementaci a použití CLR uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="6c382-121">Describes how to implement and use CLR stored procedures.</span></span> <span data-ttu-id="6c382-122">Obsahuje odkazy na další témata.</span><span class="sxs-lookup"><span data-stu-id="6c382-122">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="6c382-123">Aktivační procedury modulu CLR</span><span class="sxs-lookup"><span data-stu-id="6c382-123">CLR Triggers</span></span>](../../../../../docs/framework/data/adonet/sql/clr-triggers.md)  
 <span data-ttu-id="6c382-124">Popisuje, jak implementovat a použít aktivační procedury modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="6c382-124">Describes how to implement and use CLR triggers.</span></span> <span data-ttu-id="6c382-125">Obsahuje odkazy na další témata.</span><span class="sxs-lookup"><span data-stu-id="6c382-125">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="6c382-126">Připojení kontextu</span><span class="sxs-lookup"><span data-stu-id="6c382-126">The Context Connection</span></span>](../../../../../docs/framework/data/adonet/sql/the-context-connection.md)  
 <span data-ttu-id="6c382-127">Popisuje připojení kontextu.</span><span class="sxs-lookup"><span data-stu-id="6c382-127">Describes the context connection.</span></span>  
  
 [<span data-ttu-id="6c382-128">SQL Server v specifické pro proces chování ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6c382-128">SQL Server In-Process-Specific Behavior of ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-in-process-specific-behavior-of-adonet.md)  
 <span data-ttu-id="6c382-129">Popisuje konkrétní rozšíření systému SQL Server v rámci procesu ADO.NET a připojení kontextu.</span><span class="sxs-lookup"><span data-stu-id="6c382-129">Describes the SQL Server in-process specific extensions to ADO.NET, and the context connection.</span></span> <span data-ttu-id="6c382-130">Obsahuje odkazy na další témata.</span><span class="sxs-lookup"><span data-stu-id="6c382-130">Provides links to additional topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c382-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="6c382-131">See Also</span></span>  
 [<span data-ttu-id="6c382-132">SQL Server a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6c382-132">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)  
 [<span data-ttu-id="6c382-133">Vytváření objektů serveru SQL Server 2005 ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="6c382-133">Creating SQL Server 2005 Objects In Managed Code</span></span>](http://msdn.microsoft.com/en-us/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [<span data-ttu-id="6c382-134">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="6c382-134">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)