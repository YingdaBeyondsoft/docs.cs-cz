---
title: Sledování selhání operací služby
ms.date: 03/30/2017
ms.assetid: 59472ba3-8ebf-4479-bd7b-f440d5e636cb
ms.openlocfilehash: 3d708b537789c8d0decf75df780300c1e185c4c8
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803764"
---
# <a name="monitoring-service-operation-failures"></a>Sledování selhání operací služby
Pokud je povolené analytické trasování pro aplikaci, selhání služby se dá snadno sledovat v prohlížeči událostí.  Toto téma ukazuje, jak k určení, kdy dojde k selhání operace služby, a jak zjistit, co způsobilo selhání.  
  
### <a name="determining-service-operation-failure-information"></a>Určení informace o selhání operaci služby  
  
1.  Otevřete Prohlížeč událostí kliknutím **spustit**, **spustit**a zadáním `eventvwr.exe`.  
  
2.  Pokud jste nepovolili analytické trasování, rozbalte položku **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **serveru aplikace – aplikace** . Vyberte **zobrazení**, **ukazují analytické a ladicí protokoly**. Klikněte pravým tlačítkem na **analytické** a vyberte **povolit protokol**. Ponechte prohlížeče událostí otevřete tak, aby trasování lze zobrazit po operaci služby se nezdaří.  
  
3.  Dále otevřete vytvořené v ukázce [kurzu Začínáme](../../../../../docs/framework/wcf/getting-started-tutorial.md) v [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] Všimněte si, že je nutné spustit [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] jako správce, aby bylo možné vytvořit službu. Pokud máte Ukázky WCF nainstalován, můžete otevřít [Začínáme](../../../../../docs/framework/wcf/samples/getting-started-sample.md), který obsahuje dokončený projekt vytvořený v tomto kurzu.  
  
4.  V souboru Program.cs v projektu serveru, přidejte následující řádek kódu na začátek `Divide` metoda v `CalculatorService` třídy:  
  
    ```  
    if (n2 == 0) throw new DivideByZeroException();  
    ```  
  
5.  V souboru Program.cs v projektu klienta změňte hodnotu přiřazenou value2 na nulu:  
  
    ```  
    //Call the Divide service operation  
    value1 = 22.00D;  
    value2 = 0.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("Divide({0}, {1}) = {2}", value1, value2, result);  
    ```  
  
6.  Spuštění aplikace serveru bez ladění stisknutím kombinace kláves **Ctrl + F5**.  
  
7.  Otevřete příkazový řádek sady Visual Studio.  Přejděte do adresáře klienta a klient pro spuštění z příkazového řádku.  
  
8.  V prohlížeči událostí zakázat a aktualizujte protokol analytické a seřaďte události podle ID události.  Vyhledejte událost s ID události [219 - ServiceException](../../../../../docs/framework/wcf/diagnostics/etw/219-serviceexception.md), který popisuje selhání služby.  
  
    ```Output  
    There was an unhandled exception of type 'System.DivideByZeroException' during message processing.  Full Exception ToString: System.DivideByZeroException: Attempted to divide by zero.  
    ```  
  
    > [!NOTE]
    >  Události jsou do vyrovnávací paměti při odesílání do prohlížeče událostí; událost selhání nemusí zobrazit hned.
