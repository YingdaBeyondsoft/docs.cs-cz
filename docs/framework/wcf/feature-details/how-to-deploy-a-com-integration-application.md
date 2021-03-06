---
title: 'Postupy: Nasazení aplikace integrací COM+'
ms.date: 03/30/2017
ms.assetid: 2e5a0510-db3c-4988-a09c-696285836650
ms.openlocfilehash: 872d0f0c84c1ac0ea96a87ed24a386bb9bedcf85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490136"
---
# <a name="how-to-deploy-a-com-integration-application"></a>Postupy: Nasazení aplikace integrací COM+
Jednou byly zapsány aplikace integrací COM +, můžete chtít nasadit virtuální počítač na jiný počítač. Toto téma popisuje postup přesunutí integrace aplikace modelu COM + z jednoho počítače do druhého.  
  
### <a name="moving-a-com-hosted-integration-app"></a>Přesunutí modelu COM + hostované integrace aplikace  
  
1.  Zkontrolujte, zda je na obou počítačích nainstalován WCF.  
  
2.  Exportujte aplikace z počítače A.  
  
3.  Importovat aplikace na počítači B.  
  
4.  Nastavte kořenový adresář aplikace. Podle konvence, to je %PROGRAMFILES%/ComPlus aplikace / {AppGUID}.  
  
5.  Zkopírujte soubory Application.config a Application.manifest z kořenového adresáře aplikace na počítače A do kořenového adresáře aplikace v počítači B.  
  
6.  Upravte adresy koncového bodu služby v souboru Application.config na počítači B identifikovat příslušný počítač. Můžete například změnit http://machineA/MyService k http://machineB/MyService.  
  
### <a name="moving-a-web-hosted-integration-application"></a>Přesunutí integrace hostované webové aplikace  
  
1.  Zkontrolujte, zda je na obou počítačích nainstalován WCF.  
  
2.  Exportujte aplikace z počítače A.  
  
3.  Importovat aplikace na počítači B.  
  
4.  Vytvořte kořenovou složku IIS v počítači B.  
  
5.  Zkopírujte soubor .svc (componentName.svc) a v souboru Web.config z vroot na počítač A pro nově vytvořený virtuální kořenový adresář na počítači B.  
  
## <a name="see-also"></a>Viz také  
 [Přehled integrace s aplikacemi modelu COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)  
 [Postupy: Konfigurace nastavení služby modelu COM+](../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)  
 [Postupy: Použití nástroje pro konfiguraci služby modelu COM+](../../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
