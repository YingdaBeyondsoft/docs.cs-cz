---
title: Spolupráce peer-to-Peer
ms.date: 03/30/2017
ms.assetid: b6216d88-bccb-4a59-9f1c-9f751708e811
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a933c81105399a9411fcb749a06e47bf769cf532
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397816"
---
# <a name="peer-to-peer-collaboration"></a>Spolupráce peer-to-Peer
Sítě peer-to-peer je využití poměrně výkonné počítače (osobní počítače), které existují na hranici sítě Internet pro více než jen na základě klienta výpočetní úlohy. Moderní osobní počítač (počítače) má velmi rychlé procesor, valná paměti a velký pevný disk, žádný z nich se právě plně využít při provádění běžných úloh výpočetní například e-mailu a procházení webu. Moderní počítač můžete snadno fungovat jako klient i server (sdílené) pro mnoho typů aplikací.  
  
-   Infrastruktura spolupráce Peer-to-Peer je zjednodušenou implementaci infrastruktury Microsoft Windows Peer-to-Peer, která využívá osoby téměř mi služby v systému Windows Vista a pozdější platformy. Je nejvhodnější pro aplikace sdílené v rámci jedné podsítě pro pro který lidé téměř mi služba funguje, i když ho může obsluhovat koncové body internet nebo také kontakty. Její součástí jsou běžné správce kontaktovat, který je používán Live Messenger a další aplikace používající živé určit kontaktní koncových bodů, dostupnosti a přítomnosti.  
  
-  
  
## <a name="collaboration-applications"></a>Aplikace spolupráce  
 Typické peer-to-peer spolupráce aplikace se skládá z následujících kroků:  
  
-   Sdílené určuje identitu partnerského uzlu, který má zájem o hostování relaci spolupráce  
  
-   Je odeslán požadavek na hostitele relace, nějakým způsobem, a sdílené hostitele souhlasí ke správě spolupráce aktivity.  
  
-   Hostitel vyzývá kontaktů v podsíti (včetně žadatel) k relaci.  
  
-   Všechny partnerské uzly, kteří chtějí spolupracovat může přidávat hostitele do jejich kontaktujte správce.  
  
-   Většina partnerské uzly bude posílat odpovědi pozvánku, zda přijímat nebo odmítnuty zpět na hostitele partnera včas.  
  
-   Všechny partnerské uzly, které chcete spolupracovat se přihlášení k odběru na hostitele partnera.  
  
-   Při provádění jejich aktivita počáteční spolupráce partnerské uzly, může sdílené hostitele přidejte vzdálených partnerských uzlů do jejího kontaktujte správce. Také zpracuje všechny odpovědi pozvánku k určení kteří přijali, kdo má odmítl a kdo nebyl odpovědi.  Může zrušit pozvánky na ty, kteří neodpověděli, nebo provést některé další aktivity.  
  
-   Sdílené hostitele v tomto okamžiku můžete spustit relaci spolupráce s všechny pozvané partnerské uzly nebo zaregistrovat aplikaci s infrastrukturou spolupráce.  Aplikace P2P používat infrastrukturu Peer-to-Peer spolupráce a <xref:System.Net.PeerToPeer.Collaboration> obor názvů pro koordinaci komunikaci pro hry, BBS, konference a jiné bez serveru přítomnost aplikace.  
  
-  
  
## <a name="peer-to-peer-networking-security"></a>Zabezpečení sítě peer-to-Peer  
 V doméně služby Active Directory řadiče domény poskytovaly služby ověřování pomocí protokolu Kerberos. V prostředí bez serveru sdílené partnerské uzly musíte zadat své vlastní ověřování. Pro Peer-to-Peer sítě libovolného uzlu vystupovat jako odebrání požadavek kořenového certifikátu v úložišti každé sdílené důvěryhodné kořenové certifikační Autority. Zajišťuje ověřování pomocí certifikátů podepsaných držitelem, naformátovaná jako certifikáty X.509. Jedná se o certifikáty, které jsou vytvořené pomocí každého partnera, který generuje veřejný klíč a privátního klíče RSA a certifikát, který je podepsaný pomocí soukromého klíče. Certifikát podepsaný svým držitelem se používá k ověřování a poskytují informace o sdílené entity. Jako X.509 ověřování ověřování sítě partnera závisí na řetěz certifikátů trasování zpět na veřejný klíč, který je důvěryhodný.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.PeerToPeer.Collaboration>  
 [Obor názvů System.Net.PeerToPeer.Collaboration](../../../docs/framework/network-programming/about-the-system-net-peertopeer-collaboration-namespace.md)
