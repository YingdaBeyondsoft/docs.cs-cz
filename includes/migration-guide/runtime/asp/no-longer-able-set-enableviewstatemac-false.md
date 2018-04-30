### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a><span data-ttu-id="35676-101">Už moct EnableViewStateMac nastavena na hodnotu false</span><span class="sxs-lookup"><span data-stu-id="35676-101">No longer able to set EnableViewStateMac to false</span></span>

|   |   |
|---|---|
|<span data-ttu-id="35676-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="35676-102">Details</span></span>|<span data-ttu-id="35676-103">Technologie ASP.NET již umožňuje vývojářům zadejte <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> nebo <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>.</span><span class="sxs-lookup"><span data-stu-id="35676-103">ASP.NET no longer allows developers to specify <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> or <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>.</span></span> <span data-ttu-id="35676-104">V zobrazení stavu ověřovací kód zprávy (MAC) teď se vynucuje pro všechny požadavky s vložené zobrazení stavu.</span><span class="sxs-lookup"><span data-stu-id="35676-104">The view state message authentication code (MAC) is now enforced for all requests with embedded view state.</span></span> <span data-ttu-id="35676-105">Jenom aplikace, které explicitně nastavit vlastnost EnableViewStateMac na <code>false</code> vliv.</span><span class="sxs-lookup"><span data-stu-id="35676-105">Only apps that explicitly set the EnableViewStateMac property to <code>false</code> are affected.</span></span>|
|<span data-ttu-id="35676-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="35676-106">Suggestion</span></span>|<span data-ttu-id="35676-107">EnableViewStateMac musí předpokládat, že hodnota true a je třeba vyřešit případné chyby MAC (jak je popsáno v [v tomto návodu](https://support.microsoft.com/kb/2915218), která obsahuje více řešení v závislosti na tom, jaké jsou specifikace příčinu chyby MAC).</span><span class="sxs-lookup"><span data-stu-id="35676-107">EnableViewStateMac must be assumed to be true, and any resulting MAC errors must be resolved (as explained in [this guidance](https://support.microsoft.com/kb/2915218), which contains multiple resolutions depending on the specifics of what is causing MAC errors).</span></span>|
|<span data-ttu-id="35676-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="35676-108">Scope</span></span>|<span data-ttu-id="35676-109">Hlavní</span><span class="sxs-lookup"><span data-stu-id="35676-109">Major</span></span>|
|<span data-ttu-id="35676-110">Version</span><span class="sxs-lookup"><span data-stu-id="35676-110">Version</span></span>|<span data-ttu-id="35676-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="35676-111">4.5.2</span></span>|
|<span data-ttu-id="35676-112">Typ</span><span class="sxs-lookup"><span data-stu-id="35676-112">Type</span></span>|<span data-ttu-id="35676-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="35676-113">Runtime</span></span>|
