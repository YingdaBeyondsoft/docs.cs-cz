---
title: Šifrování dat v systému SQL Server
ms.date: 03/30/2017
ms.assetid: 83b992f7-b351-4678-b4b9-f4ffd58134cc
ms.openlocfilehash: 9e2924dc9f2f2954f6690ad5009c4143d1b9a44f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358365"
---
# <a name="data-encryption-in-sql-server"></a>Šifrování dat v systému SQL Server
SQL Server poskytuje funkce pro šifrování a dešifrování dat pomocí certifikátu, asymetrického klíče nebo symetrického klíče. Spravuje všechny tyto v úložišti vnitřní certifikát. Úložiště používá k šifrování hierarchii, který zabezpečuje certifikáty a klíče na jedné úrovni vrstva nad ním v hierarchii. Tato oblast funkcí systému SQL Server se nazývá tajný klíč úložiště.  
  
 Nejrychlejší režim šifrování nepodporuje funkce šifrování je šifrování symetrického klíče. Tento režim je vhodný pro zpracování velkých objemů dat. Symetrické klíče se můžou šifrovat certifikáty, hesla nebo dalších symetrické klíče.  
  
## <a name="keys-and-algorithms"></a>Klíčů a algoritmy  
 SQL Server podporuje několik algoritmy šifrování symetrického klíče, včetně DES, Triple DES, RC2, RC4, RC4 128-bit, DESX, AES 128-bit, AES 192 bitů a AES 256 bitů. Algoritmy jsou implementovány pomocí rozhraní API pro šifrování systému Windows.  
  
 V rámci oboru připojení k databázi systému SQL Server můžete udržovat více otevřete symetrické klíče. Otevřít klíč je načíst z úložiště a je k dispozici pro dešifrování dat. Když se dešifrují část dat, není nutné specifikovat symetrický klíč pro použití. Každý zašifrovanou hodnotu obsahuje klíč identifikátor (klíč identifikátor GUID) klíč používaný k jejich zašifrování. Modul odpovídá šifrované bajtů datového proudu k otevřete symetrický klíč, pokud správný klíč po dešifrování a je otevřené. Tento klíč je pak používá k dešifrování a vrátit data. Pokud správný klíč není otevřený, vrátí se hodnota NULL.  
  
 Příklad, který ukazuje, jak pracovat s šifrovaných dat v databázi, naleznete v části [postupy: šifrování sloupec dat](http://go.microsoft.com/fwlink/?LinkID=128559) v SQL Server Books Online.  
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace o šifrování dat najdete v následujících materiálech.  
  
|||  
|-|-|  
|[Šifrování SQL serveru](http://msdn.microsoft.com/library/bb510663.aspx) v Online knihách serveru SQL|Obsahuje přehled šifrování v sloužit SQL. Toto téma obsahuje odkazy na další témata a jak – k společnosti.|  
|[Šifrování hierarchie](http://msdn.microsoft.com/library/ms189586.aspx) a [témata s postupy pro šifrování](http://msdn.microsoft.com/library/aa337557.aspx) v Online knihách serveru SQL|Poskytuje přehled o šifrování v systému SQL Server. Toto téma obsahuje odkazy na další témata a jak – k společnosti.|  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Scénáře zabezpečení aplikací na SQL Serveru](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Ověřování v SQL Serveru](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 [Serverové a databázové role na SQL Serveru](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)  
 [Vlastnictví a oddělení uživatelských schémat na SQL Serveru](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)  
 [Autorizace a oprávnění na SQL Serveru](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
