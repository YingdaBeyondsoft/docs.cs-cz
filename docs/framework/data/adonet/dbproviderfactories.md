---
title: DbProviderFactories
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2a8e2640-3a49-42a1-a3a9-b43026907ae1
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0e8c6310b8ce164a60541dae030ce603bccd372e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="dbproviderfactories"></a><span data-ttu-id="d84de-102">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="d84de-102">DbProviderFactories</span></span>
<span data-ttu-id="d84de-103"><xref:System.Data.Common> Obor názvů obsahuje třídy pro vytváření <xref:System.Data.Common.DbProviderFactory> instance pro práci s konkrétní zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="d84de-103">The <xref:System.Data.Common> namespace provides classes for creating <xref:System.Data.Common.DbProviderFactory> instances to work with specific data sources.</span></span> <span data-ttu-id="d84de-104">Při vytváření <xref:System.Data.Common.DbProviderFactory> instance a předejte ji informace o poskytovateli dat `DbProviderFactory` můžete určit objekt správný, silného typu připojení a vraťte se na základě informací, které bylo zadáno.</span><span class="sxs-lookup"><span data-stu-id="d84de-104">When you create a <xref:System.Data.Common.DbProviderFactory> instance and pass it information about the data provider, the `DbProviderFactory` can determine the correct, strongly typed connection object to return based on the information it has been provided.</span></span>  
  
 <span data-ttu-id="d84de-105">Od verze rozhraní .NET Framework verze 4, zprostředkovatelé dat, jako <xref:System.Data.Odbc>, <xref:System.Data.OleDb>, <xref:System.Data.SqlClient>, a <xref:System.Data.OracleClient> již nejsou uvedeny v souboru machine.config, ale vlastní zprostředkovatelé budou nadále uvedené existuje.</span><span class="sxs-lookup"><span data-stu-id="d84de-105">Beginning in the .NET Framework version 4, data providers such as <xref:System.Data.Odbc>, <xref:System.Data.OleDb>, <xref:System.Data.SqlClient>, and <xref:System.Data.OracleClient> are no longer listed in machine.config file, but custom providers will continue to be listed there.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d84de-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d84de-106">In This Section</span></span>  
 [<span data-ttu-id="d84de-107">Přehled modelu objektu pro vytváření</span><span class="sxs-lookup"><span data-stu-id="d84de-107">Factory Model Overview</span></span>](../../../../docs/framework/data/adonet/factory-model-overview.md)  
 <span data-ttu-id="d84de-108">Poskytuje přehled vzoru návrhu objektu pro vytváření a programovací rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d84de-108">Provides an overview of the factory design pattern and programming interface.</span></span>  
  
 [<span data-ttu-id="d84de-109">Získání DbProviderFactory</span><span class="sxs-lookup"><span data-stu-id="d84de-109">Obtaining a DbProviderFactory</span></span>](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 <span data-ttu-id="d84de-110">Ukazuje, jak zobrazit seznam poskytovatelů nainstalované data a vytvářet <xref:System.Data.Common.DbConnection> z `DbProviderFactory`.</span><span class="sxs-lookup"><span data-stu-id="d84de-110">Demonstrates how to list the installed data providers and create a <xref:System.Data.Common.DbConnection> from a `DbProviderFactory`.</span></span>  
  
 [<span data-ttu-id="d84de-111">Připojení DbConnection, DbCommand a dbexception –</span><span class="sxs-lookup"><span data-stu-id="d84de-111">DbConnection, DbCommand and DbException</span></span>](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 <span data-ttu-id="d84de-112">Ukazuje, jak vytvořit <xref:System.Data.Common.DbCommand> a <xref:System.Data.Common.DbDataReader>a jak se budou zpracovávat chyby dat pomocí <xref:System.Data.Common.DbException>.</span><span class="sxs-lookup"><span data-stu-id="d84de-112">Demonstrates how to create a <xref:System.Data.Common.DbCommand> and <xref:System.Data.Common.DbDataReader>, and how to handle data errors using <xref:System.Data.Common.DbException>.</span></span>  
  
 [<span data-ttu-id="d84de-113">Úprava dat s DbDataAdapter</span><span class="sxs-lookup"><span data-stu-id="d84de-113">Modifying Data with a DbDataAdapter</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 <span data-ttu-id="d84de-114">Ukazuje, jak používat <xref:System.Data.Common.DbCommandBuilder> s <xref:System.Data.Common.DbDataAdapter> k načtení a upravovat data.</span><span class="sxs-lookup"><span data-stu-id="d84de-114">Demonstrates how to use a <xref:System.Data.Common.DbCommandBuilder> with a <xref:System.Data.Common.DbDataAdapter> to retrieve and modify data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d84de-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="d84de-115">See Also</span></span>  
 [<span data-ttu-id="d84de-116">Načítání a upravovat Data v technologii ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d84de-116">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="d84de-117">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="d84de-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)