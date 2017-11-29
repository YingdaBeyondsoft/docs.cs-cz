---
title: "Funkce GetPropertyQualifierSet (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce GetPropertyQualifierSet načte kvalifikátor nastavená pro vlastnost."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetPropertyQualifierSet
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetPropertyQualifierSet
helpviewer_keywords: GetPropertyQualifierSet function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bd8abdb34f37273e469bdf5fc659b261bb2b9304
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2017
---
# <a name="getpropertyqualifierset-function"></a><span data-ttu-id="5a133-103">GetPropertyQualifierSet – funkce</span><span class="sxs-lookup"><span data-stu-id="5a133-103">GetPropertyQualifierSet function</span></span>
<span data-ttu-id="5a133-104">Načte kvalifikátor nastavit určité vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5a133-104">Retrieves the qualifier set for a particular property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="5a133-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a133-105">Syntax</span></span>  
  
```  
HRESULT GetPropertyQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszProperty,
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a><span data-ttu-id="5a133-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5a133-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="5a133-107">[v] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="5a133-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="5a133-108">[v] Ukazatel na [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="5a133-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszMethod`  
<span data-ttu-id="5a133-109">[v] Název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5a133-109">[in] The property  name.</span></span> <span data-ttu-id="5a133-110">`wszProperty`musí odkazovat na platný `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="5a133-110">`wszProperty` must point to a valid `LPCWSTR`.</span></span> 

`ppQualSet`  
<span data-ttu-id="5a133-111">[out] Ukazatel rozhraní, které umožňuje přístup k kvalifikátory vlastnosti obdrží.</span><span class="sxs-lookup"><span data-stu-id="5a133-111">[out] Receives the interface pointer that allows access to the qualifiers of the property.</span></span> <span data-ttu-id="5a133-112">`ppQualSet`nemůže být `null`.</span><span class="sxs-lookup"><span data-stu-id="5a133-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="5a133-113">Pokud dojde k chybě, nevrátí nový objekt a ukazatel je nastaven tak, aby odkazoval na `null`.</span><span class="sxs-lookup"><span data-stu-id="5a133-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="5a133-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5a133-114">Return value</span></span>

<span data-ttu-id="5a133-115">Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="5a133-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="5a133-116">Konstanta</span><span class="sxs-lookup"><span data-stu-id="5a133-116">Constant</span></span>  |<span data-ttu-id="5a133-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5a133-117">Value</span></span>  |<span data-ttu-id="5a133-118">Popis</span><span class="sxs-lookup"><span data-stu-id="5a133-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="5a133-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="5a133-119">0x80041001</span></span> | <span data-ttu-id="5a133-120">Došlo k obecné chybě.</span><span class="sxs-lookup"><span data-stu-id="5a133-120">There has been a general failure.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="5a133-121">0x80041002</span><span class="sxs-lookup"><span data-stu-id="5a133-121">0x80041002</span></span> | <span data-ttu-id="5a133-122">Zadaná metoda neexistuje.</span><span class="sxs-lookup"><span data-stu-id="5a133-122">The specified method does not exist.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="5a133-123">0x80041006</span><span class="sxs-lookup"><span data-stu-id="5a133-123">0x80041006</span></span> | <span data-ttu-id="5a133-124">Je k dispozici k dokončení operace není dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="5a133-124">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="5a133-125">0x80041008</span><span class="sxs-lookup"><span data-stu-id="5a133-125">0x80041008</span></span> | <span data-ttu-id="5a133-126">Parametr je `null`.</span><span class="sxs-lookup"><span data-stu-id="5a133-126">A parameter is `null`.</span></span> |
| `WBEM_E_SYSTEM_PROPERTY` | <span data-ttu-id="5a133-127">0x80041030</span><span class="sxs-lookup"><span data-stu-id="5a133-127">0x80041030</span></span> | <span data-ttu-id="5a133-128">Funkce, pokusí se získat kvalifikátory vlastnosti systému.</span><span class="sxs-lookup"><span data-stu-id="5a133-128">The function attempts to get qualifiers of a system property.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="5a133-129">0</span><span class="sxs-lookup"><span data-stu-id="5a133-129">0</span></span> | <span data-ttu-id="5a133-130">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="5a133-130">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="5a133-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5a133-131">Remarks</span></span>

<span data-ttu-id="5a133-132">Tato funkce zabalí volání [IWbemClassObject::GetPropertyQualifierSet](https://msdn.microsoft.com/library/aa391450(v=vs.85).aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="5a133-132">This function wraps a call to the [IWbemClassObject::GetPropertyQualifierSet](https://msdn.microsoft.com/library/aa391450(v=vs.85).aspx) method.</span></span> 

<span data-ttu-id="5a133-133">Volání této funkce je podporována pouze v případě, že je aktuální objekt definice třídy CIM.</span><span class="sxs-lookup"><span data-stu-id="5a133-133">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="5a133-134">Není k dispozici pro manipulaci s metoda [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) ponters, které odkazují na modelu CIM instancí.</span><span class="sxs-lookup"><span data-stu-id="5a133-134">Method manipulation is not available for [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) ponters that point to CIM instances.</span></span>

<span data-ttu-id="5a133-135">Protože každá metoda může mít svůj vlastní kvalifikátory [IWbemQualifierSet ukazatel](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) umožňuje přidat, upravit nebo odstranit tyto kvalifikátory volající.</span><span class="sxs-lookup"><span data-stu-id="5a133-135">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) lets the caller add, edit, or delete these qualifiers.</span></span>

<span data-ttu-id="5a133-136">Vzhledem k tomu, že vlastnosti systému žádné kvalifikátory, funkce vrátí hodnotu `WBEM_E_SYSTEM_PROPERTY` když se pokusí získat [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) ukazatele pro vlastnost systému.</span><span class="sxs-lookup"><span data-stu-id="5a133-136">Because system properties have no qualifiers, the function returns `WBEM_E_SYSTEM_PROPERTY` if you attempt to obtain a [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) pointer for a system property.</span></span>

## <a name="requirements"></a><span data-ttu-id="5a133-137">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5a133-137">Requirements</span></span>  
<span data-ttu-id="5a133-138">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a133-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a133-139">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="5a133-139">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="5a133-140">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5a133-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a133-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a133-141">See also</span></span>  
[<span data-ttu-id="5a133-142">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="5a133-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)