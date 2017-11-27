---
title: "Kanonické funkce řetězce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e2cbebd-5df3-47c7-b0e2-49a17ab22bfb
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 55d139fe4a1448f1f9f4739421a90b4dc8729489
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="string-canonical-functions"></a><span data-ttu-id="18d01-102">Kanonické funkce řetězce</span><span class="sxs-lookup"><span data-stu-id="18d01-102">String Canonical Functions</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="18d01-103">zahrnuje kanonické funkce řetězec.</span><span class="sxs-lookup"><span data-stu-id="18d01-103"> includes string canonical functions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18d01-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="18d01-104">Remarks</span></span>  
 <span data-ttu-id="18d01-105">V následující tabulce jsou uvedeny řetězec [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="18d01-105">The following table shows the string [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
|<span data-ttu-id="18d01-106">Funkce</span><span class="sxs-lookup"><span data-stu-id="18d01-106">Function</span></span>|<span data-ttu-id="18d01-107">Popis</span><span class="sxs-lookup"><span data-stu-id="18d01-107">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="18d01-108">`Concat (` `string1`, `string2``)`</span><span class="sxs-lookup"><span data-stu-id="18d01-108">`Concat (` `string1`, `string2``)`</span></span>|<span data-ttu-id="18d01-109">Vrátí řetězec, který obsahuje `string2` připojenou k `string1`.</span><span class="sxs-lookup"><span data-stu-id="18d01-109">Returns a string that contains `string2` appended to `string1`.</span></span><br /><br /> <span data-ttu-id="18d01-110">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="18d01-110">**Arguments**</span></span><br /><br /> <span data-ttu-id="18d01-111">`string1`: Řetězec, který `string2` se připojí.</span><span class="sxs-lookup"><span data-stu-id="18d01-111">`string1`: The string to which `string2` is appended.</span></span><br /><br /> <span data-ttu-id="18d01-112">`string2`: Řetězec, který se připojí k `string1`.</span><span class="sxs-lookup"><span data-stu-id="18d01-112">`string2`: The string that is appended to `string1`.</span></span><br /><br /> <span data-ttu-id="18d01-113">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="18d01-113">**Return Value**</span></span><br /><br /> <span data-ttu-id="18d01-114">A `String`.</span><span class="sxs-lookup"><span data-stu-id="18d01-114">A `String`.</span></span> <span data-ttu-id="18d01-115">Pokud je délka řetězce návratovou hodnotu větší než maximální povolenou délku, dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="18d01-115">An error will occur if the length of the return value string is greater than the maximum length allowed.</span></span><br /><br /> <span data-ttu-id="18d01-116">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="18d01-116">**Example**</span></span><br /><br /> `-- The following example returns abcxyz.`<br /><br /> `Concat('abc', 'xyz')`|  
|<span data-ttu-id="18d01-117">`Contains (` `string`, `target``)`</span><span class="sxs-lookup"><span data-stu-id="18d01-117">`Contains (` `string`, `target``)`</span></span>|<span data-ttu-id="18d01-118">Vrátí `true` Pokud `target` je součástí `string`.</span><span class="sxs-lookup"><span data-stu-id="18d01-118">Returns `true` if `target` is contained in `string`.</span></span><br /><br /> <span data-ttu-id="18d01-119">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="18d01-119">**Arguments**</span></span><br /><br /> <span data-ttu-id="18d01-120">`string`: Řetězec, který je vyhledán.</span><span class="sxs-lookup"><span data-stu-id="18d01-120">`string`: The string that is searched.</span></span><br /><br /> <span data-ttu-id="18d01-121">`target`: Cílový řetězec, který je hledán.</span><span class="sxs-lookup"><span data-stu-id="18d01-121">`target`: The target string that is searched for.</span></span><br /><br /> <span data-ttu-id="18d01-122">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="18d01-122">**Return Value**</span></span><br /><br /> <span data-ttu-id="18d01-123">`true`Pokud `target` je součástí `string`jinak `false`.</span><span class="sxs-lookup"><span data-stu-id="18d01-123">`true` if `target` is contained in `string`; otherwise `false`.</span></span><br /><br /> <span data-ttu-id="18d01-124">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="18d01-124">**Example**</span></span><br /><br /> `-- The following example returns true.`<br /><br /> `Contains('abc', 'bc')`|  
|<span data-ttu-id="18d01-125">`EndsWith (` `string`, `target``)`</span><span class="sxs-lookup"><span data-stu-id="18d01-125">`EndsWith (` `string`, `target``)`</span></span>|<span data-ttu-id="18d01-126">Vrátí `true` Pokud `target` končí `string`.</span><span class="sxs-lookup"><span data-stu-id="18d01-126">Returns `true` if `target` ends with `string`.</span></span><br /><br /> <span data-ttu-id="18d01-127">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="18d01-127">**Arguments**</span></span><br /><br /> <span data-ttu-id="18d01-128">`string`: Řetězec, který je vyhledán.</span><span class="sxs-lookup"><span data-stu-id="18d01-128">`string`: The string that is searched.</span></span><br /><br /> <span data-ttu-id="18d01-129">`target`: Cílový řetězec vyhledávat na konci `string`.</span><span class="sxs-lookup"><span data-stu-id="18d01-129">`target`: The target string searched for at the end of `string`.</span></span><br /><br /> <span data-ttu-id="18d01-130">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="18d01-130">**Return Value**</span></span><br /><br /> <span data-ttu-id="18d01-131">`True`Pokud `string` končí `target`jinak `false`.</span><span class="sxs-lookup"><span data-stu-id="18d01-131">`True` if `string` ends with `target`; otherwise `false`.</span></span><br /><br /> <span data-ttu-id="18d01-132">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="18d01-132">**Example**</span></span><br /><br /> `-- The following example returns true.`<br /><br /> <span data-ttu-id="18d01-133">`EndsWith('abc', 'bc')`**Poznámka:** Pokud používáte [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] zprostředkovatele dat, funkce vrátí hodnotu `false` Pokud řetězec uložený ve sloupci řetězec pevnou délkou a `target` konstanta.</span><span class="sxs-lookup"><span data-stu-id="18d01-133">`EndsWith('abc', 'bc')` **Note:**  If you are using the [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] data provider, this function returns `false` if the string is stored in a fixed length string column and `target` is a constant.</span></span> <span data-ttu-id="18d01-134">V takovém případě je prohledána celý řetězec, včetně všech odsazení koncové mezery.</span><span class="sxs-lookup"><span data-stu-id="18d01-134">In this case, the entire string is searched, including any padding trailing spaces.</span></span> <span data-ttu-id="18d01-135">Možným řešením je oříznout data v řetězce pevné délky, jako v následujícím příkladu:`EndsWith(TRIM(string), target)`</span><span class="sxs-lookup"><span data-stu-id="18d01-135">A possible workaround is to trim the data in the fixed length string, as in the following example: `EndsWith(TRIM(string), target)`</span></span>|  
|<span data-ttu-id="18d01-136">`IndexOf(` `target`, `string``)`</span><span class="sxs-lookup"><span data-stu-id="18d01-136">`IndexOf(` `target`, `string``)`</span></span>|<span data-ttu-id="18d01-137">Vrátí pozici `target` uvnitř `string`, nebo 0, pokud není nalezena.</span><span class="sxs-lookup"><span data-stu-id="18d01-137">Returns the position of `target` inside `string`, or 0 if not found.</span></span> <span data-ttu-id="18d01-138">Vrátí hodnotu 1 označující začátek `string`.</span><span class="sxs-lookup"><span data-stu-id="18d01-138">Returns 1 to indicate the beginning of `string`.</span></span> <span data-ttu-id="18d01-139">Index číslování spustí od 1.</span><span class="sxs-lookup"><span data-stu-id="18d01-139">Index numbering starts from 1.</span></span><br /><br /> <span data-ttu-id="18d01-140">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="18d01-140">**Arguments**</span></span><br /><br /> <span data-ttu-id="18d01-141">`target`: Řetězec, který je hledán.</span><span class="sxs-lookup"><span data-stu-id="18d01-141">`target`: The string that is searched for.</span></span><br /><br /> <span data-ttu-id="18d01-142">`string`: Řetězec, který je vyhledán.</span><span class="sxs-lookup"><span data-stu-id="18d01-142">`string`: The string that is searched.</span></span><br /><br /> <span data-ttu-id="18d01-143">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="18d01-143">**Return Value**</span></span><br /><br /> <span data-ttu-id="18d01-144">`Int32`.</span><span class="sxs-lookup"><span data-stu-id="18d01-144">An `Int32`.</span></span><br /><br /> <span data-ttu-id="18d01-145">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="18d01-145">**Example**</span></span><br /><br /> `-- The following example returns 4.`<br /><br /> `IndexOf('xyz', 'abcxyz')`|  
|<span data-ttu-id="18d01-146">`Left (` `string`, `length``)`</span><span class="sxs-lookup"><span data-stu-id="18d01-146">`Left (` `string`, `length``)`</span></span>|<span data-ttu-id="18d01-147">Vrátí první `length` znaků od levé straně `string`.</span><span class="sxs-lookup"><span data-stu-id="18d01-147">Returns the first `length` characters from the left side of `string`.</span></span> <span data-ttu-id="18d01-148">Pokud délka `string` je menší než `length`, bude vrácen celý řetězec.</span><span class="sxs-lookup"><span data-stu-id="18d01-148">If the length of `string` is less than `length`, the entire string is returned.</span></span><br /><br /> <span data-ttu-id="18d01-149">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="18d01-149">**Arguments**</span></span><br /><br /> <span data-ttu-id="18d01-150">`string`: A `String`.</span><span class="sxs-lookup"><span data-stu-id="18d01-150">`string`: A `String`.</span></span><br /><br /> <span data-ttu-id="18d01-151">`length`: `Int16`, `Int32`, `Int64`, Nebo `Byte`.</span><span class="sxs-lookup"><span data-stu-id="18d01-151">`length`: An `Int16`, `Int32`, `Int64`, or `Byte`.</span></span> <span data-ttu-id="18d01-152">`length`nesmí být menší než nula.</span><span class="sxs-lookup"><span data-stu-id="18d01-152">`length` cannot be less than zero.</span></span><br /><br /> <span data-ttu-id="18d01-153">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="18d01-153">**Return Value**</span></span><br /><br /> <span data-ttu-id="18d01-154">A `String`.</span><span class="sxs-lookup"><span data-stu-id="18d01-154">A `String`.</span></span><br /><br /> <span data-ttu-id="18d01-155">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="18d01-155">**Example**</span></span><br /><br /> `-- The following example returns abc.`<br /><br /> `Left('abcxyz', 3)`|  
|<span data-ttu-id="18d01-156">`Length (` `string` `)`</span><span class="sxs-lookup"><span data-stu-id="18d01-156">`Length (` `string` `)`</span></span>|<span data-ttu-id="18d01-157">Vrátí (`Int32`) délka ve znacích řetězce.</span><span class="sxs-lookup"><span data-stu-id="18d01-157">Returns the (`Int32`) length, in characters, of the string.</span></span><br /><br /> <span data-ttu-id="18d01-158">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="18d01-158">**Arguments**</span></span><br /><br /> <span data-ttu-id="18d01-159">`string`: A `String`.</span><span class="sxs-lookup"><span data-stu-id="18d01-159">`string`: A `String`.</span></span><br /><br /> <span data-ttu-id="18d01-160">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="18d01-160">**Return Value**</span></span><br /><br /> <span data-ttu-id="18d01-161">`Int32`.</span><span class="sxs-lookup"><span data-stu-id="18d01-161">An `Int32`.</span></span><br /><br /> <span data-ttu-id="18d01-162">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="18d01-162">**Example**</span></span><br /><br /> `-- The following example returns 6.`<br /><br /> `Legth('abcxyz')`|  
|<span data-ttu-id="18d01-163">`LTrim(` `string` `)`</span><span class="sxs-lookup"><span data-stu-id="18d01-163">`LTrim(` `string` `)`</span></span>|<span data-ttu-id="18d01-164">Vrátí `string` bez úvodní mezery.</span><span class="sxs-lookup"><span data-stu-id="18d01-164">Returns `string` without leading whitespace.</span></span><br /><br /> <span data-ttu-id="18d01-165">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="18d01-165">**Arguments**</span></span><br /><br /> <span data-ttu-id="18d01-166">A `String`.</span><span class="sxs-lookup"><span data-stu-id="18d01-166">A `String`.</span></span><br /><br /> <span data-ttu-id="18d01-167">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="18d01-167">**Return Value**</span></span><br /><br /> <span data-ttu-id="18d01-168">A `String`.</span><span class="sxs-lookup"><span data-stu-id="18d01-168">A `String`.</span></span><br /><br /> <span data-ttu-id="18d01-169">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="18d01-169">**Example**</span></span><br /><br /> `-- The following example returns abc.`<br /><br /> `LTrim('   abc')`|  
|<span data-ttu-id="18d01-170">`Replace (` `string1`, `string2`, `string3``)`</span><span class="sxs-lookup"><span data-stu-id="18d01-170">`Replace (` `string1`, `string2`, `string3``)`</span></span>|<span data-ttu-id="18d01-171">Vrátí `string1`, se všechny výskyty `string2` nahrazuje `string3`.</span><span class="sxs-lookup"><span data-stu-id="18d01-171">Returns `string1`, with all occurrences of `string2` replaced by `string3`.</span></span><br /><br /> <span data-ttu-id="18d01-172">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="18d01-172">**Arguments**</span></span><br /><br /> <span data-ttu-id="18d01-173">A `String`.</span><span class="sxs-lookup"><span data-stu-id="18d01-173">A `String`.</span></span><br /><br /> <span data-ttu-id="18d01-174">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="18d01-174">**Return Value**</span></span><br /><br /> <span data-ttu-id="18d01-175">A `String`.</span><span class="sxs-lookup"><span data-stu-id="18d01-175">A `String`.</span></span><br /><br /> <span data-ttu-id="18d01-176">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="18d01-176">**Example**</span></span><br /><br /> `-- The following example returns abcxyz.`<br /><br /> `Concat('abc', 'xyz')`|  
|<span data-ttu-id="18d01-177">`Reverse (` `string` `)`</span><span class="sxs-lookup"><span data-stu-id="18d01-177">`Reverse (` `string` `)`</span></span>|<span data-ttu-id="18d01-178">Vrátí `string` s pořadím znaky vrátit zpět.</span><span class="sxs-lookup"><span data-stu-id="18d01-178">Returns `string` with the order of the characters reversed.</span></span><br /><br /> <span data-ttu-id="18d01-179">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="18d01-179">**Arguments**</span></span><br /><br /> <span data-ttu-id="18d01-180">A `String`.</span><span class="sxs-lookup"><span data-stu-id="18d01-180">A `String`.</span></span><br /><br /> <span data-ttu-id="18d01-181">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="18d01-181">**Return Value**</span></span><br /><br /> <span data-ttu-id="18d01-182">A `String`.</span><span class="sxs-lookup"><span data-stu-id="18d01-182">A `String`.</span></span><br /><br /> <span data-ttu-id="18d01-183">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="18d01-183">**Example**</span></span><br /><br /> `-- The following example returns dcba.`<br /><br /> `Reverse('abcd')`|  
|<span data-ttu-id="18d01-184">`Right (` `string`, `length``)`</span><span class="sxs-lookup"><span data-stu-id="18d01-184">`Right (` `string`, `length``)`</span></span>|<span data-ttu-id="18d01-185">Vrátí poslední `length` znaků z `string`.</span><span class="sxs-lookup"><span data-stu-id="18d01-185">Returns the last `length` characters from the `string`.</span></span> <span data-ttu-id="18d01-186">Pokud délka `string` je menší než `length`, bude vrácen celý řetězec.</span><span class="sxs-lookup"><span data-stu-id="18d01-186">If the length of `string` is less than `length`, the entire string is returned.</span></span><br /><br /> <span data-ttu-id="18d01-187">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="18d01-187">**Arguments**</span></span><br /><br /> <span data-ttu-id="18d01-188">`string`: A `String`.</span><span class="sxs-lookup"><span data-stu-id="18d01-188">`string`: A `String`.</span></span><br /><br /> <span data-ttu-id="18d01-189">`length`: `Int16`, `Int32`, `Int64`, Nebo `Byte`.</span><span class="sxs-lookup"><span data-stu-id="18d01-189">`length`: An `Int16`, `Int32`, `Int64`, or `Byte`.</span></span> <span data-ttu-id="18d01-190">`length`nesmí být menší než nula.</span><span class="sxs-lookup"><span data-stu-id="18d01-190">`length` cannot be less than zero.</span></span><br /><br /> <span data-ttu-id="18d01-191">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="18d01-191">**Return Value**</span></span><br /><br /> <span data-ttu-id="18d01-192">A `String`.</span><span class="sxs-lookup"><span data-stu-id="18d01-192">A `String`.</span></span><br /><br /> <span data-ttu-id="18d01-193">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="18d01-193">**Example**</span></span><br /><br /> `-- The following example returns xyz.`<br /><br /> `Right('abcxyz', 3)`|  
|<span data-ttu-id="18d01-194">`RTrim(` `string` `)`</span><span class="sxs-lookup"><span data-stu-id="18d01-194">`RTrim(` `string` `)`</span></span>|<span data-ttu-id="18d01-195">Vrátí `string` bez koncové mezery.</span><span class="sxs-lookup"><span data-stu-id="18d01-195">Returns `string` without trailing whitespace.</span></span><br /><br /> <span data-ttu-id="18d01-196">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="18d01-196">**Arguments**</span></span><br /><br /> <span data-ttu-id="18d01-197">A `String`.</span><span class="sxs-lookup"><span data-stu-id="18d01-197">A `String`.</span></span><br /><br /> <span data-ttu-id="18d01-198">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="18d01-198">**Return Value**</span></span><br /><br /> <span data-ttu-id="18d01-199">A `String`.</span><span class="sxs-lookup"><span data-stu-id="18d01-199">A `String`.</span></span>|  
|<span data-ttu-id="18d01-200">`Substring (` `string`, `start`, `length``)`</span><span class="sxs-lookup"><span data-stu-id="18d01-200">`Substring (` `string`, `start`, `length``)`</span></span>|<span data-ttu-id="18d01-201">Vrátí dílčí řetězec řetězce začínající na pozici `start`, s délkou `length` znaků.</span><span class="sxs-lookup"><span data-stu-id="18d01-201">Returns the substring of the string starting at position `start`, with a length of `length` characters.</span></span> <span data-ttu-id="18d01-202">Začátek 1 určuje první znak řetězce.</span><span class="sxs-lookup"><span data-stu-id="18d01-202">A start of 1 indicates the first character of the string.</span></span> <span data-ttu-id="18d01-203">Index číslování spustí od 1.</span><span class="sxs-lookup"><span data-stu-id="18d01-203">Index numbering starts from 1.</span></span><br /><br /> <span data-ttu-id="18d01-204">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="18d01-204">**Arguments**</span></span><br /><br /> <span data-ttu-id="18d01-205">`string`: A `String`.</span><span class="sxs-lookup"><span data-stu-id="18d01-205">`string`: A `String`.</span></span><br /><br /> <span data-ttu-id="18d01-206">`start`: `Int16`, `Int32`, `Int64` a `Byte`.</span><span class="sxs-lookup"><span data-stu-id="18d01-206">`start`: An `Int16`, `Int32`, `Int64` and `Byte`.</span></span> <span data-ttu-id="18d01-207">`start`nemůže být nižší než jednou.</span><span class="sxs-lookup"><span data-stu-id="18d01-207">`start` cannot be less than one.</span></span><br /><br /> <span data-ttu-id="18d01-208">`length`: `Int16`, `Int32`, `Int64` a `Byte`.</span><span class="sxs-lookup"><span data-stu-id="18d01-208">`length`: An `Int16`, `Int32`, `Int64` and `Byte`.</span></span> <span data-ttu-id="18d01-209">`length`nesmí být menší než nula.</span><span class="sxs-lookup"><span data-stu-id="18d01-209">`length` cannot be less than zero.</span></span><br /><br /> <span data-ttu-id="18d01-210">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="18d01-210">**Return Value**</span></span><br /><br /> <span data-ttu-id="18d01-211">A `String`.</span><span class="sxs-lookup"><span data-stu-id="18d01-211">A `String`.</span></span><br /><br /> <span data-ttu-id="18d01-212">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="18d01-212">**Example**</span></span><br /><br /> `-- The following example returns xyz.`<br /><br /> `Substring('abcxyz', 4, 3)`|  
|<span data-ttu-id="18d01-213">`StartsWith (` `string`, `target``)`</span><span class="sxs-lookup"><span data-stu-id="18d01-213">`StartsWith (` `string`, `target``)`</span></span>|<span data-ttu-id="18d01-214">Vrátí `true` Pokud `string` začíná `target`.</span><span class="sxs-lookup"><span data-stu-id="18d01-214">Returns `true` if `string` starts with `target`.</span></span><br /><br /> <span data-ttu-id="18d01-215">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="18d01-215">**Arguments**</span></span><br /><br /> <span data-ttu-id="18d01-216">`string`: Řetězec, který je vyhledán.</span><span class="sxs-lookup"><span data-stu-id="18d01-216">`string`: The string that is searched.</span></span><br /><br /> <span data-ttu-id="18d01-217">`target`: Cílový řetězec vyhledávat na začátku `string`.</span><span class="sxs-lookup"><span data-stu-id="18d01-217">`target`: The target string searched for at the start of `string`.</span></span><br /><br /> <span data-ttu-id="18d01-218">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="18d01-218">**Return Value**</span></span><br /><br /> <span data-ttu-id="18d01-219">`True`Pokud `string` začíná `target`jinak `false`.</span><span class="sxs-lookup"><span data-stu-id="18d01-219">`True` if `string` starts with `target`; otherwise `false`.</span></span><br /><br /> <span data-ttu-id="18d01-220">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="18d01-220">**Example**</span></span><br /><br /> `-- The following example returns true.`<br /><br /> `StartsWith('abc', 'ab')`|  
|<span data-ttu-id="18d01-221">`ToLower(` `string` `)`</span><span class="sxs-lookup"><span data-stu-id="18d01-221">`ToLower(` `string` `)`</span></span>|<span data-ttu-id="18d01-222">Vrátí `string` s převeden na malá písmena velká písmena.</span><span class="sxs-lookup"><span data-stu-id="18d01-222">Returns `string` with uppercase characters converted to lowercase.</span></span><br /><br /> <span data-ttu-id="18d01-223">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="18d01-223">**Arguments**</span></span><br /><br /> <span data-ttu-id="18d01-224">A `String`.</span><span class="sxs-lookup"><span data-stu-id="18d01-224">A `String`.</span></span><br /><br /> <span data-ttu-id="18d01-225">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="18d01-225">**Return Value**</span></span><br /><br /> <span data-ttu-id="18d01-226">A `String`.</span><span class="sxs-lookup"><span data-stu-id="18d01-226">A `String`.</span></span><br /><br /> <span data-ttu-id="18d01-227">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="18d01-227">**Example**</span></span><br /><br /> `-- The following example returns abc.`<br /><br /> `ToLower('ABC')`|  
|<span data-ttu-id="18d01-228">`ToUpper(` `string` `)`</span><span class="sxs-lookup"><span data-stu-id="18d01-228">`ToUpper(` `string` `)`</span></span>|<span data-ttu-id="18d01-229">Vrátí `string` s malá písmena převeden na velká písmena.</span><span class="sxs-lookup"><span data-stu-id="18d01-229">Returns `string` with lowercase characters converted to uppercase.</span></span><br /><br /> <span data-ttu-id="18d01-230">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="18d01-230">**Arguments**</span></span><br /><br /> <span data-ttu-id="18d01-231">A `String`.</span><span class="sxs-lookup"><span data-stu-id="18d01-231">A `String`.</span></span><br /><br /> <span data-ttu-id="18d01-232">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="18d01-232">**Return Value**</span></span><br /><br /> <span data-ttu-id="18d01-233">A `String`.</span><span class="sxs-lookup"><span data-stu-id="18d01-233">A `String`.</span></span><br /><br /> <span data-ttu-id="18d01-234">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="18d01-234">**Example**</span></span><br /><br /> `-- The following example returns ABC.`<br /><br /> `ToUpper('abc')`|  
|<span data-ttu-id="18d01-235">`Trim(` `string` `)`</span><span class="sxs-lookup"><span data-stu-id="18d01-235">`Trim(` `string` `)`</span></span>|<span data-ttu-id="18d01-236">Vrátí `string` bez úvodní a koncové mezery.</span><span class="sxs-lookup"><span data-stu-id="18d01-236">Returns `string` without leading and trailing whitespace.</span></span><br /><br /> <span data-ttu-id="18d01-237">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="18d01-237">**Arguments**</span></span><br /><br /> <span data-ttu-id="18d01-238">A `String`.</span><span class="sxs-lookup"><span data-stu-id="18d01-238">A `String`.</span></span><br /><br /> <span data-ttu-id="18d01-239">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="18d01-239">**Return Value**</span></span><br /><br /> <span data-ttu-id="18d01-240">A `String`.</span><span class="sxs-lookup"><span data-stu-id="18d01-240">A `String`.</span></span><br /><br /> <span data-ttu-id="18d01-241">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="18d01-241">**Example**</span></span><br /><br /> `-- The following example returns abc.`<br /><br /> `Trim('      abc   ')`|  
  
 <span data-ttu-id="18d01-242">Vrátí tyto funkce `null` -li zadány `null` vstupní.</span><span class="sxs-lookup"><span data-stu-id="18d01-242">These functions will return `null` if given `null` input.</span></span>  
  
 <span data-ttu-id="18d01-243">Ekvivalentní funkce je k dispozici ve zprostředkovateli spravované klienta Microsoft SQL.</span><span class="sxs-lookup"><span data-stu-id="18d01-243">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="18d01-244">Další informace najdete v tématu [SqlClient pro funkce Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="18d01-244">For more information, see [SqlClient for Entity Framework Functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18d01-245">Viz také</span><span class="sxs-lookup"><span data-stu-id="18d01-245">See Also</span></span>  
 [<span data-ttu-id="18d01-246">Kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="18d01-246">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)