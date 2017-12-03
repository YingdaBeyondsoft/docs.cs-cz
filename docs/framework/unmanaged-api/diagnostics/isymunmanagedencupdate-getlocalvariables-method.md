---
title: "ISymUnmanagedENCUpdate::GetLocalVariables – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedENCUpdate.GetLocalVariables
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedENCUpdate::GetLocalVariables
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables method [.NET Framework debugging]
- GetLocalVariables method [.NET Framework debugging]
ms.assetid: 5c8840be-ffea-447f-9c8d-178f1eaf8d06
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 492d41402531cb6fb92f90ab0e533fb20c6129df
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedencupdategetlocalvariables-method"></a><span data-ttu-id="3dd05-102">ISymUnmanagedENCUpdate::GetLocalVariables – metoda</span><span class="sxs-lookup"><span data-stu-id="3dd05-102">ISymUnmanagedENCUpdate::GetLocalVariables Method</span></span>
<span data-ttu-id="3dd05-103">Získá místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="3dd05-103">Gets the local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dd05-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3dd05-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVariables(  
    [in]  mdMethodDef  mdMethodToken,  
    [in]  ULONG        cLocals,  
    [out, size_is(cLocals), length_is(*pceltFetched)]  
        ISymUnmanagedVariable *rgLocals[],  
    [out] ULONG        *pceltFetched);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3dd05-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3dd05-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="3dd05-106">[v] Token metadata metody.</span><span class="sxs-lookup"><span data-stu-id="3dd05-106">[in] The metadata token of the method.</span></span>  
  
 `cLocals`  
 <span data-ttu-id="3dd05-107">[v] A `ULONG` určující velikost `rgLocals` parametr.</span><span class="sxs-lookup"><span data-stu-id="3dd05-107">[in] A `ULONG` that indicates the size of the `rgLocals` parameter.</span></span>  
  
 `rgLocals`  
 <span data-ttu-id="3dd05-108">[out] Vrácená pole <!--zz<xref:ISymUnmanagedVariable>--> `ISymUnmanagedVariable` instance.</span><span class="sxs-lookup"><span data-stu-id="3dd05-108">[out] The returned array of <!--zz<xref:ISymUnmanagedVariable>--> `ISymUnmanagedVariable`  instances.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="3dd05-109">[out] Ukazatel `ULONG` která přijme velikost `rgLocals` vyrovnávací paměti musí obsahovat lokální.</span><span class="sxs-lookup"><span data-stu-id="3dd05-109">[out] A pointer to a `ULONG` that receives the size of the `rgLocals` buffer required to contain the locals.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3dd05-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3dd05-110">Return Value</span></span>  
 <span data-ttu-id="3dd05-111">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="3dd05-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3dd05-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3dd05-112">Requirements</span></span>  
 <span data-ttu-id="3dd05-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3dd05-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dd05-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="3dd05-114">See Also</span></span>  
 [<span data-ttu-id="3dd05-115">Isymunmanagedencupdate – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3dd05-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)