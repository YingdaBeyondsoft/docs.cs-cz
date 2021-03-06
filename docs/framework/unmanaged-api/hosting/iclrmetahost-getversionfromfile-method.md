---
title: ICLRMetaHost::GetVersionFromFile – metoda
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.GetVersionFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetVersionFromFile
helpviewer_keywords:
- ICLRMetaHost::GetVersionFromFile method [.NET Framework hosting]
- GetVersionFromFile method [.NET Framework hosting]
ms.assetid: 55bb3eb4-f665-42fc-973c-465567570e82
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 538e596c3a705020150f52c9e55605a49434ce8f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434048"
---
# <a name="iclrmetahostgetversionfromfile-method"></a>ICLRMetaHost::GetVersionFromFile – metoda
Získá sestavení původní verze rozhraní .NET Framework kompilace (uložená v metadatech), zadána cesta k souboru. Tato metoda nahrazuje [getfileversion –](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md) funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetVersionFromFile (  
    [in] LPCWSTR pwzFilePath,  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBuffer);  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pwzFilePath`  
 [v] Cesta k souboru dokončení sestavení.  
  
 `pwzbuffer`  
 [out] Verze kompilace rozhraní .NET Framework, uložená v metadatech ve formátu "v*A*. *B*[. *X*] ". *A*, *B*, a *X* jsou desetinná čísla, která odpovídá hlavní, vedlejší verze a číslo sestavení. Délka tohoto řetězce je omezená na hodnotou MAX_PATH.  
  
> [!NOTE]
>  Tento výstup odpovídá název adresáře pro verzi rozhraní .NET Framework, jak se objevuje v části C:\Windows\Microsoft.NET\Framework.  
  
 Ukázkové hodnoty jsou "v1.0.3705", "v1.1.4322", "v2.0.50727" a "v4.0. *X*", kde *X* závisí na počtu sestavení nainstalována. Všimněte si, že vyžaduje se předpona "v".  
  
 `pcchBuffer`  
 [ve out] Velikost `pwzbuffer` předejdete přetečení vyrovnávací paměti.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_POINTER|`pwzbuffer` nebo `pcchBuffer` má hodnotu null.|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|Vyrovnávací paměť je příliš malá.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRMetaHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
