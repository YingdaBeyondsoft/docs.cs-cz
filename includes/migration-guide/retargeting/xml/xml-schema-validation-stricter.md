### <a name="xml-schema-validation-is-stricter"></a><span data-ttu-id="8b7d0-101">Ověření schématu XML je přísnější</span><span class="sxs-lookup"><span data-stu-id="8b7d0-101">XML schema validation is stricter</span></span>

|   |   |
|---|---|
|<span data-ttu-id="8b7d0-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="8b7d0-102">Details</span></span>|<span data-ttu-id="8b7d0-103">V rozhraní .NET Framework 4.5 je více striktní ověřování schématu XML.</span><span class="sxs-lookup"><span data-stu-id="8b7d0-103">In the .NET Framework 4.5, XML schema validation is more strict.</span></span> <span data-ttu-id="8b7d0-104">Jestliže použijete xsd:anyURI k vyhodnocení URI jako protokolu e-mailu a v URI jsou mezery, vyhodnocení selže.</span><span class="sxs-lookup"><span data-stu-id="8b7d0-104">If you use xsd:anyURI to validate a URI such as a mailto protocol, validation fails if there are spaces in the URI.</span></span> <span data-ttu-id="8b7d0-105">V předchozích verzích rozhraní .NET Framework ověření proběhlo úspěšně.</span><span class="sxs-lookup"><span data-stu-id="8b7d0-105">In previous versions of the .NET Framework, validation succeeded.</span></span> <span data-ttu-id="8b7d0-106">Změna ovlivní pouze aplikace cílených rozhraní .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="8b7d0-106">The change affects only applications that target the .NET Framework 4.5.</span></span>|
|<span data-ttu-id="8b7d0-107">Návrh</span><span class="sxs-lookup"><span data-stu-id="8b7d0-107">Suggestion</span></span>|<span data-ttu-id="8b7d0-108">V případě potřeby Čím větší ověřování rozhraní .NET Framework 4.0 ověřování aplikace, můžete vybrat verzi rozhraní .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="8b7d0-108">If looser .NET Framework 4.0 validation is needed, the validating application can target version 4.0 of the .NET Framework.</span></span> <span data-ttu-id="8b7d0-109">Při přesměrování na rozhraní .NET 4.5, ale revize kódu je potřeba zajistit, že nejsou neplatné identifikátory URI (včetně mezer) očekávané jako hodnoty atributů s datovým typem anyURI.</span><span class="sxs-lookup"><span data-stu-id="8b7d0-109">When retargeting to .NET 4.5, however, code review should be done to be sure that invalid URIs (with spaces) are not expected as attribute values with the anyURI data type.</span></span>|
|<span data-ttu-id="8b7d0-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="8b7d0-110">Scope</span></span>|<span data-ttu-id="8b7d0-111">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="8b7d0-111">Minor</span></span>|
|<span data-ttu-id="8b7d0-112">Version</span><span class="sxs-lookup"><span data-stu-id="8b7d0-112">Version</span></span>|<span data-ttu-id="8b7d0-113">4.5</span><span class="sxs-lookup"><span data-stu-id="8b7d0-113">4.5</span></span>|
|<span data-ttu-id="8b7d0-114">Typ</span><span class="sxs-lookup"><span data-stu-id="8b7d0-114">Type</span></span>|<span data-ttu-id="8b7d0-115">Změna orientace</span><span class="sxs-lookup"><span data-stu-id="8b7d0-115">Retargeting</span></span>|
