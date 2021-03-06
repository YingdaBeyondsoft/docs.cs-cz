---
title: Mapování a modelování
ms.date: 03/30/2017
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
ms.openlocfilehash: 88c8786a5e538d8441e03e46e59743e4c489b4c5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32762933"
---
# <a name="modeling-and-mapping"></a>Mapování a modelování
V [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], můžete definovat Koncepční model, modelu úložiště a mapování mezi těmito dvěma způsobem, který nejlépe vyhovuje vaší aplikace. Nástroje modelu Entity Data v sadě Visual Studio umožňují vytvářet. [souboru edmx](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4) z databáze nebo grafické modelu a poté aktualizace které souboru při změně databáze nebo model.  
  
 Od verze Entity Framework 4.1 můžete také vytvořit model programově pomocí Code First vývoj. Existují dva různé scénáře pro vývoj Code First. V obou případech vývojář definuje model pomocí kódování definice tříd rozhraní .NET Framework a poté Volitelně můžete určit další mapování nebo konfigurace pomocí datových poznámek nebo rozhraní fluent API.  
  
 Další informace najdete v tématu [vytvoření a mapování konceptuálního modelu](http://go.microsoft.com/fwlink/?LinkId=235016).  
  
 Můžete také použít Generátor EDM, který je součástí [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]. EdmGen.exe generuje .csdl, .ssdl a .msl soubory z existujícího zdroje dat. Můžete také ručně vytvořit model a mapování obsahu. Další informace najdete v tématu [EDM generátor (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md).
