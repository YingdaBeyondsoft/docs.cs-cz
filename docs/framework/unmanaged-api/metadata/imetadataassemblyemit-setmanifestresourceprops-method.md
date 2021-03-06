---
title: IMetaDataAssemblyEmit::SetManifestResourceProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetManifestResourceProps
helpviewer_keywords:
- SetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetManifestResourceProps method [.NET Framework metadata]
ms.assetid: ef77efd1-849c-4e51-ba92-7ee3d2bf0339
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 755c64aa00b82bf2d8213217787f4dc1916c0898
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443297"
---
# <a name="imetadataassemblyemitsetmanifestresourceprops-method"></a>IMetaDataAssemblyEmit::SetManifestResourceProps – metoda
Upraví zadaný `ManifestResource` strukturu metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetManifestResourceProps (  
    [in] mdManifestResource  mr,  
    [in] mdToken             tkImplementation,   
    [in] DWORD               dwOffset,  
    [in] DWORD               dwResourceFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `mr`  
 [v] Token, který určuje `ManifestResource` strukturu metadat má být změněn.  
  
 `tkImplementation`  
 [v] Token, typu `File` nebo `AssemblyRef`, která se mapuje na zprostředkovateli prostředků.  
  
 `dwOffset`  
 [v] Posun na začátek prostředků v rámci tohoto souboru.  
  
 `dwResourceFlags`  
 [v] Bitová kombinace hodnot příznaku, které určují atributy prostředku.  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li vytvořit `ManifestResource` strukturu metadat, použijte [imetadataassemblyemit::definemanifestresource –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) metoda.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
