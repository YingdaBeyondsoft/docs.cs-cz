---
title: DbProviderFactories
ms.date: 03/30/2017
ms.assetid: 2a8e2640-3a49-42a1-a3a9-b43026907ae1
ms.openlocfilehash: 8692dc761f00e0ddc8ec9fad5a5df66b7fda7916
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32762296"
---
# <a name="dbproviderfactories"></a>DbProviderFactories
<xref:System.Data.Common> Obor názvů obsahuje třídy pro vytváření <xref:System.Data.Common.DbProviderFactory> instance pro práci s konkrétní zdroje dat. Při vytváření <xref:System.Data.Common.DbProviderFactory> instance a předejte ji informace o poskytovateli dat `DbProviderFactory` můžete určit objekt správný, silného typu připojení a vraťte se na základě informací, které bylo zadáno.  
  
 Od verze rozhraní .NET Framework verze 4, zprostředkovatelé dat, jako <xref:System.Data.Odbc>, <xref:System.Data.OleDb>, <xref:System.Data.SqlClient>, a <xref:System.Data.OracleClient> již nejsou uvedeny v souboru machine.config, ale vlastní zprostředkovatelé budou nadále uvedené existuje.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled modelu objektu pro vytváření](../../../../docs/framework/data/adonet/factory-model-overview.md)  
 Poskytuje přehled vzoru návrhu objektu pro vytváření a programovací rozhraní.  
  
 [Získání DbProviderFactory](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 Ukazuje, jak zobrazit seznam poskytovatelů nainstalované data a vytvářet <xref:System.Data.Common.DbConnection> z `DbProviderFactory`.  
  
 [DbConnection, DbCommand a DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 Ukazuje, jak vytvořit <xref:System.Data.Common.DbCommand> a <xref:System.Data.Common.DbDataReader>a jak se budou zpracovávat chyby dat pomocí <xref:System.Data.Common.DbException>.  
  
 [Úpravy dat přes DbDataAdapter](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 Ukazuje, jak používat <xref:System.Data.Common.DbCommandBuilder> s <xref:System.Data.Common.DbDataAdapter> k načtení a upravovat data.  
  
## <a name="see-also"></a>Viz také  
 [Načítání a úpravy dat v ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
