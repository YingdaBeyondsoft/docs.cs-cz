---
title: Emulace nejnovější ve chvíli aktivity
ms.date: 03/30/2017
ms.assetid: ddff715d-d623-4b54-b841-60bacbc3ca21
ms.openlocfilehash: 37c64c2b8dc03d58f9c2802edef644fe4888e87d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514710"
---
# <a name="emulating-breaking-in-a-while-activity"></a>Emulace nejnovější ve chvíli aktivity
Tento příklad ukazuje, jak rozdělit opakování mechanismus z následujících aktivit: <xref:System.Activities.Statements.DoWhile>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.While>, a <xref:System.Activities.Statements.ParallelForEach%601>.  
  
 To je užitečné, protože Windows Workflow Foundation (WF) neobsahuje žádnou aktivitu pro přerušení provádění těchto smyčky.  
  
## <a name="scenario"></a>Scénář  
 Ukázka vyhledá první spolehlivé dodavatele ze seznamu dodavatelů (instance `Vendor` třídy). Má jednotlivých dodavatelů `ID`, `Name` a spolehlivost číselnou hodnotu, která určuje, jak spolehlivé dodavatele. Ukázka vytvoří vlastní aktivity volá `FindReliableVendor` který přijímá dva vstupní parametry (seznam dodavateli a hodnotu minimální spolehlivost) a vrátí první dodavatele tohoto seznamu, který odpovídá zadaným kritériím.  
  
## <a name="breaking-a-loop"></a>Pozastavení smyčku  
 Windows Workflow Foundation (WF) nezahrnuje aktivitu pro přerušení smyčku. Ukázka kódu provede nejnovější smyčku pomocí <xref:System.Activities.Statements.If> aktivity a několik proměnné. V ukázce <xref:System.Activities.Statements.While> aktivity je porušený jednou `reliableVendor` proměnné je jiné než přiřazenou hodnotu `null`.  
  
 Následující příklad kódu ukazuje, jak ukázku dělí chvíli smyčky.  
  
```csharp  
// Iterates while the "i" variable is lower than the size of the list   
// and any reliable Vendor is found.        
new While(env => i.Get(env) < this.Vendors.Get(env).Count && reliableVendor.Get(env) == null)  
{  
    DisplayName = "Main loop. Breaks when a reliable vendor is found",  
    Body = new Sequence  
    {                              
        Activities =  
        {  
            // This is the if used for setting the value of the break value…  
            new If  
            {  
                DisplayName = "Check for a reliable vendor",  
  
                //  If a vendor satisfies the reliability level…  
                Condition = new InArgument<bool>(env =>   
                           this.Vendors.Get(env)[i.Get(env)].Reliability >   
                           this.MinimumReliability.Get(env)),  
  
                // then assign that vendor to the reliable vendor variable and   
                // the while condition becomes false (exit the loop).  
                Then = new Assign<Vendor>  
                {  
                    To = reliableVendor,  
                    Value = new InArgument<Vendor>(env =>   
                                  this.Vendors.Get(env)[i.Get(env)])  
                }  
            },  
  
            // Increment the iteration variable.   
            new Assign<int>  
            {  
                DisplayName = "Increment iteration variable",  
                To = i,  
                Value = new InArgument<int>(env => i.Get(env) + 1)  
            }   
        }  
    }  
}  
```  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení EmulatingBreakInWhile.sln.  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Chcete-li spustit řešení, stiskněte CTRL + F5.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\EmulatingBreakInWhile`