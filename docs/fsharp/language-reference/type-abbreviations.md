---
title: Zkratky typů (F#)
description: 'Další informace o F # zkratky typů pojmenovat typu smysluplnější abyste snadněji kódu.'
ms.date: 05/16/2016
ms.openlocfilehash: e222caa41a20a64071c94cffea6ea7b2bec8eb22
ms.sourcegitcommit: ff1d40507b3eb6e2185478e37c66c66be6de46f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/11/2018
ms.locfileid: "34058950"
---
# <a name="type-abbreviations"></a>Zkratky typů

A *– zkratka typu* je alias nebo alternativní název typu.

## <a name="syntax"></a>Syntaxe

```fsharp
type [accessibility-modifier] type-abbreviation = type-name
```

## <a name="remarks"></a>Poznámky
Zkratky typů můžete poskytnout typu více smysluplný název, abyste snadněji kódu. Můžete je také použít k vytvoření snadno použitelný názvu pro typ, který je jinak náročná zapsat. Kromě toho aby bylo snazší změna základního typu beze změny jejího kódu, který používá typ můžete zkratky typů. Toto je zkratka jednoduchého typu.

Výchozí nastavení usnadnění zkratky typů `public`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

Zkratky typů může zahrnovat obecné parametry, jako v následujícím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

V předchozí kód `Transform` je zkratka typu, který představuje funkci, která přijímá jeden argument libovolného typu a který vrací jedinou hodnotu stejného typu.

Zkratky typů nejsou zachována v rozhraní .NET Framework MSIL kódu. Proto při použití sestavení F # z jiný jazyk rozhraní .NET Framework, musíte použít název základního typu pro zkratka typu.

Zkratky typů můžete použít taky u měrné jednotky. Další informace najdete v tématu [měrné jednotky](units-of-measure.md).


## <a name="see-also"></a>Viz také
[Referenční dokumentace jazyka F#](index.md)

