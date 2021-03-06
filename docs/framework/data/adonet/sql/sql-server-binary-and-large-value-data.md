---
title: Binární a velké hodnoty dat systému SQL Server
ms.date: 03/30/2017
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.openlocfilehash: c0202f6dc17d36fafb28206e17b71fc6d68d88c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33363403"
---
# <a name="sql-server-binary-and-large-value-data"></a>Binární a velké hodnoty dat systému SQL Server
SQL Server poskytuje `max` specifikátor, který rozbalí úložnou kapacitu `varchar`, `nvarchar`, a `varbinary` datové typy. `varchar(max)`, `nvarchar(max)`, a `varbinary(max)` se souhrnně označují jako *velké hodnoty datové typy*. Typy dat velké hodnoty můžete použít k uložení až 2 ^ 31-1 bajtů dat.  
  
 SQL Server 2008 zavádí FILESTREAM atribut, který není typu data, ale spíš atribut, který může být definováno na sloupci, což velké hodnoty data k uložení v systému souborů místo v databázi.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Úprava vysokých (maximálních) hodnot v ADO.NET](../../../../../docs/framework/data/adonet/sql/modifying-large-value-max-data.md)  
 Popisuje, jak pracovat s typy dat velké hodnoty.  
  
 [Data FILESTREAM](../../../../../docs/framework/data/adonet/sql/filestream-data.md)  
 Popisuje, jak pracovat s daty velké hodnoty, které jsou uložené v systému SQL Server 2008 s atributem FILESTREAM.  
  
## <a name="see-also"></a>Viz také  
 [Datové typy SQL Serveru a ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [Operace dat na SQL Serveru v ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 [Načítání a úpravy dat v ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
