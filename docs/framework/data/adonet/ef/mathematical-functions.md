---
title: Matematické funkce
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: 9dfd1faf9bdab995b19c38e32f64a88ed67cb280
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766969"
---
# <a name="mathematical-functions"></a>Matematické funkce
Zprostředkovatel dat .NET Framework pro SQL Server (SqlClient) poskytuje matematické funkce, které provádějí výpočty s vstupní hodnoty, které jsou k dispozici jako argumenty a vrátí výsledek číselná hodnota. Tyto funkce jsou v oboru názvů SQL Server, která je k dispozici při použití SqlClient. Umožňuje vlastnost obor názvů zprostředkovatele Entity Frameworku chcete zjistit, která předpona je používána tohoto poskytovatele pro konkrétní konstrukce, jako jsou typy a funkce. Následující tabulka popisuje matematické funkce SqlClient.  
  
|Funkce|Popis|  
|--------------|-----------------|  
|`ABS(` `expression` `)`|Provede funkci absolutní hodnotu.<br /><br /> **Argumenty**<br /><br /> `expression`: `Int32`, `Int64`, `Double`, Nebo `Decimal`.<br /><br /> **Návratová hodnota**<br /><br /> Absolutní hodnota, z určeného výrazu.<br /><br /> **Příklad**<br /><br /> `SqlServer.ABS(-2)`|  
|`ACOS(` `expression` `)`|Vrátí hodnotu Arkus, z určeného výrazu.<br /><br /> **Argumenty**<br /><br /> `expression`: A `Double`.<br /><br /> **Návratová hodnota**<br /><br /> A `Double`.<br /><br /> **Příklad**<br /><br /> `SqlServer.ACOS(.9)`|  
|`ASIN(` `expression` `)`|Vrátí Arkus sinus hodnotu zadaného výrazu.<br /><br /> **Argumenty**<br /><br /> `expression`: A `Double`.<br /><br /> **Návratová hodnota**<br /><br /> A `Double`.<br /><br /> **Příklad**<br /><br /> `SqlServer.ASIN(.9)`|  
|`ATAN(` `expression` `)`|Vrátí hodnotu Arkus zadaný číselný výraz.<br /><br /> **Argumenty**<br /><br /> `expression`: A `Double`.<br /><br /> **Návratová hodnota**<br /><br /> A `Double`.<br /><br /> **Příklad**<br /><br /> `SqlServer.ATAN(9)`|  
|`ATN2(` `expression`, `expression``)`|Vrací úhel, v radiánech, jehož tangens je mezi zadaný dvou numerických výrazů.<br /><br /> **Argumenty**<br /><br /> `expression`: A `Double`.<br /><br /> **Návratová hodnota**<br /><br /> A `Double`.<br /><br /> **Příklad**<br /><br /> `SqlServer.ATN2(9, 8)`|  
|`CEILING(` `expression` `)`|Převede zadaný výraz na nejmenší celé číslo, které je větší než nebo rovno ho.<br /><br /> **Argumenty**<br /><br /> `expression`: `Int32`, `Int64`, `Double`, Nebo `Decimal`.<br /><br /> **Návratová hodnota**<br /><br /> `Int32`, `Int64`, `Double`, Nebo `Decimal`.<br /><br /> **Příklad**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_CEILING](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_ceiling)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]|  
|`COS(` `expression` `)`|Vypočítá trigonometrické kosinus určeného úhlu v radiánech.<br /><br /> **Argumenty**<br /><br /> `expression`: A `Double`.<br /><br /> **Návratová hodnota**<br /><br /> A `Double`.<br /><br /> **Příklad**<br /><br /> `SqlServer.COS(45)`|  
|`COT(` `expression` `)`|Vypočítá trigonometrické kotangens zadaný úhel v radiánech.<br /><br /> **Argumenty**<br /><br /> `expression`: A `Double`.<br /><br /> **Návratová hodnota**<br /><br /> A `Double`.<br /><br /> **Příklad**<br /><br /> `SqlServer.COT(60)`|  
|`DEGREES(` `radians` `)`|Vrací odpovídající úhel ve stupních.<br /><br /> **Argumenty**<br /><br /> `expression`: `Int32`, `Int64`, `Double`, Nebo `Decimal`.<br /><br /> **Návratová hodnota**<br /><br /> `Int32`, `Int64`, `Double`, Nebo `Decimal`.<br /><br /> **Příklad**<br /><br /> `SqlServer.DEGREES(3.1)`|  
|`EXP(` `expression` `)`|Vypočítá exponenciální hodnotu zadaného číselného výrazu.<br /><br /> **Argumenty**<br /><br /> `expression`: A `Double`.<br /><br /> **Návratová hodnota**<br /><br /> A `Double`.<br /><br /> **Příklad**<br /><br /> `SqlServer.EXP(1)`|  
|`FLOOR(` `expression` `)`|Převede zadaný výraz největší celé číslo menší než nebo rovna k němu.<br /><br /> **Argumenty**<br /><br /> `expression`: A `Double`.<br /><br /> **Návratová hodnota**<br /><br /> A `Double`.<br /><br /> **Příklad**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_FLOOR](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_floor)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]|  
|`LOG(` `expression` `)`|Vypočítá přirozený logaritmus zadaného `float` výraz.<br /><br /> **Argumenty**<br /><br /> `expression`: A `Double`.<br /><br /> **Návratová hodnota**<br /><br /> A `Double`.<br /><br /> **Příklad**<br /><br /> `SqlServer.LOG(100)`|  
|`LOG10(` `expression` `)`|Vrátí logaritmus základu 10 zadaného `Double` výraz.<br /><br /> **Argumenty**<br /><br /> `expression`: A `Double`.<br /><br /> **Návratová hodnota**<br /><br /> A `Double`.<br /><br /> **Příklad**<br /><br /> `SqlServer.LOG10(100)`|  
|`PI()`|Vrátí hodnotu čísla pí jako konstanty `Double`.<br /><br /> **Návratová hodnota**<br /><br /> A `Double`.<br /><br /> **Příklad**<br /><br /> `SqlServer.PI()`|  
|`POWER(` `numeric_expression, power_expression` `)`|Vypočítá hodnotu zadaného výrazu na zadanou mocninu.<br /><br /> **Argumenty**<br /><br /> `numeric_expression`: `Int32`, `Int64`, `Double`, Nebo `Decimal`.<br /><br /> `power_expression`: A `Double` představující napájení, do kterého se mají zvýšit `numeric_expression`.<br /><br /> **Návratová hodnota**<br /><br /> Hodnota zadaného `numeric_expression` do zadané `power_expression`.<br /><br /> **Příklad**<br /><br /> `SqlServer.POWER(2,7)`|  
|`RADIANS(` `expression` `)`|Převede radiánech stupňů.<br /><br /> **Argumenty**<br /><br /> `expression`: `Int32`, `Int64`, `Double`, Nebo `Decimal`.<br /><br /> **Návratová hodnota**<br /><br /> `Int32`, `Int64`,<br /><br /> `Double`, nebo<br /><br /> `Decimal`.<br /><br /> **Příklad**<br /><br /> `SqlServer.RADIANS(360.0)`|  
|`RAND(`[počáteční hodnoty]`)`|Vrátí náhodné hodnotu od 0 do 1.<br /><br /> **Argumenty**<br /><br /> Hodnota Retruns počáteční hodnoty jako `Int32`. Pokud počáteční hodnotu nezadáte, přiřadí databázového stroje SQL Server v náhodných počáteční hodnoty. Pro zadaný počáteční hodnoty výsledek vrácený je vždy stejný.<br /><br /> **Návratová hodnota**<br /><br /> Náhodnou `Double` hodnotu od 0 do 1.<br /><br /> **Příklad**<br /><br /> `SqlServer.RAND()`|  
|`ROUND(` `numeric_expression, length` [ ,`function` ]`)`|Vrátí hodnotu číselného výrazu, zaokrouhlí se zadané délky nebo přesnosti.<br /><br /> **Argumenty**<br /><br /> `numeric_expression`: `Int32`, `Int64`, `Double`, Nebo `Decimal`.<br /><br /> `length`: `Int32` Představující přesnost, ke kterému `numeric_expression` je má být zaokrouhleno. Když `length` kladné číslo, `numeric_expression` se zaokrouhlí na počet desetinných pozic určeného `length`. Když `length` záporné číslo, `numeric_expression` se zaokrouhlí na levé straně od desetinné čárky, podle specifikace `length`.<br /><br /> `function`: (nepovinný) `Int32` , která představuje typ operaci provést. Když funkce je vynechán nebo má hodnotu 0 (výchozí), `numeric_expression` zaokrouhleno. Když jinou hodnotu než je zadána hodnota 0, `numeric_expression` se zkrátí.<br /><br /> **Návratová hodnota**<br /><br /> Hodnota zadaného `numeric_expression` do zadané `power_expression`.<br /><br /> **Příklad**<br /><br /> `SqlServer.ROUND(748.58, -3)`|  
|`SIGN(` `expression` `)`|Vrátí kladnou (+ 1), nula (0) nebo záporné znaménko (-1), z určeného výrazu.<br /><br /> **Argumenty**<br /><br /> `expression`: `Int32`, `Int64`, `Double`, nebo `Decimal`<br /><br /> **Návratová hodnota**<br /><br /> `Int32`, `Int64`, `Double`, Nebo `Decimal`.<br /><br /> **Příklad**<br /><br /> `SqlServer.SIGN(-10)`|  
|`SIN(` `expression` `)`|Vypočítá trigonometrické sinus určeného úhlu v radiánech a vrátí `Double` výraz.<br /><br /> **Argumenty**<br /><br /> `expression`: A `Double`.<br /><br /> **Návratová hodnota**<br /><br /> A `Double`.<br /><br /> **Příklad**<br /><br /> `SqlServer.SIN(20)`|  
|`SQRT(` `expression` `)`|Vrátí druhou odmocninu, z určeného výrazu.<br /><br /> **Argumenty**<br /><br /> `expression`: A `Double`.<br /><br /> **Návratová hodnota**<br /><br /> A `Double`.<br /><br /> **Příklad**<br /><br /> `SqlServer.SQRT(3600)`|  
|`SQUARE(` `expression` `)`|Vrátí druhou, z určeného výrazu.<br /><br /> **Argumenty**<br /><br /> `expression`: A `Double`.<br /><br /> **Návratová hodnota**<br /><br /> A `Double`.<br /><br /> **Příklad**<br /><br /> `SqlServer.SQUARE(25)`|  
|`TAN(` `expression` `)`|Vypočítá tangens zadaného výrazu.<br /><br /> **Argumenty**<br /><br /> `expression`: `Double`<br /><br /> **Návratová hodnota**<br /><br /> `Double`<br /><br /> **Příklad**<br /><br /> `SqlServer.TAN(45.0)`|  
  
 Další informace o matematické funkce, které SqlClient podporuje najdete v dokumentaci pro používanou verzi systému SQL Server, který jste zadali v manifestu zprostředkovatele, SqlClient:  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[Matematické funkce (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115913)|[Matematické funkce (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115911)|[Matematické funkce (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115912)|  
  
## <a name="see-also"></a>Viz také  
 [SqlClient pro funkce Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)
