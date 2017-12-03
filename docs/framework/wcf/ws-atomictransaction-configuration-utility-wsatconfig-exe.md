---
title: "Nástroj WS-AtomicTransaction Configuration Utility (wsatConfig.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c56cf98-3963-46d5-a4e1-482deae58c58
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 59b56b542a1624f1bae332ab91e1ac835aa47c8b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ws-atomictransaction-configuration-utility-wsatconfigexe"></a><span data-ttu-id="1394a-102">Nástroj WS-AtomicTransaction Configuration Utility (wsatConfig.exe)</span><span class="sxs-lookup"><span data-stu-id="1394a-102">WS-AtomicTransaction Configuration Utility (wsatConfig.exe)</span></span>
<span data-ttu-id="1394a-103">Nástroj WS-AtomicTransaction Configuration Utility slouží ke konfiguraci základní nastavení podpory protokolu WS-AtomicTransaction.</span><span class="sxs-lookup"><span data-stu-id="1394a-103">The WS-AtomicTransaction Configuration Utility is used to configure basic WS-AtomicTransaction support settings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1394a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1394a-104">Syntax</span></span>  
  
```  
wsatConfig [Options]  
```  
  
## <a name="remarks"></a><span data-ttu-id="1394a-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1394a-105">Remarks</span></span>  
 <span data-ttu-id="1394a-106">Tento nástroj příkazového řádku můžete použít ke konfiguraci základní WS-AT nastavení v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="1394a-106">This command line tool can be used to configure basic WS-AT settings in a local machine only.</span></span> <span data-ttu-id="1394a-107">Pokud budete muset nakonfigurovat nastavení na místních i vzdálených počítačích, se musí použít modul snap-in konzoly MMC jak je popsáno v [konfigurace podpory WS-Atomic Transactions](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md).</span><span class="sxs-lookup"><span data-stu-id="1394a-107">If you have to configure settings on both local and remote machines, you should use the MMC snap-in as described in [Configuring WS-Atomic Transaction Support](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md).</span></span>  
  
 <span data-ttu-id="1394a-108">Nástroje příkazového řádku najdete v umístění instalace sady Windows SDK, konkrétně</span><span class="sxs-lookup"><span data-stu-id="1394a-108">The command line tool can be found in the Windows SDK installation location, specifically,</span></span>  
  
 <span data-ttu-id="1394a-109">Foundation\wsatConfig.exe %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows komunikace</span><span class="sxs-lookup"><span data-stu-id="1394a-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\wsatConfig.exe</span></span>  
  
 <span data-ttu-id="1394a-110">Pokud používáte [!INCLUDE[wxp](../../../includes/wxp-md.md)] nebo [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], je nutné stáhnout aktualizace před spuštěním WsatConfig.exe.</span><span class="sxs-lookup"><span data-stu-id="1394a-110">If you are running [!INCLUDE[wxp](../../../includes/wxp-md.md)] or [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], you must download an update before running WsatConfig.exe.</span></span> <span data-ttu-id="1394a-111">Další informace o této aktualizaci najdete v tématu [aktualizace pro Commerce Server 2007 (KB912817)](http://go.microsoft.com/fwlink/?LinkId=95340) a [dostupnosti systému Windows XP modelu COM + opravu Hotfix kumulativní balíček 13](http://go.microsoft.com/fwlink/?LinkId=95341).</span><span class="sxs-lookup"><span data-stu-id="1394a-111">For more information about this update, see [Update for Commerce Server 2007 (KB912817)](http://go.microsoft.com/fwlink/?LinkId=95340) and [Availability of Windows XP COM+ Hotfix Rollup Package 13](http://go.microsoft.com/fwlink/?LinkId=95341).</span></span>  
  
 <span data-ttu-id="1394a-112">V následující tabulce jsou uvedeny možnosti, které lze použít s WS-AtomicTransaction Configuration Utility (wsatConfig.exe).</span><span class="sxs-lookup"><span data-stu-id="1394a-112">The following table shows the options that can be used with WS-AtomicTransaction Configuration Utility (wsatConfig.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1394a-113">Když nastavíte certifikát protokolu SSL pro vybraný port, můžete přepsat původní certifikát SSL přidružený tento port, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="1394a-113">When you set an SSL certificate for a selected port, you overwrite the original SSL certificate associated with that port if one exists.</span></span>  
  
|<span data-ttu-id="1394a-114">Možnosti</span><span class="sxs-lookup"><span data-stu-id="1394a-114">Options</span></span>|<span data-ttu-id="1394a-115">Popis</span><span class="sxs-lookup"><span data-stu-id="1394a-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1394a-116">-účty:\<účet ></span><span class="sxs-lookup"><span data-stu-id="1394a-116">-accounts:\<account,></span></span>|<span data-ttu-id="1394a-117">Určuje textový soubor s oddělovači seznam účtů, které se můžou zapojit v WS-AtomicTransaction.</span><span class="sxs-lookup"><span data-stu-id="1394a-117">Specifies a comma-separated list of accounts that can participate in WS-AtomicTransaction.</span></span> <span data-ttu-id="1394a-118">Platnost tyto účty není zaškrtnuto.</span><span class="sxs-lookup"><span data-stu-id="1394a-118">The validity of these accounts is not checked.</span></span>|  
|<span data-ttu-id="1394a-119">-accountsCerts:\<jezdec > &#124; " Issuer\SubjectName"></span><span class="sxs-lookup"><span data-stu-id="1394a-119">-accountsCerts:\<thumb>&#124;"Issuer\SubjectName",></span></span>|<span data-ttu-id="1394a-120">Určuje textový soubor s oddělovači seznam certifikátů, které se můžou zapojit v WS-AtomicTransaction.</span><span class="sxs-lookup"><span data-stu-id="1394a-120">Specifies a comma-separated list of certificates that can participate in WS-AtomicTransaction.</span></span> <span data-ttu-id="1394a-121">Certifikáty jsou vypsány kryptografický otisk nebo pár Issuer\SubjectName.</span><span class="sxs-lookup"><span data-stu-id="1394a-121">The certificates are indicated by thumbprint or by the Issuer\SubjectName pair.</span></span> <span data-ttu-id="1394a-122">Použijte {prázdný} pro název subjektu, pokud je prázdná.</span><span class="sxs-lookup"><span data-stu-id="1394a-122">Use {EMPTY} for subject name if it is empty.</span></span>|  
|<span data-ttu-id="1394a-123">-endpointCert: < počítač &#124; \<jezdec > &#124; " Issuer\SubjectName"></span><span class="sxs-lookup"><span data-stu-id="1394a-123">-endpointCert:<machine&#124;\<thumb>&#124;"Issuer\SubjectName"></span></span>|<span data-ttu-id="1394a-124">Používá certifikát počítače nebo jiné místní koncový bod certifikát určený kryptografickým otiskem nebo Issuer\SubjectName pár.</span><span class="sxs-lookup"><span data-stu-id="1394a-124">Uses the machine certificate or another local endpoint certificate specified by thumbprint or Issuer\SubjectName pair.</span></span> <span data-ttu-id="1394a-125">{PRÁZDNÝ} používá pro název subjektu, pokud je prázdná.</span><span class="sxs-lookup"><span data-stu-id="1394a-125">Uses {EMPTY} for the subject name if it is empty.</span></span>|  
|<span data-ttu-id="1394a-126">-maxTimeout:\<sekundu ></span><span class="sxs-lookup"><span data-stu-id="1394a-126">-maxTimeout:\<sec></span></span>|<span data-ttu-id="1394a-127">Určuje maximální časový limit v sekundách.</span><span class="sxs-lookup"><span data-stu-id="1394a-127">Specifies the maximum timeout in seconds.</span></span> <span data-ttu-id="1394a-128">Platné hodnoty jsou 0 až 3600.</span><span class="sxs-lookup"><span data-stu-id="1394a-128">Valid values are from 0 to 3600.</span></span>|  
|<span data-ttu-id="1394a-129">-sítě:\<povolit za &#124; zakázat ></span><span class="sxs-lookup"><span data-stu-id="1394a-129">-network:\<enable&#124;disable></span></span>|<span data-ttu-id="1394a-130">Povolí nebo zakáže podporu WS-AtomicTransaction sítě.</span><span class="sxs-lookup"><span data-stu-id="1394a-130">Enables or disables the WS-AtomicTransaction network support.</span></span>|  
|<span data-ttu-id="1394a-131">-port:\<portNum ></span><span class="sxs-lookup"><span data-stu-id="1394a-131">-port:\<portNum></span></span>|<span data-ttu-id="1394a-132">Nastaví HTTPS port pro WS-AtomicTransaction.</span><span class="sxs-lookup"><span data-stu-id="1394a-132">Sets the HTTPS port for WS-AtomicTransaction.</span></span><br /><br /> <span data-ttu-id="1394a-133">Pokud před spuštěním tohoto nástroje je již povolena brána firewall, port se automaticky registruje v seznamu výjimek.</span><span class="sxs-lookup"><span data-stu-id="1394a-133">If you have already enabled firewall before running this tool, the port is automatically registered in the exception list.</span></span> <span data-ttu-id="1394a-134">Pokud je brána firewall neaktivní před spuštěním tohoto nástroje, žádné další je nakonfigurovaná týkající se brány firewall.</span><span class="sxs-lookup"><span data-stu-id="1394a-134">If firewall is disabled before running this tool, nothing additional is configured regarding the firewall.</span></span><br /><br /> <span data-ttu-id="1394a-135">Pokud povolíte bránu firewall po dokončení konfigurace služby WS-AT, budete muset znovu spustit tento nástroj a zadejte číslo portu pomocí tohoto parametru.</span><span class="sxs-lookup"><span data-stu-id="1394a-135">If you enable firewall after configuring WS-AT, you have to run this tool again and supply the port number using this parameter.</span></span> <span data-ttu-id="1394a-136">Pokud zakážete po dokončení konfigurace brány firewall, WS-AT i nadále fungovat bez další vstup.</span><span class="sxs-lookup"><span data-stu-id="1394a-136">If you disable firewall after configuring, WS-AT continues to work without additional input.</span></span>|  
|<span data-ttu-id="1394a-137">-časový limit:\<sekundu ></span><span class="sxs-lookup"><span data-stu-id="1394a-137">-timeout:\<sec></span></span>|<span data-ttu-id="1394a-138">Určuje výchozí časový limit v sekundách.</span><span class="sxs-lookup"><span data-stu-id="1394a-138">Specifies the default timeout in seconds.</span></span> <span data-ttu-id="1394a-139">Platné hodnoty jsou 1 až 3600.</span><span class="sxs-lookup"><span data-stu-id="1394a-139">Valid values are from 1 to 3600.</span></span>|  
|<span data-ttu-id="1394a-140">-traceActivity:\<povolit za &#124; zakázat ></span><span class="sxs-lookup"><span data-stu-id="1394a-140">-traceActivity:\<enable&#124;disable></span></span>|<span data-ttu-id="1394a-141">Povolí nebo zakáže trasování událostí aktivity.</span><span class="sxs-lookup"><span data-stu-id="1394a-141">Enables or disables the tracing of activity events.</span></span>|  
|<span data-ttu-id="1394a-142">-traceLevel:\<vypnout &#124; Chyba &#124; Kritické &#124; Upozornění &#124; informace o &#124; Podrobné &#124; Všechny >}</span><span class="sxs-lookup"><span data-stu-id="1394a-142">-traceLevel:\<Off&#124;Error&#124;Critical&#124;Warning&#124;Information&#124; Verbose&#124;All>}</span></span>|<span data-ttu-id="1394a-143">Určuje úroveň trasování.</span><span class="sxs-lookup"><span data-stu-id="1394a-143">Specifies the trace level.</span></span>|  
|<span data-ttu-id="1394a-144">-tracePII:\<povolit za &#124; zakázat ></span><span class="sxs-lookup"><span data-stu-id="1394a-144">-tracePII:\<enable&#124;disable></span></span>|<span data-ttu-id="1394a-145">Povolí nebo zakáže trasování identifikovatelné osobní údaje.</span><span class="sxs-lookup"><span data-stu-id="1394a-145">Enables or disables the tracing of personally identifiable information.</span></span>|  
|<span data-ttu-id="1394a-146">-traceProp:\<povolit za &#124; zakázat ></span><span class="sxs-lookup"><span data-stu-id="1394a-146">-traceProp:\<enable&#124;disable></span></span>|<span data-ttu-id="1394a-147">Povolí nebo zakáže trasování událostí šíření.</span><span class="sxs-lookup"><span data-stu-id="1394a-147">Enables or disables the tracing of propagation events.</span></span>|  
|<span data-ttu-id="1394a-148">– restartování</span><span class="sxs-lookup"><span data-stu-id="1394a-148">-restart</span></span>|<span data-ttu-id="1394a-149">Restartování služby MSDTC aktivovat změny okamžitě.</span><span class="sxs-lookup"><span data-stu-id="1394a-149">Restarts MSDTC to activate changes immediately.</span></span> <span data-ttu-id="1394a-150">Pokud není zadáno, změny se projeví po restartování služby MS DTC.</span><span class="sxs-lookup"><span data-stu-id="1394a-150">If this is not specified, the changes take effect when MSDTC is restarted.</span></span>|  
|<span data-ttu-id="1394a-151">-Zobrazit</span><span class="sxs-lookup"><span data-stu-id="1394a-151">-show</span></span>|<span data-ttu-id="1394a-152">Zobrazí aktuální nastavení protokolu WS-AtomicTransaction.</span><span class="sxs-lookup"><span data-stu-id="1394a-152">Displays the current WS-AtomicTransaction protocol settings.</span></span>|  
|<span data-ttu-id="1394a-153">-virtuální_server:\<virtuální_server ></span><span class="sxs-lookup"><span data-stu-id="1394a-153">-virtualServer:\<virtualServer></span></span>|<span data-ttu-id="1394a-154">Určuje název prostředku clusteru DTC.</span><span class="sxs-lookup"><span data-stu-id="1394a-154">Specifies the DTC resource cluster name.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1394a-155">Viz také</span><span class="sxs-lookup"><span data-stu-id="1394a-155">See Also</span></span>  
 [<span data-ttu-id="1394a-156">Pomocí protokolu WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="1394a-156">Using WS-AtomicTransaction</span></span>](../../../docs/framework/wcf/feature-details/using-ws-atomictransaction.md)  
 [<span data-ttu-id="1394a-157">Konfigurace podpory protokolu WS-Atomic Transactions</span><span class="sxs-lookup"><span data-stu-id="1394a-157">Configuring WS-Atomic Transaction Support</span></span>](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)