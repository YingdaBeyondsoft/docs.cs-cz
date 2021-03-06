---
title: IMetaDataImport::GetPropertyProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPropertyProps
helpviewer_keywords:
- GetPropertyProps method [.NET Framework metadata]
- IMetaDataImport::GetPropertyProps method [.NET Framework metadata]
ms.assetid: dc0ff3e6-7e7d-4f6c-948d-52b28f5cb78c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7312cbd31a04365801b0380d5914966f36679560
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449452"
---
# <a name="imetadataimportgetpropertyprops-method"></a>IMetaDataImport::GetPropertyProps – metoda
Získá metadata pro vlastnost reprezentována zadaný token.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetPropertyProps (  
   [in]  mdProperty        prop,  
   [out] mdTypeDef         *pClass,   
   [out] LPCWSTR           szProperty,   
   [in]  ULONG             cchProperty,   
   [out] ULONG             *pchProperty,   
   [out] DWORD             *pdwPropFlags,   
   [out] PCCOR_SIGNATURE   *ppvSig,   
   [out] ULONG             *pbSig,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppDefaultValue,  
   [out] ULONG             *pcchDefaultValue,  
   [out] mdMethodDef       *pmdSetter,   
   [out] mdMethodDef       *pmdGetter,   
   [out] mdMethodDef       rmdOtherMethod[],  
   [in]  ULONG             cMax,   
   [out] ULONG             *pcOtherMethod   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `prop`  
 [v] Token, který reprezentuje vlastnost vrátit metadata pro.  
  
 `pClass`  
 [out] Ukazatel na TypeDef token, který představuje typ, který implementuje vlastnost.  
  
 `szProperty`  
 [out] Vyrovnávací paměť pro název vlastnosti.  
  
 `cchProperty`  
 [v] Velikost v široké znaky `szProperty`.  
  
 `pchProperty`  
 [out] Počet široké znaky, vrátí se v `szProperty`.  
  
 `pdwPropFlags`  
 [out] Ukazatel na žádné příznaky atribut použit na vlastnosti. Tato hodnota je bitová maska z [CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) výčtu.  
  
 `ppvSig`  
 [out] Ukazatel na podpis metadata vlastnosti.  
  
 `pbSig`  
 [out] Počet bajtů vrácených v `ppvSig`.  
  
 `pdwCPlusTypeFlag`  
 [out] Příznak určující typ konstanta, která je výchozí hodnota vlastnosti. Tato hodnota je z CorElementType – výčet.  
  
 `ppDefaultValue`  
 [out] Ukazatel na počet bajtů, které ukládají výchozí hodnotu pro tuto vlastnost.  
  
 `pcchDefaultValue`  
 [out] Velikost v široké znaky `ppDefaultValue`, pokud `pdwCPlusTypeFlag` je ELEMENT_TYPE_STRING; jinak, tato hodnota není relevantní. V takovém případě délka `ppDefaultValue` je odvozen od typu, která je zadána `pdwCPlusTypeFlag`.  
  
 `pmdSetter`  
 [out] Ukazatel na MethodDef token, který představuje metodu přistupující objekt set pro vlastnost.  
  
 `pmdGetter`  
 [out] Ukazatel na MethodDef token, který představuje metodu get přistupujícího objektu vlastnosti.  
  
 `rmdOtherMethod`  
 [out] Pole MethodDef tokeny, které představují další metody související s vlastností.  
  
 `cMax`  
 [v] Maximální velikost `rmdOtherMethod` pole. Pokud nezadáte pole dostatečně velký pro uložení všech metod, jsou přeskočena bez upozornění.  
  
 `pcOtherMethod`  
 [out] Počet MethodDef tokeny, vrátí se v `rmdOtherMethod`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
