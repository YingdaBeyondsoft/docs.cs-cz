### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a><span data-ttu-id="2ffcc-101">WPF windows vykreslují bez výstřižek rozšíření mimo jednoho monitoru</span><span class="sxs-lookup"><span data-stu-id="2ffcc-101">WPF windows are rendered without clipping when extending outside a single monitor</span></span>

|   |   |
|---|---|
|<span data-ttu-id="2ffcc-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="2ffcc-102">Details</span></span>|<span data-ttu-id="2ffcc-103">V rozhraní .NET Framework 4.6 běžícím na systému Windows 8 a vyšší, vykreslením celé okno bez výstřižek, když ji rozšiřuje mimo jednoho zobrazení ve scénáři s více monitorování.</span><span class="sxs-lookup"><span data-stu-id="2ffcc-103">In the .NET Framework 4.6 running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span> <span data-ttu-id="2ffcc-104">To se liší od předchozích verzí rozhraní .NET Framework, které by v případě potřeby upraví WPF windows, které i po uplynutí jednoho zobrazení.</span><span class="sxs-lookup"><span data-stu-id="2ffcc-104">This is different from previous versions of the .NET Framework which would clip WPF windows that extended beyond a single display.</span></span>|
|<span data-ttu-id="2ffcc-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="2ffcc-105">Suggestion</span></span>|<span data-ttu-id="2ffcc-106">Toto chování (ať už k oříznutí nebo ne) může být explicitně nastaveny pomocí <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> element v <code>&lt;appSettings&gt;</code> v konfiguračním souboru aplikace, nebo nastavením <code>EnableMultiMonitorDisplayClipping</code> vlastnost při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="2ffcc-106">This behavior (whether to clip or not) can be explicitly set using the <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> element in <code>&lt;appSettings&gt;</code> in an application's configuration file, or by setting the <code>EnableMultiMonitorDisplayClipping</code> property at app startup.</span></span>|
|<span data-ttu-id="2ffcc-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="2ffcc-107">Scope</span></span>|<span data-ttu-id="2ffcc-108">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="2ffcc-108">Minor</span></span>|
|<span data-ttu-id="2ffcc-109">Version</span><span class="sxs-lookup"><span data-stu-id="2ffcc-109">Version</span></span>|<span data-ttu-id="2ffcc-110">4.6</span><span class="sxs-lookup"><span data-stu-id="2ffcc-110">4.6</span></span>|
|<span data-ttu-id="2ffcc-111">Typ</span><span class="sxs-lookup"><span data-stu-id="2ffcc-111">Type</span></span>|<span data-ttu-id="2ffcc-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="2ffcc-112">Runtime</span></span>|
