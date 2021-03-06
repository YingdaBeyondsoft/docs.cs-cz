---
title: 'Postupy: Přidání odkazu služby dat (služby WCF Data Services)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
ms.openlocfilehash: a8dcc01fb7a564a363cabed6a22738cd520d317f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356228"
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a>Postupy: Přidání odkazu služby dat (služby WCF Data Services)
Můžete použít **přidat odkaz na službu** dialogové okno v sadě Visual Studio se přidat odkaz na [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. To umožňuje snadno přístup ke službě data v aplikaci klienta, které vyvíjíte v sadě Visual Studio. Po dokončení tohoto postupu se generují třídy dat na základě metadat, který byl získán z službu data. Další informace najdete v tématu [generování dat služby klientské knihovny](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).  
  
### <a name="to-add-a-data-service-reference"></a>Chcete-li přidat odkaz na službu data  
  
1.  (Volitelné) Pokud službu data není součástí řešení a není spuštěná, spusťte službu data a poznamenejte si identifikátor URI služby data.  
  
2.  Klikněte pravým tlačítkem na projekt klienta a pak vyberte **přidat odkaz na službu**.  
  
3.  Pokud službu data je součástí aktuální řešení, klikněte na tlačítko **Discover**.  
  
     -nebo-  
  
     V **adresu** textového pole zadejte základní adresu URL služby data, jako třeba `http://localhost:1234/Northwind.svc`a potom klikněte na **přejděte**.  
  
4.  Click **OK**.  
  
     Tento postup přidá nový soubor kód, který obsahuje datové třídy, které se používají pro přístup a pracovat s prostředky služby data jako objekty.  
  
## <a name="see-also"></a>Viz také  
 [Rychlý start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
