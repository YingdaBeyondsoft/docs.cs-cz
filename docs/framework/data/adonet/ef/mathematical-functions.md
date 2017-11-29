---
title: "Matematické funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8390f1e1822d7581ab0352a8c81acbc7ce545507
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="mathematical-functions"></a><span data-ttu-id="2029d-102">Matematické funkce</span><span class="sxs-lookup"><span data-stu-id="2029d-102">Mathematical Functions</span></span>
<span data-ttu-id="2029d-103">Zprostředkovatel dat .NET Framework pro SQL Server (SqlClient) poskytuje matematické funkce, které provádějí výpočty s vstupní hodnoty, které jsou k dispozici jako argumenty a vrátí výsledek číselná hodnota.</span><span class="sxs-lookup"><span data-stu-id="2029d-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides math functions that perform calculations on input values that are provided as arguments, and return a numeric value result.</span></span> <span data-ttu-id="2029d-104">Tyto funkce jsou v oboru názvů SQL Server, která je k dispozici při použití SqlClient.</span><span class="sxs-lookup"><span data-stu-id="2029d-104">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="2029d-105">Umožňuje vlastnost obor názvů zprostředkovatele Entity Frameworku chcete zjistit, která předpona je používána tohoto poskytovatele pro konkrétní konstrukce, jako jsou typy a funkce. Následující tabulka popisuje matematické funkce SqlClient.</span><span class="sxs-lookup"><span data-stu-id="2029d-105">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.The following table describes the SqlClient math functions.</span></span>  
  
