---
title: IMetaDataEmit::MergeEnd – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.MergeEnd
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::MergeEnd
helpviewer_keywords:
- MergeEnd method [.NET Framework metadata]
- IMetaDataEmit::MergeEnd method [.NET Framework metadata]
ms.assetid: 2d64315a-1af1-4c60-aedf-f8a781914aea
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b794a62a0ac0d253f1431be29b43101816dc7233
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449439"
---
# <a name="imetadataemitmergeend-method"></a>IMetaDataEmit::MergeEnd – metoda
Sloučení do aktuální obor všechny obory metadata určeného jeden nebo více předchozích volání [imetadataemit::merge –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT MergeEnd ();  
```  
  
#### <a name="parameters"></a>Parametry  
 Tato metoda nepřijímá žádné parametry.  
  
## <a name="remarks"></a>Poznámky  
 Tato rutina aktivuje skutečné sloučení metadat, všechny importovat rozsahy určené tak, že před volání `IMetaDataEmit::Merge`, do aktuálního oboru výstup.  
  
 Následující zvláštní podmínky platí pro sloučení:  
  
-   Identifikátor verze modulu (identifikátoru MVID) je nikdy importován, protože je jedinečné pro metadata v oboru importu.  
  
-   Žádné existující vlastnosti modulu celou se přepíší.  
  
     Pokud modul vlastnosti byly nastaveny pro aktuální obor, žádné vlastnosti modulu importují. Nicméně pokud nebyly nastaveny vlastnosti modulu v aktuálním oboru, jsou importované jen jednou, pokud se při prvním výskytu. Pokud tyto vlastnosti modulu nedojde k znovu, jsou duplicitní. Pokud porovnání hodnot všech vlastností modulu (s výjimkou identifikátoru MVID) a jsou nalezeny žádné duplicitní hodnoty, je vyvolána k chybě.  
  
-   Pro definice typů (`TypeDef`), neobsahuje žádné duplikáty jsou sloučeny do aktuálního oboru. `TypeDef` objekty jsou kontrolovány duplikátů proti jednotlivým *objekt plně kvalifikovaný název* + *GUID* + *číslo verze*. Pokud není nalezena shoda na název nebo identifikátor GUID, a všechny další dva elementy se liší, je vyvolána k chybě. Jinak, pokud se všechny tři položky shodují, `MergeEnd` provede zběžnou kontrolu, ujistěte se, pak jsou skutečně duplikáty; v opačném případě se vyvolá chybu. Kontrola zběžnou vyhledá:  
  
    -   Stejném deklarace členů, ke kterým dochází ve stejném pořadí. Členové, které jsou označeny jako `mdPrivateScope` (najdete v článku [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) – výčet) nejsou součástí této kontroly; se speciálně sloučí.  
  
    -   Se stejné rozvržení třídy.  
  
     To znamená, že `TypeDef` objekt musí vždy být plně a konzistentně definován v oboru každých metadata ve kterém je deklarovaná; pokud jeho implementace člen (pro třídu) jsou rozloženy několika kompilačních jednotek, se považuje za úplné definice v každé oboru a ne přírůstkové do každého oboru. Například pokud názvy parametrů jsou relevantní pro kontrakt, se musí být vygenerované stejným způsobem jako do každé oboru; Pokud nejsou relevantní, by neměl být vložen do metadat.  
  
     Výjimkou je, že `TypeDef` objekt může mít přírůstkové členy označení `mdPrivateScope`. Na tyto zjištění `MergeEnd` přírůstkově se přidají do aktuálního oboru bez ohledu na duplicitní položky. Protože kompilátor rozumí oboru privátní, musí být kompilátor zodpovědný za vynucení pravidel.  
  
-   Relativní virtuální adresy (RVAs) nejsou importovány nebo sloučit; Kompilátor očekává se znovu generuje tato informace.  
  
-   Vlastní atributy jsou sloučeny jenom v případě, že je sloučen položku, ke kterému jsou připojené. Například vlastní atributy přidružené třídy jsou sloučeny, pokud je třída při prvním výskytu. Pokud jsou vlastní atributy přidružené `TypeDef` nebo `MemberDef` týkající se jednotka kompilace (například časové razítko kompilace člen), není sloučeno a je maximálně kompilátoru odebrat nebo aktualizovat takové metadat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
