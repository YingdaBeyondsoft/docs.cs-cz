---
title: Zabezpečení zprostředkovatele typů
description: 'Další informace o zabezpečení zprostředkovatele typů v jazyce F #, včetně toho, jak chcete-li změnit nastavení vztahu důvěryhodnosti pro zprostředkovatele typů.'
ms.date: 05/16/2016
ms.openlocfilehash: 66a873a32029d706f1f6fab50dd4f93bc29bca03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563542"
---
# <a name="type-provider-security"></a>Zabezpečení zprostředkovatele typů

Zprostředkovatelé typů jsou sestavení (DLL) odkazuje F # projektu nebo skriptu obsahující kód k připojení k externím zdrojům dat a prezentovat informace o typu prostředí typ F #. Kód v odkazovaných sestaveních je obvykle spustit pouze při kompilaci a potom spusťte kód (nebo v případě skriptu poslat kód F # interaktivní). Sestavení zprostředkovatele typ však bude fungovat v sadě Visual Studio, při procházení kódu jenom v editoru. K tomu dochází, protože typ zprostředkovatele musí spustit a přidat doplňující informace do editoru, jako je například popisy tlačítek rychlé informace, dokončování IntelliSense a tak dále. V důsledku toho existují další bezpečnostní aspekty pro typ sestavení zprostředkovatele, vzhledem k tomu, že budou automaticky spustit uvnitř proces sady Visual Studio.


## <a name="security-warning-dialog"></a>Dialogové okno upozornění zabezpečení
Při prvním použití sestavení zprostředkovatele konkrétní typ, Visual Studio zobrazí dialogové okno zabezpečení, které vás varuje, že typ zprostředkovatele je spuštěn. Předtím, než Visual Studio načítá typu poskytovatele, nabízí možnost rozhodnout, zda důvěřovat tohoto konkrétního zprostředkovatele. Pokud považujete zdroj typ zprostředkovatele, pak vyberte "Důvěřuji tohoto typu zprostředkovatele." Pokud nedůvěřujete zdroji typ zprostředkovatele, pak vyberte "I možnost nedůvěřujete tohoto typu zprostředkovatele." Důvěřující zprostředkovatel umožňuje ho spustit v prostředí Visual Studio a poskytovat technologii IntelliSense a sestavení funkce. Ale pokud typ samotné se zlými úmysly, spuštění jeho kódu by mohly ohrozit váš počítač.

Pokud projekt obsahuje kód, který odkazuje na typ zprostředkovatele, které jste zvolili v dialogu není pro vztah důvěryhodnosti, pak při kompilaci, kompilátor nahlásí chybu, která označuje, že je zprostředkovatel typu nedůvěryhodné. Všechny typy, které jsou závislé na poskytovateli nedůvěryhodné typu jsou označeny červenou podtržení vlnovkou. Je bezpečné procházet kód v editoru.

Pokud se rozhodnete změnit nastavení důvěryhodnosti přímo v sadě Visual Studio, proveďte následující kroky.


#### <a name="to-change-the-trust-settings-for-type-providers"></a>Chcete-li změnit nastavení vztahu důvěryhodnosti pro zprostředkovatelů typů

1. Na `Tools` nabídce vyberte možnost `Options`a rozbalte `F# Tools` uzlu.
<br />

2. Vyberte `Type Providers`a v seznamu zprostředkovatelů typů, zaškrtněte políčko pro typ zprostředkovatele důvěřujete a zrušte zaškrtnutí políčka u uživatelů, kterým nedůvěřujete.
<br />


## <a name="see-also"></a>Viz také
[Zprostředkovatelé typů](index.md)