|<span data-ttu-id="2029d-106">Funkce</span><span class="sxs-lookup"><span data-stu-id="2029d-106">Function</span></span>|<span data-ttu-id="2029d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2029d-107">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="2029d-108">`ABS(` `expression` `)`</span><span class="sxs-lookup"><span data-stu-id="2029d-108">`ABS(` `expression` `)`</span></span>|<span data-ttu-id="2029d-109">Provede funkci absolutní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2029d-109">Performs the absolute value function.</span></span><br /><br /> <span data-ttu-id="2029d-110">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="2029d-110">**Arguments**</span></span><br /><br /> <span data-ttu-id="2029d-111">`expression`: `Int32`, `Int64`, `Double`, Nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="2029d-111">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span><br /><br /> <span data-ttu-id="2029d-112">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="2029d-112">**Return Value**</span></span><br /><br /> <span data-ttu-id="2029d-113">Absolutní hodnota, z určeného výrazu.</span><span class="sxs-lookup"><span data-stu-id="2029d-113">The absolute value of the specified expression.</span></span><br /><br /> <span data-ttu-id="2029d-114">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="2029d-114">**Example**</span></span><br /><br /> `SqlServer.ABS(-2)`|  
|<span data-ttu-id="2029d-115">`ACOS(` `expression` `)`</span><span class="sxs-lookup"><span data-stu-id="2029d-115">`ACOS(` `expression` `)`</span></span>|<span data-ttu-id="2029d-116">Vrátí hodnotu Arkus, z určeného výrazu.</span><span class="sxs-lookup"><span data-stu-id="2029d-116">Returns the arccosine value of the specified expression.</span></span><br /><br /> <span data-ttu-id="2029d-117">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="2029d-117">**Arguments**</span></span><br /><br /> <span data-ttu-id="2029d-118">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="2029d-118">`expression`: A `Double`.</span></span><br /><br /> <span data-ttu-id="2029d-119">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="2029d-119">**Return Value**</span></span><br /><br /> <span data-ttu-id="2029d-120">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="2029d-120">A `Double`.</span></span><br /><br /> <span data-ttu-id="2029d-121">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="2029d-121">**Example**</span></span><br /><br /> `SqlServer.ACOS(.9)`|  
|<span data-ttu-id="2029d-122">`ASIN(` `expression` `)`</span><span class="sxs-lookup"><span data-stu-id="2029d-122">`ASIN(` `expression` `)`</span></span>|<span data-ttu-id="2029d-123">Vrátí Arkus sinus hodnotu zadaného výrazu.</span><span class="sxs-lookup"><span data-stu-id="2029d-123">Returns the arcsine value of the specified expression.</span></span><br /><br /> <span data-ttu-id="2029d-124">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="2029d-124">**Arguments**</span></span><br /><br /> <span data-ttu-id="2029d-125">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="2029d-125">`expression`: A `Double`.</span></span><br /><br /> <span data-ttu-id="2029d-126">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="2029d-126">**Return Value**</span></span><br /><br /> <span data-ttu-id="2029d-127">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="2029d-127">A `Double`.</span></span><br /><br /> <span data-ttu-id="2029d-128">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="2029d-128">**Example**</span></span><br /><br /> `SqlServer.ASIN(.9)`|  
|<span data-ttu-id="2029d-129">`ATAN(` `expression` `)`</span><span class="sxs-lookup"><span data-stu-id="2029d-129">`ATAN(` `expression` `)`</span></span>|<span data-ttu-id="2029d-130">Vrátí hodnotu Arkus zadaný číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="2029d-130">Returns the arctangent value of the specified numeric expression.</span></span><br /><br /> <span data-ttu-id="2029d-131">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="2029d-131">**Arguments**</span></span><br /><br /> <span data-ttu-id="2029d-132">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="2029d-132">`expression`: A `Double`.</span></span><br /><br /> <span data-ttu-id="2029d-133">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="2029d-133">**Return Value**</span></span><br /><br /> <span data-ttu-id="2029d-134">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="2029d-134">A `Double`.</span></span><br /><br /> <span data-ttu-id="2029d-135">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="2029d-135">**Example**</span></span><br /><br /> `SqlServer.ATAN(9)`|  
|<span data-ttu-id="2029d-136">`ATN2(` `expression`, `expression``)`</span><span class="sxs-lookup"><span data-stu-id="2029d-136">`ATN2(` `expression`, `expression``)`</span></span>|<span data-ttu-id="2029d-137">Vrací úhel, v radiánech, jehož tangens je mezi zadaný dvou numerických výrazů.</span><span class="sxs-lookup"><span data-stu-id="2029d-137">Returns the angle, in radians, whose tangent is between the two specified numeric expressions.</span></span><br /><br /> <span data-ttu-id="2029d-138">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="2029d-138">**Arguments**</span></span><br /><br /> <span data-ttu-id="2029d-139">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="2029d-139">`expression`: A `Double`.</span></span><br /><br /> <span data-ttu-id="2029d-140">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="2029d-140">**Return Value**</span></span><br /><br /> <span data-ttu-id="2029d-141">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="2029d-141">A `Double`.</span></span><br /><br /> <span data-ttu-id="2029d-142">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="2029d-142">**Example**</span></span><br /><br /> `SqlServer.ATN2(9, 8)`|  
|<span data-ttu-id="2029d-143">`CEILING(` `expression` `)`</span><span class="sxs-lookup"><span data-stu-id="2029d-143">`CEILING(` `expression` `)`</span></span>|<span data-ttu-id="2029d-144">Převede zadaný výraz na nejmenší celé číslo, které je větší než nebo rovno ho.</span><span class="sxs-lookup"><span data-stu-id="2029d-144">Converts the specified expression to the smallest integer that is greater than or equal to it.</span></span><br /><br /> <span data-ttu-id="2029d-145">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="2029d-145">**Arguments**</span></span><br /><br /> <span data-ttu-id="2029d-146">`expression`: `Int32`, `Int64`, `Double`, Nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="2029d-146">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span><br /><br /> <span data-ttu-id="2029d-147">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="2029d-147">**Return Value**</span></span><br /><br /> <span data-ttu-id="2029d-148">`Int32`, `Int64`, `Double`, Nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="2029d-148">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span><br /><br /> <span data-ttu-id="2029d-149">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="2029d-149">**Example**</span></span><br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_CEILING](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_ceiling)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]|  
|<span data-ttu-id="2029d-150">`COS(` `expression` `)`</span><span class="sxs-lookup"><span data-stu-id="2029d-150">`COS(` `expression` `)`</span></span>|<span data-ttu-id="2029d-151">Vypočítá trigonometrické kosinus určeného úhlu v radiánech.</span><span class="sxs-lookup"><span data-stu-id="2029d-151">Calculates the trigonometric cosine of the specified angle in radians.</span></span><br /><br /> <span data-ttu-id="2029d-152">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="2029d-152">**Arguments**</span></span><br /><br /> <span data-ttu-id="2029d-153">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="2029d-153">`expression`: A `Double`.</span></span><br /><br /> <span data-ttu-id="2029d-154">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="2029d-154">**Return Value**</span></span><br /><br /> <span data-ttu-id="2029d-155">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="2029d-155">A `Double`.</span></span><br /><br /> <span data-ttu-id="2029d-156">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="2029d-156">**Example**</span></span><br /><br /> `SqlServer.COS(45)`|  
|<span data-ttu-id="2029d-157">`COT(` `expression` `)`</span><span class="sxs-lookup"><span data-stu-id="2029d-157">`COT(` `expression` `)`</span></span>|<span data-ttu-id="2029d-158">Vypočítá trigonometrické kotangens zadaný úhel v radiánech.</span><span class="sxs-lookup"><span data-stu-id="2029d-158">Calculates the trigonometric cotangent of the specified angle in radians.</span></span><br /><br /> <span data-ttu-id="2029d-159">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="2029d-159">**Arguments**</span></span><br /><br /> <span data-ttu-id="2029d-160">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="2029d-160">`expression`: A `Double`.</span></span><br /><br /> <span data-ttu-id="2029d-161">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="2029d-161">**Return Value**</span></span><br /><br /> <span data-ttu-id="2029d-162">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="2029d-162">A `Double`.</span></span><br /><br /> <span data-ttu-id="2029d-163">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="2029d-163">**Example**</span></span><br /><br /> `SqlServer.COT(60)`|  
|<span data-ttu-id="2029d-164">`DEGREES(` `radians` `)`</span><span class="sxs-lookup"><span data-stu-id="2029d-164">`DEGREES(` `radians` `)`</span></span>|<span data-ttu-id="2029d-165">Vrací odpovídající úhel ve stupních.</span><span class="sxs-lookup"><span data-stu-id="2029d-165">Returns the corresponding angle in degrees.</span></span><br /><br /> <span data-ttu-id="2029d-166">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="2029d-166">**Arguments**</span></span><br /><br /> <span data-ttu-id="2029d-167">`expression`: `Int32`, `Int64`, `Double`, Nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="2029d-167">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span><br /><br /> <span data-ttu-id="2029d-168">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="2029d-168">**Return Value**</span></span><br /><br /> <span data-ttu-id="2029d-169">`Int32`, `Int64`, `Double`, Nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="2029d-169">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span><br /><br /> <span data-ttu-id="2029d-170">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="2029d-170">**Example**</span></span><br /><br /> `SqlServer.DEGREES(3.1)`|  
|<span data-ttu-id="2029d-171">`EXP(` `expression` `)`</span><span class="sxs-lookup"><span data-stu-id="2029d-171">`EXP(` `expression` `)`</span></span>|<span data-ttu-id="2029d-172">Vypočítá exponenciální hodnotu zadaného číselného výrazu.</span><span class="sxs-lookup"><span data-stu-id="2029d-172">Calculates the exponential value of a specified numeric expression.</span></span><br /><br /> <span data-ttu-id="2029d-173">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="2029d-173">**Arguments**</span></span><br /><br /> <span data-ttu-id="2029d-174">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="2029d-174">`expression`: A `Double`.</span></span><br /><br /> <span data-ttu-id="2029d-175">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="2029d-175">**Return Value**</span></span><br /><br /> <span data-ttu-id="2029d-176">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="2029d-176">A `Double`.</span></span><br /><br /> <span data-ttu-id="2029d-177">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="2029d-177">**Example**</span></span><br /><br /> `SqlServer.EXP(1)`|  
|<span data-ttu-id="2029d-178">`FLOOR(` `expression` `)`</span><span class="sxs-lookup"><span data-stu-id="2029d-178">`FLOOR(` `expression` `)`</span></span>|<span data-ttu-id="2029d-179">Převede zadaný výraz největší celé číslo menší než nebo rovna k němu.</span><span class="sxs-lookup"><span data-stu-id="2029d-179">Converts the specified expression to the largest integer less than or equal to it.</span></span><br /><br /> <span data-ttu-id="2029d-180">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="2029d-180">**Arguments**</span></span><br /><br /> <span data-ttu-id="2029d-181">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="2029d-181">`expression`: A `Double`.</span></span><br /><br /> <span data-ttu-id="2029d-182">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="2029d-182">**Return Value**</span></span><br /><br /> <span data-ttu-id="2029d-183">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="2029d-183">A `Double`.</span></span><br /><br /> <span data-ttu-id="2029d-184">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="2029d-184">**Example**</span></span><br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_FLOOR](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_floor)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]|  
|<span data-ttu-id="2029d-185">`LOG(` `expression` `)`</span><span class="sxs-lookup"><span data-stu-id="2029d-185">`LOG(` `expression` `)`</span></span>|<span data-ttu-id="2029d-186">Vypočítá přirozený logaritmus zadaného `float` výraz.</span><span class="sxs-lookup"><span data-stu-id="2029d-186">Calculates the natural logarithm of the specified `float` expression.</span></span><br /><br /> <span data-ttu-id="2029d-187">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="2029d-187">**Arguments**</span></span><br /><br /> <span data-ttu-id="2029d-188">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="2029d-188">`expression`: A `Double`.</span></span><br /><br /> <span data-ttu-id="2029d-189">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="2029d-189">**Return Value**</span></span><br /><br /> <span data-ttu-id="2029d-190">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="2029d-190">A `Double`.</span></span><br /><br /> <span data-ttu-id="2029d-191">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="2029d-191">**Example**</span></span><br /><br /> `SqlServer.LOG(100)`|  
|<span data-ttu-id="2029d-192">`LOG10(` `expression` `)`</span><span class="sxs-lookup"><span data-stu-id="2029d-192">`LOG10(` `expression` `)`</span></span>|<span data-ttu-id="2029d-193">Vrátí logaritmus základu 10 zadaného `Double` výraz.</span><span class="sxs-lookup"><span data-stu-id="2029d-193">Returns the base-10 logarithm of the specified `Double` expression.</span></span><br /><br /> <span data-ttu-id="2029d-194">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="2029d-194">**Arguments**</span></span><br /><br /> <span data-ttu-id="2029d-195">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="2029d-195">`expression`: A `Double`.</span></span><br /><br /> <span data-ttu-id="2029d-196">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="2029d-196">**Return Value**</span></span><br /><br /> <span data-ttu-id="2029d-197">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="2029d-197">A `Double`.</span></span><br /><br /> <span data-ttu-id="2029d-198">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="2029d-198">**Example**</span></span><br /><br /> `SqlServer.LOG10(100)`|  
|`PI()`|<span data-ttu-id="2029d-199">Vrátí hodnotu čísla pí jako konstanty `Double`.</span><span class="sxs-lookup"><span data-stu-id="2029d-199">Returns the constant value of pi as a `Double`.</span></span><br /><br /> <span data-ttu-id="2029d-200">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="2029d-200">**Return Value**</span></span><br /><br /> <span data-ttu-id="2029d-201">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="2029d-201">A `Double`.</span></span><br /><br /> <span data-ttu-id="2029d-202">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="2029d-202">**Example**</span></span><br /><br /> `SqlServer.PI()`|  
|<span data-ttu-id="2029d-203">`POWER(` `numeric_expression, power_expression` `)`</span><span class="sxs-lookup"><span data-stu-id="2029d-203">`POWER(` `numeric_expression, power_expression` `)`</span></span>|<span data-ttu-id="2029d-204">Vypočítá hodnotu zadaného výrazu na zadanou mocninu.</span><span class="sxs-lookup"><span data-stu-id="2029d-204">Calculates the value of a specified expression to a specified power.</span></span><br /><br /> <span data-ttu-id="2029d-205">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="2029d-205">**Arguments**</span></span><br /><br /> <span data-ttu-id="2029d-206">`numeric_expression`: `Int32`, `Int64`, `Double`, Nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="2029d-206">`numeric_expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span><br /><br /> <span data-ttu-id="2029d-207">`power_expression`: A `Double` představující napájení, do kterého se mají zvýšit `numeric_expression`.</span><span class="sxs-lookup"><span data-stu-id="2029d-207">`power_expression`: A `Double` that represents the power to which to raise the `numeric_expression`.</span></span><br /><br /> <span data-ttu-id="2029d-208">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="2029d-208">**Return Value**</span></span><br /><br /> <span data-ttu-id="2029d-209">Hodnota zadaného `numeric_expression` do zadané `power_expression`.</span><span class="sxs-lookup"><span data-stu-id="2029d-209">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span><br /><br /> <span data-ttu-id="2029d-210">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="2029d-210">**Example**</span></span><br /><br /> `SqlServer.POWER(2,7)`|  
|<span data-ttu-id="2029d-211">`RADIANS(` `expression` `)`</span><span class="sxs-lookup"><span data-stu-id="2029d-211">`RADIANS(` `expression` `)`</span></span>|<span data-ttu-id="2029d-212">Převede radiánech stupňů.</span><span class="sxs-lookup"><span data-stu-id="2029d-212">Converts degrees to radians.</span></span><br /><br /> <span data-ttu-id="2029d-213">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="2029d-213">**Arguments**</span></span><br /><br /> <span data-ttu-id="2029d-214">`expression`: `Int32`, `Int64`, `Double`, Nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="2029d-214">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span><br /><br /> <span data-ttu-id="2029d-215">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="2029d-215">**Return Value**</span></span><br /><br /> <span data-ttu-id="2029d-216">`Int32`, `Int64`,</span><span class="sxs-lookup"><span data-stu-id="2029d-216">An `Int32`, `Int64`,</span></span><br /><br /> <span data-ttu-id="2029d-217">`Double`, nebo</span><span class="sxs-lookup"><span data-stu-id="2029d-217">`Double`, or</span></span><br /><br /> <span data-ttu-id="2029d-218">`Decimal`.</span><span class="sxs-lookup"><span data-stu-id="2029d-218">`Decimal`.</span></span><br /><br /> <span data-ttu-id="2029d-219">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="2029d-219">**Example**</span></span><br /><br /> `SqlServer.RADIANS(360.0)`|  
|<span data-ttu-id="2029d-220">`RAND(`[počáteční hodnoty]`)`</span><span class="sxs-lookup"><span data-stu-id="2029d-220">`RAND(`[seed]`)`</span></span>|<span data-ttu-id="2029d-221">Vrátí náhodné hodnotu od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="2029d-221">Returns a random value from 0 through 1.</span></span><br /><br /> <span data-ttu-id="2029d-222">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="2029d-222">**Arguments**</span></span><br /><br /> <span data-ttu-id="2029d-223">Hodnota Retruns počáteční hodnoty jako `Int32`.</span><span class="sxs-lookup"><span data-stu-id="2029d-223">Retruns the seed value as an `Int32`.</span></span> <span data-ttu-id="2029d-224">Pokud počáteční hodnotu nezadáte, přiřadí databázového stroje SQL Server v náhodných počáteční hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2029d-224">If the seed is not specified, the SQL Server Database Engine assigns a seed value at random.</span></span> <span data-ttu-id="2029d-225">Pro zadaný počáteční hodnoty výsledek vrácený je vždy stejný.</span><span class="sxs-lookup"><span data-stu-id="2029d-225">For a specified seed value, the result returned is always the same.</span></span><br /><br /> <span data-ttu-id="2029d-226">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="2029d-226">**Return Value**</span></span><br /><br /> <span data-ttu-id="2029d-227">Náhodnou `Double` hodnotu od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="2029d-227">A random `Double` value from 0 through 1.</span></span><br /><br /> <span data-ttu-id="2029d-228">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="2029d-228">**Example**</span></span><br /><br /> `SqlServer.RAND()`|  
|<span data-ttu-id="2029d-229">`ROUND(` `numeric_expression, length` [ ,`function` ]`)`</span><span class="sxs-lookup"><span data-stu-id="2029d-229">`ROUND(` `numeric_expression, length` [ ,`function` ]`)`</span></span>|<span data-ttu-id="2029d-230">Vrátí hodnotu číselného výrazu, zaokrouhlí se zadané délky nebo přesnosti.</span><span class="sxs-lookup"><span data-stu-id="2029d-230">Returns a numeric expression, rounded to the specified length or precision.</span></span><br /><br /> <span data-ttu-id="2029d-231">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="2029d-231">**Arguments**</span></span><br /><br /> <span data-ttu-id="2029d-232">`numeric_expression`: `Int32`, `Int64`, `Double`, Nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="2029d-232">`numeric_expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span><br /><br /> <span data-ttu-id="2029d-233">`length`: `Int32` Představující přesnost, ke kterému `numeric_expression` je má být zaokrouhleno.</span><span class="sxs-lookup"><span data-stu-id="2029d-233">`length`: An `Int32` that represents the precision to which `numeric_expression` is to be rounded.</span></span> <span data-ttu-id="2029d-234">Když `length` kladné číslo, `numeric_expression` se zaokrouhlí na počet desetinných pozic určeného `length`.</span><span class="sxs-lookup"><span data-stu-id="2029d-234">When `length` is a positive number, `numeric_expression` is rounded to the number of decimal positions specified by `length`.</span></span> <span data-ttu-id="2029d-235">Když `length` záporné číslo, `numeric_expression` se zaokrouhlí na levé straně od desetinné čárky, podle specifikace `length`.</span><span class="sxs-lookup"><span data-stu-id="2029d-235">When `length` is a negative number, `numeric_expression` is rounded on the left side of the decimal point, as specified by `length`.</span></span><br /><br /> <span data-ttu-id="2029d-236">`function`: (nepovinný) `Int32` , která představuje typ operaci provést.</span><span class="sxs-lookup"><span data-stu-id="2029d-236">`function`:(optional) An `Int32` that represents the type of operation to perform.</span></span> <span data-ttu-id="2029d-237">Když funkce je vynechán nebo má hodnotu 0 (výchozí), `numeric_expression` zaokrouhleno.</span><span class="sxs-lookup"><span data-stu-id="2029d-237">When function is omitted or has a value of 0 (default), `numeric_expression` is rounded.</span></span> <span data-ttu-id="2029d-238">Když jinou hodnotu než je zadána hodnota 0, `numeric_expression` se zkrátí.</span><span class="sxs-lookup"><span data-stu-id="2029d-238">When a value other than 0 is specified, `numeric_expression` is truncated.</span></span><br /><br /> <span data-ttu-id="2029d-239">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="2029d-239">**Return Value**</span></span><br /><br /> <span data-ttu-id="2029d-240">Hodnota zadaného `numeric_expression` do zadané `power_expression`.</span><span class="sxs-lookup"><span data-stu-id="2029d-240">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span><br /><br /> <span data-ttu-id="2029d-241">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="2029d-241">**Example**</span></span><br /><br /> `SqlServer.ROUND(748.58, -3)`|  
|<span data-ttu-id="2029d-242">`SIGN(` `expression` `)`</span><span class="sxs-lookup"><span data-stu-id="2029d-242">`SIGN(` `expression` `)`</span></span>|<span data-ttu-id="2029d-243">Vrátí kladnou (+ 1), nula (0) nebo záporné znaménko (-1), z určeného výrazu.</span><span class="sxs-lookup"><span data-stu-id="2029d-243">Returns the positive (+1), zero (0), or negative (-1) sign of the specified expression.</span></span><br /><br /> <span data-ttu-id="2029d-244">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="2029d-244">**Arguments**</span></span><br /><br /> <span data-ttu-id="2029d-245">`expression`: `Int32`, `Int64`, `Double`, nebo`Decimal`</span><span class="sxs-lookup"><span data-stu-id="2029d-245">`expression`: `Int32`, `Int64`, `Double`, or `Decimal`</span></span><br /><br /> <span data-ttu-id="2029d-246">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="2029d-246">**Return Value**</span></span><br /><br /> <span data-ttu-id="2029d-247">`Int32`, `Int64`, `Double`, Nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="2029d-247">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span><br /><br /> <span data-ttu-id="2029d-248">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="2029d-248">**Example**</span></span><br /><br /> `SqlServer.SIGN(-10)`|  
|<span data-ttu-id="2029d-249">`SIN(` `expression` `)`</span><span class="sxs-lookup"><span data-stu-id="2029d-249">`SIN(` `expression` `)`</span></span>|<span data-ttu-id="2029d-250">Vypočítá trigonometrické sinus určeného úhlu v radiánech a vrátí `Double` výraz.</span><span class="sxs-lookup"><span data-stu-id="2029d-250">Calculates the trigonometric sine of the specified angle in radians, and returns a `Double` expression.</span></span><br /><br /> <span data-ttu-id="2029d-251">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="2029d-251">**Arguments**</span></span><br /><br /> <span data-ttu-id="2029d-252">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="2029d-252">`expression`: A `Double`.</span></span><br /><br /> <span data-ttu-id="2029d-253">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="2029d-253">**Return Value**</span></span><br /><br /> <span data-ttu-id="2029d-254">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="2029d-254">A `Double`.</span></span><br /><br /> <span data-ttu-id="2029d-255">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="2029d-255">**Example**</span></span><br /><br /> `SqlServer.SIN(20)`|  
|<span data-ttu-id="2029d-256">`SQRT(` `expression` `)`</span><span class="sxs-lookup"><span data-stu-id="2029d-256">`SQRT(` `expression` `)`</span></span>|<span data-ttu-id="2029d-257">Vrátí druhou odmocninu, z určeného výrazu.</span><span class="sxs-lookup"><span data-stu-id="2029d-257">Returns the square root of the specified expression.</span></span><br /><br /> <span data-ttu-id="2029d-258">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="2029d-258">**Arguments**</span></span><br /><br /> <span data-ttu-id="2029d-259">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="2029d-259">`expression`: A `Double`.</span></span><br /><br /> <span data-ttu-id="2029d-260">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="2029d-260">**Return Value**</span></span><br /><br /> <span data-ttu-id="2029d-261">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="2029d-261">A `Double`.</span></span><br /><br /> <span data-ttu-id="2029d-262">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="2029d-262">**Example**</span></span><br /><br /> `SqlServer.SQRT(3600)`|  
|<span data-ttu-id="2029d-263">`SQUARE(` `expression` `)`</span><span class="sxs-lookup"><span data-stu-id="2029d-263">`SQUARE(` `expression` `)`</span></span>|<span data-ttu-id="2029d-264">Vrátí druhou, z určeného výrazu.</span><span class="sxs-lookup"><span data-stu-id="2029d-264">Returns the square of the specified expression.</span></span><br /><br /> <span data-ttu-id="2029d-265">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="2029d-265">**Arguments**</span></span><br /><br /> <span data-ttu-id="2029d-266">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="2029d-266">`expression`: A `Double`.</span></span><br /><br /> <span data-ttu-id="2029d-267">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="2029d-267">**Return Value**</span></span><br /><br /> <span data-ttu-id="2029d-268">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="2029d-268">A `Double`.</span></span><br /><br /> <span data-ttu-id="2029d-269">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="2029d-269">**Example**</span></span><br /><br /> `SqlServer.SQUARE(25)`|  
|<span data-ttu-id="2029d-270">`TAN(` `expression` `)`</span><span class="sxs-lookup"><span data-stu-id="2029d-270">`TAN(` `expression` `)`</span></span>|<span data-ttu-id="2029d-271">Vypočítá tangens zadaného výrazu.</span><span class="sxs-lookup"><span data-stu-id="2029d-271">Calculates the tangent of a specified expression.</span></span><br /><br /> <span data-ttu-id="2029d-272">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="2029d-272">**Arguments**</span></span><br /><br /> <span data-ttu-id="2029d-273">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="2029d-273">`expression`: `Double`</span></span><br /><br /> <span data-ttu-id="2029d-274">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="2029d-274">**Return Value**</span></span><br /><br /> `Double`<br /><br /> <span data-ttu-id="2029d-275">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="2029d-275">**Example**</span></span><br /><br /> `SqlServer.TAN(45.0)`|  
  
 <span data-ttu-id="2029d-276">Další informace o matematické funkce, které SqlClient podporuje najdete v dokumentaci pro používanou verzi systému SQL Server, který jste zadali v manifestu zprostředkovatele, SqlClient:</span><span class="sxs-lookup"><span data-stu-id="2029d-276">For more information about the mathematical functions that SqlClient supports, see the documentation for the SQL Server version that you specified in the SqlClient provider manifest:</span></span>  
  
