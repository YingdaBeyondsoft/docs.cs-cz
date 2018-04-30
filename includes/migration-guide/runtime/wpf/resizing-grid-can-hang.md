### <a name="resizing-a-grid-can-hang"></a><span data-ttu-id="41f84-101">Změna velikosti mřížka může na</span><span class="sxs-lookup"><span data-stu-id="41f84-101">Resizing a Grid can hang</span></span>

|   |   |
|---|---|
|<span data-ttu-id="41f84-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="41f84-102">Details</span></span>|<span data-ttu-id="41f84-103">Nekonečná smyčka může dojít během rozložení <code>T:System.Windows.Controls.Grid</code> podle následujících okolností:</span><span class="sxs-lookup"><span data-stu-id="41f84-103">An infinite loop can occur during layout of a <code>T:System.Windows.Controls.Grid</code> under the following circumstances:</span></span><ul><li><span data-ttu-id="41f84-104">Definice řádků obsahovat dvě \*-řádků, jak deklarace MinHeight a MaxHeight.</span><span class="sxs-lookup"><span data-stu-id="41f84-104">Row definitions contain two \*-rows, both declaring a MinHeight and a MaxHeight.</span></span></li><li><span data-ttu-id="41f84-105">Obsah \*-řádky nepřekročí odpovídající MaxHeight</span><span class="sxs-lookup"><span data-stu-id="41f84-105">Content of the \*-rows doesn't exceed the corresponding MaxHeight</span></span></li><li><span data-ttu-id="41f84-106">K dispozici výška mřížky dojde k překročení první MinHeight (plus jakékoliv pevné nebo automaticky řádky)</span><span class="sxs-lookup"><span data-stu-id="41f84-106">The Grid's available height is exceeded by the first MinHeight (plus any other fixed or Auto rows)</span></span></li><li><span data-ttu-id="41f84-107">Aplikace .net 4.7 cílí nebo vyjádřit výslovný souhlas pro algoritmus 4.7 přidělení nastavením <code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code></span><span class="sxs-lookup"><span data-stu-id="41f84-107">The app targets .Net 4.7, or opts in to the 4.7 allocation algorithm by setting <code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code></span></span></li></ul><span data-ttu-id="41f84-108">Smyčky by také mohlo dojít s více než dva řádky nebo v případě podobá pro sloupce. Je problém vyřešen v rozhraní .net 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="41f84-108">The loop would also happen with more than two rows, or in the analogous case for columns.The issue is fixed in .Net 4.7.1.</span></span>|
|<span data-ttu-id="41f84-109">Návrh</span><span class="sxs-lookup"><span data-stu-id="41f84-109">Suggestion</span></span>|<span data-ttu-id="41f84-110">Upgrade na rozhraní .net 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="41f84-110">Upgrade to .Net 4.7.1.</span></span>  <span data-ttu-id="41f84-111">Případně pokud nepotřebujete algoritmus 4.7 přidělení můžete použít následující nastavení konfigurace:</span><span class="sxs-lookup"><span data-stu-id="41f84-111">Alternatively, if you don't need the 4.7 allocation algorithm you can use the following configuration setting:</span></span><pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="41f84-112">Rozsah</span><span class="sxs-lookup"><span data-stu-id="41f84-112">Scope</span></span>|<span data-ttu-id="41f84-113">Edge</span><span class="sxs-lookup"><span data-stu-id="41f84-113">Edge</span></span>|
|<span data-ttu-id="41f84-114">Version</span><span class="sxs-lookup"><span data-stu-id="41f84-114">Version</span></span>|<span data-ttu-id="41f84-115">4.7</span><span class="sxs-lookup"><span data-stu-id="41f84-115">4.7</span></span>|
|<span data-ttu-id="41f84-116">Typ</span><span class="sxs-lookup"><span data-stu-id="41f84-116">Type</span></span>|<span data-ttu-id="41f84-117">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="41f84-117">Runtime</span></span>|
