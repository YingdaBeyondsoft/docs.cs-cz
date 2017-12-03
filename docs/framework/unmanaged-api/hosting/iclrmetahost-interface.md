---
title: "ICLRMetaHost – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHost
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHost
helpviewer_keywords: ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: c627fcdd-fc4f-4b1c-8e91-df8536f627d8
topic_type: apiref
caps.latest.revision: "28"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d271a69847e3bd4dc972ed8e697b8cd15f049fb9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmetahost-interface"></a><span data-ttu-id="f6366-102">ICLRMetaHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f6366-102">ICLRMetaHost Interface</span></span>
<span data-ttu-id="f6366-103">Poskytuje metody, které vrátí na konkrétní verzi common language runtime (CLR) podle jeho číslo verze, seznam všech nainstalovaných CLRs, seznamu všechny moduly runtime načtené v určeném procesu, zjistit verze CLR použít ke kompilaci sestavení, ukončete proces vypnutí čistou runtime a starší verze rozhraní API vazby dotazů.</span><span class="sxs-lookup"><span data-stu-id="f6366-103">Provides methods that return a specific version of the common language runtime (CLR) based on its version number, list all installed CLRs, list all runtimes that are loaded in a specified process, discover the CLR version used to compile an assembly, exit a process with a clean runtime shutdown, and query legacy API binding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f6366-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f6366-104">Methods</span></span>  
  
|<span data-ttu-id="f6366-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f6366-105">Method</span></span>|<span data-ttu-id="f6366-106">Popis</span><span class="sxs-lookup"><span data-stu-id="f6366-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f6366-107">Enumerateinstalledruntimes – metoda</span><span class="sxs-lookup"><span data-stu-id="f6366-107">EnumerateInstalledRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateinstalledruntimes-method.md)|<span data-ttu-id="f6366-108">Vrátí výčet, který obsahuje platnou [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) ukazatel rozhraní pro jednotlivé verze CLR, který je nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="f6366-108">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each CLR version that is installed on a computer.</span></span>|  
|[<span data-ttu-id="f6366-109">Enumerateloadedruntimes – metoda</span><span class="sxs-lookup"><span data-stu-id="f6366-109">EnumerateLoadedRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateloadedruntimes-method.md)|<span data-ttu-id="f6366-110">Vrátí výčet, který obsahuje platnou [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) ukazatel rozhraní pro každý modul CLR, který je načten do daného procesu.</span><span class="sxs-lookup"><span data-stu-id="f6366-110">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each CLR that is loaded in a given process.</span></span> <span data-ttu-id="f6366-111">Tato metoda nahrazuje [getversionfromprocess –](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md).</span><span class="sxs-lookup"><span data-stu-id="f6366-111">This method supersedes [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md).</span></span>|  
|[<span data-ttu-id="f6366-112">Exitprocess – metoda</span><span class="sxs-lookup"><span data-stu-id="f6366-112">ExitProcess Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md)|<span data-ttu-id="f6366-113">Pokusí se korektně vypnout všechny načíst moduly runtime a pak ukončit proces.</span><span class="sxs-lookup"><span data-stu-id="f6366-113">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="f6366-114">Nahrazuje [corexitprocess –](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="f6366-114">Supersedes the [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) function.</span></span>|  
|[<span data-ttu-id="f6366-115">Getruntime – metoda</span><span class="sxs-lookup"><span data-stu-id="f6366-115">GetRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md)|<span data-ttu-id="f6366-116">Získá [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní, která odpovídá na konkrétní verzi CLR.</span><span class="sxs-lookup"><span data-stu-id="f6366-116">Gets the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to a particular CLR version.</span></span> <span data-ttu-id="f6366-117">Tato metoda nahrazuje [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) funkce použít s [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) příznak.</span><span class="sxs-lookup"><span data-stu-id="f6366-117">This method supersedes the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) flag.</span></span>|  
|[<span data-ttu-id="f6366-118">Getversionfromfile – metoda</span><span class="sxs-lookup"><span data-stu-id="f6366-118">GetVersionFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getversionfromfile-method.md)|<span data-ttu-id="f6366-119">Získá sestavení původní verze rozhraní .NET Framework kompilace (uložená v metadatech), zadána cesta k souboru.</span><span class="sxs-lookup"><span data-stu-id="f6366-119">Gets the assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="f6366-120">Tato metoda nahrazuje [getfileversion –](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md).</span><span class="sxs-lookup"><span data-stu-id="f6366-120">This method supersedes [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md).</span></span>|  
|[<span data-ttu-id="f6366-121">Querylegacyv2runtimebinding – metoda</span><span class="sxs-lookup"><span data-stu-id="f6366-121">QueryLegacyV2RuntimeBinding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-querylegacyv2runtimebinding-method.md)|<span data-ttu-id="f6366-122">Vrátí rozhraní, které představuje runtime, do které starší verze aktivace zásad byla svázána, například pomocí `useLegacyV2RuntimeActivationPolicy` atributu u [ \<spuštění > Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) souboru položka konfigurace, pomocí přímých Aktivace starší verze rozhraní API nebo voláním [iclrruntimeinfo::bindaslegacyv2runtime –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="f6366-122">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>|  
|[<span data-ttu-id="f6366-123">Requestruntimeloadednotification – metoda</span><span class="sxs-lookup"><span data-stu-id="f6366-123">RequestRuntimeLoadedNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-requestruntimeloadednotification-method.md)|<span data-ttu-id="f6366-124">Zpětné volání pro zadanou funkci ukazatele zaručuje, když je prvním načtení verze CLR, ale ještě nebyla spuštěna.</span><span class="sxs-lookup"><span data-stu-id="f6366-124">Guarantees a callback to the specified function pointer when a CLR version is first loaded, but not yet started.</span></span> <span data-ttu-id="f6366-125">Tato metoda nahrazuje [lockclrversion –](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)</span><span class="sxs-lookup"><span data-stu-id="f6366-125">This method supersedes [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6366-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f6366-126">Remarks</span></span>  
 <span data-ttu-id="f6366-127">Jediný způsob, jak získat instanci toto rozhraní je voláním [clrcreateinstance –](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) funkce následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f6366-127">The only way to get an instance of this interface is by calling the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function as follows:</span></span>  
  
```  
ICLRMetaHost *pMetaHost = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHost,  
                   IID_ICLRMetaHost, (LPVOID*)&pMetaHost);  
```  
  
## <a name="requirements"></a><span data-ttu-id="f6366-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f6366-128">Requirements</span></span>  
 <span data-ttu-id="f6366-129">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6366-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6366-130">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="f6366-130">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f6366-131">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f6366-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f6366-132">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6366-132">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6366-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="f6366-133">See Also</span></span>  
 [<span data-ttu-id="f6366-134">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="f6366-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="f6366-135">Hostování</span><span class="sxs-lookup"><span data-stu-id="f6366-135">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)