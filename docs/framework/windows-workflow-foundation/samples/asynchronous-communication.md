---
title: Asynchronní komunikaci
ms.date: 03/30/2017
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
ms.openlocfilehash: 9eafeab89aefb181ae016dc0219f9155d9bd2a25
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515157"
---
# <a name="asynchronous-communication"></a>Asynchronní komunikaci
Tento příklad znázorňuje, jak komunikaci mezi dvěma různými službami Windows Workflow Foundation (WF) probíhá asynchronně ve výchozím nastavení.  
  
## <a name="demonstrates"></a>Demonstruje  
 Asynchronní komunikaci mezi [!INCLUDE[wf1](../../../../includes/wf1-md.md)] služby.  
  
## <a name="discussion"></a>Diskusní  
 Tento příklad ukazuje, jak komunikaci mezi [!INCLUDE[wf1](../../../../includes/wf1-md.md)] aplikací se provádí asynchronně pomocí zasílání zpráv aktivity poskytované rozhraní .NET Framework.  
  
 Tato ukázka se skládá z následujících tří projektů.  
  
 CreditCheckService  
 Tato služba přijímá skóre platební konkrétní osoby nebo hodnota položky získat a potom se rozhodne, zda je zadána se kredit osobě.  
  
 RentalApprovalService  
 Tato služba přijímá aplikace z osoba, která je potřeba zkontrolovat některé kreditu. Tato služba komunikuje asynchronně `CreditCheckService` rozhodnout, zda je aplikace platební platný.  
  
 Klient  
 Klient komunikuje s synchronně `RentalApprovalService` vědět, jestli je schváleno se kredit.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Klikněte pravým tlačítkem myši **AsynchronousCommunication** řešení a vyberte **vlastnosti**.  
  
2.  V **společných vlastností**, vyberte **spouštěný projekt**a vyberte **více projektů po spuštění**.  
  
3.  Přesunout **RentalApprovalService** na první pozici v seznamu, následuje **CreditCheckService**, za nímž následují **klienta**. Nastavte **spustit** akce na všech tří projektů.  
  
4.  Klikněte na tlačítko **OK**, a stisknutím klávesy F5 spusťte vzorku.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
