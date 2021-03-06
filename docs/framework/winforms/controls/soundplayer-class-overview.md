---
title: Přehled třídy SoundPlayer
ms.date: 03/30/2017
helpviewer_keywords:
- playing sounds [Windows Forms], SoundPlayer class
- SoundPlayer class [Windows Forms], about SoundPlayer class
- sounds [Windows Forms], playing
ms.assetid: fcebb938-62b9-4677-9cbe-6465bc863e22
ms.openlocfilehash: 31ce87303b7b96cfd14d4daf07fd21c9de91a548
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535961"
---
# <a name="soundplayer-class-overview"></a>Přehled třídy SoundPlayer
<xref:System.Media.SoundPlayer> Vám umožňuje snadno zahrnout zvuky ve svých aplikacích.  
  
 <xref:System.Media.SoundPlayer> Třídy můžete přehrát zvukové soubory ve formátu WAV, z prostředku nebo z umístění UNC nebo HTTP. Kromě toho <xref:System.Media.SoundPlayer> vám umožňuje načíst nebo přehrání zvuků asynchronně.  
  
 Můžete také <xref:System.Media.SystemSounds> třída přehrávání běžné systémové zvuky, včetně zvukový signál.  
  
## <a name="commonly-used-properties-methods-and-events"></a>Běžně používané vlastnosti, metod a události  
  
|Název|Popis|  
|----------|-----------------|  
|<xref:System.Media.SoundPlayer.SoundLocation%2A> Vlastnost|Cesta k souboru nebo webovou adresu zvuku. Přípustné hodnoty může být cesta UNC nebo HTTP.|  
|<xref:System.Media.SoundPlayer.LoadTimeout%2A> Vlastnost|Počet milisekund, po které vašeho programu bude čekat na načítání zvuku dříve, než se vyvolá výjimku. Výchozí hodnota je 10 sekund.|  
|<xref:System.Media.SoundPlayer.IsLoadCompleted%2A> Vlastnost|Logická hodnota, která určuje, zda se dokončil načítání.|  
|<xref:System.Media.SoundPlayer.Load%2A> – Metoda|Načte zvuk synchronně.|  
|<xref:System.Media.SoundPlayer.LoadAsync%2A> – Metoda|Zahájí asynchronní načítání zvuku. Po dokončení načítání vyvolá <xref:System.Media.SoundPlayer.OnLoadCompleted%2A> událostí.|  
|<xref:System.Media.SoundPlayer.Play%2A> – Metoda|Hraje zvuk zadaný v <xref:System.Media.SoundPlayer.SoundLocation%2A> nebo <xref:System.Media.SoundPlayer.Stream%2A> vlastnost v nové vlákno.|  
|<xref:System.Media.SoundPlayer.PlaySync%2A> – Metoda|Hraje zvuk zadaný v <xref:System.Media.SoundPlayer.SoundLocation%2A> nebo <xref:System.Media.SoundPlayer.Stream%2A> vlastnost v aktuální vlákno.|  
|<xref:System.Media.SoundPlayer.Stop%2A> – Metoda|Ukončí všechny aktuálně přehrávání zvuku.|  
|<xref:System.Media.SoundPlayer.LoadCompleted> Události|Vyvolána po dojde k pokusu o načtení zvuku.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Media.SoundPlayer>  
 <xref:System.Media.SystemSounds>