|<span data-ttu-id="2029d-277">SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="2029d-277">SQL Server 2000</span></span>|<span data-ttu-id="2029d-278">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="2029d-278">SQL Server 2005</span></span>|<span data-ttu-id="2029d-279">SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="2029d-279">SQL Server 2008</span></span>|  
|---------------------|---------------------|---------------------|  
|[<span data-ttu-id="2029d-280">Matematické funkce (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="2029d-280">Mathematical Functions (Transact-SQL)</span></span>](http://go.microsoft.com/fwlink/?LinkId=115913)|[<span data-ttu-id="2029d-281">Matematické funkce (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="2029d-281">Mathematical Functions (Transact-SQL)</span></span>](http://go.microsoft.com/fwlink/?LinkId=115911)|[<span data-ttu-id="2029d-282">Matematické funkce (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="2029d-282">Mathematical Functions (Transact-SQL)</span></span>](http://go.microsoft.com/fwlink/?LinkId=115912)|  
  
## <a name="see-also"></a><span data-ttu-id="2029d-283">Viz také</span><span class="sxs-lookup"><span data-stu-id="2029d-283">See Also</span></span>  
 [<span data-ttu-id="2029d-284">SqlClient pro funkce Entity Framework</span><span class="sxs-lookup"><span data-stu-id="2029d-284">SqlClient for Entity Framework Functions</span></span>](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)