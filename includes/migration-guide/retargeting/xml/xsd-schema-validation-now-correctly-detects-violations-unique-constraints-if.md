### <a name="xsd-schema-validation-now-correctly-detects-violations-of-unique-constraints-if-compound-keys-are-used-and-one-key-is-empty"></a><span data-ttu-id="37d48-101">Ověření schématu XSD nyní správně rozpozná porušení jedinečné omezení, pokud složené klíče se používají a jeden klíč je prázdná</span><span class="sxs-lookup"><span data-stu-id="37d48-101">XSD Schema validation now correctly detects violations of unique constraints if compound keys are used and one key is empty</span></span>

|   |   |
|---|---|
|<span data-ttu-id="37d48-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="37d48-102">Details</span></span>|<span data-ttu-id="37d48-103">Verze rozhraní .NET Framework 4.6 obsahovala chybu, která způsobila ověření XSD není detekuje jedinečné omezení složené klíče, pokud jeden z klíčů byla prázdná.</span><span class="sxs-lookup"><span data-stu-id="37d48-103">Versions of the .NET Framework prior to 4.6 had a bug that caused XSD validation to not detect unique constraints on compound keys if one of the keys was empty.</span></span> <span data-ttu-id="37d48-104">V rozhraní .NET Framework 4.6 je tento problém vyřešen.</span><span class="sxs-lookup"><span data-stu-id="37d48-104">In the .NET Framework 4.6, this issue is corrected.</span></span> <span data-ttu-id="37d48-105">To bude mít za následek více správné ověření, ale také to může způsobit v některé XML není ověřování, které dříve by mít.</span><span class="sxs-lookup"><span data-stu-id="37d48-105">This will result in more correct validation, but it may also result in some XML not validating which previously would have.</span></span>|
|<span data-ttu-id="37d48-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="37d48-106">Suggestion</span></span>|<span data-ttu-id="37d48-107">V případě potřeby Čím větší ověřování rozhraní .NET Framework 4.0 ověřování aplikace, můžete vybrat verzi 4.5 (nebo starší) rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="37d48-107">If looser .NET Framework 4.0 validation is needed, the validating application can target version 4.5 (or earlier) of the .NET Framework.</span></span> <span data-ttu-id="37d48-108">Při přesměrování na rozhraní .NET 4.6, ale revize kódu potřeba zajistit, že duplicitní složené klíče (jak je popsáno v popisu tento problém) nejsou očekávané k ověření.</span><span class="sxs-lookup"><span data-stu-id="37d48-108">When retargeting to .NET 4.6, however, code review should be done to be sure that duplicate compound keys (as described in this issue's description) are not expected to validate.</span></span>|
|<span data-ttu-id="37d48-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="37d48-109">Scope</span></span>|<span data-ttu-id="37d48-110">Edge</span><span class="sxs-lookup"><span data-stu-id="37d48-110">Edge</span></span>|
|<span data-ttu-id="37d48-111">Version</span><span class="sxs-lookup"><span data-stu-id="37d48-111">Version</span></span>|<span data-ttu-id="37d48-112">4.6</span><span class="sxs-lookup"><span data-stu-id="37d48-112">4.6</span></span>|
|<span data-ttu-id="37d48-113">Typ</span><span class="sxs-lookup"><span data-stu-id="37d48-113">Type</span></span>|<span data-ttu-id="37d48-114">Změna orientace</span><span class="sxs-lookup"><span data-stu-id="37d48-114">Retargeting</span></span>|
