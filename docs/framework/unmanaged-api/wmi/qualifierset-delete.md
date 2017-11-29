---
title: "Funkce QualifierSet_Delete (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce QualifierSet_Delete odstraní kvalifikátor podle názvu."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_Delete
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_Delete
helpviewer_keywords: QualifierSet_Delete function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9245fc0ee109837249f1f3df400385c117a2f2d7
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2017
---
# <a name="qualifiersetdelete-function"></a><span data-ttu-id="ee9ee-103">QualifierSet_Delete – funkce</span><span class="sxs-lookup"><span data-stu-id="ee9ee-103">QualifierSet_Delete function</span></span>
<span data-ttu-id="ee9ee-104">Odstraní zadaný kvalifikátor podle názvu.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-104">Deletes a specified qualifier by name.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="ee9ee-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ee9ee-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName
); 
```  

## <a name="parameters"></a><span data-ttu-id="ee9ee-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ee9ee-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="ee9ee-107">[v] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="ee9ee-108">[v] Ukazatel na [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-108">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

`wszName`   
<span data-ttu-id="ee9ee-109">[v] Název kvalifikátor odstranit.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-109">[in] The name of the qualifier to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="ee9ee-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ee9ee-110">Return value</span></span>

<span data-ttu-id="ee9ee-111">Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="ee9ee-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="ee9ee-112">Konstanta</span><span class="sxs-lookup"><span data-stu-id="ee9ee-112">Constant</span></span>  |<span data-ttu-id="ee9ee-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ee9ee-113">Value</span></span>  |<span data-ttu-id="ee9ee-114">Popis</span><span class="sxs-lookup"><span data-stu-id="ee9ee-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="ee9ee-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="ee9ee-115">0x80041008</span></span> | <span data-ttu-id="ee9ee-116">`wszName` Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-116">The `wszName` parameter is not valid.</span></span> |
|`WBEM_E_INVALID_OPERATION` | <span data-ttu-id="ee9ee-117">0x80041016</span><span class="sxs-lookup"><span data-stu-id="ee9ee-117">0x80041016</span></span> | <span data-ttu-id="ee9ee-118">Odstranění této kvalifikátor je neplatný.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-118">Deleting this qualifier is illegal.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="ee9ee-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="ee9ee-119">0x80041002</span></span> | <span data-ttu-id="ee9ee-120">Nebyl nalezen zadaný kvalifikátor.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-120">The specified qualifier was not found.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="ee9ee-121">0</span><span class="sxs-lookup"><span data-stu-id="ee9ee-121">0</span></span> | <span data-ttu-id="ee9ee-122">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-122">The function call was successful.</span></span>  |
| `WBEM_S_RESET_TO_DEFAULT` | <span data-ttu-id="ee9ee-123">0x40002</span><span class="sxs-lookup"><span data-stu-id="ee9ee-123">0x40002</span></span> | <span data-ttu-id="ee9ee-124">Místní přepsání bylo odstraněno a původní kvalifikátor z nadřazeného objektu došlo k obnovení oboru.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-124">The local override was deleted and the original qualifier from the parent object has resumed scope.</span></span> |

## <a name="remarks"></a><span data-ttu-id="ee9ee-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ee9ee-125">Remarks</span></span>

<span data-ttu-id="ee9ee-126">Tato funkce zabalí volání [IWbemQualifierSet::Delete](https://msdn.microsoft.com/library/aa391864(v=vs.85).aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-126">This function wraps a call to the [IWbemQualifierSet::Delete](https://msdn.microsoft.com/library/aa391864(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="ee9ee-127">Z důvodu kvalifikátor šíření pravidla kvalifikátor konkrétní může byly zděděno z jiného objektu a jenom přepsání v aktuální třídě nebo instanci.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-127">Due to qualifier propagation rules, a particular qualifier may have been inherited from another object and merely overridden in the current class or instance.</span></span> <span data-ttu-id="ee9ee-128">V takovém případě `QualifierSet_Delete` metoda obnoví kvalifikátor na jeho původní zděděná hodnota.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-128">In this case, the `QualifierSet_Delete` method resets the qualifier to its original inherited value.</span></span> <span data-ttu-id="ee9ee-129">Funkce v tomto případě vrátí stavový kód `WBEM_S_RESET_TO_DEFAULT`.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-129">The function in this case returns the status code `WBEM_S_RESET_TO_DEFAULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="ee9ee-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ee9ee-130">Requirements</span></span>  
 <span data-ttu-id="ee9ee-131">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee9ee-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee9ee-132">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="ee9ee-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="ee9ee-133">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ee9ee-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee9ee-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="ee9ee-134">See also</span></span>  
[<span data-ttu-id="ee9ee-135">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="ee9ee-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)