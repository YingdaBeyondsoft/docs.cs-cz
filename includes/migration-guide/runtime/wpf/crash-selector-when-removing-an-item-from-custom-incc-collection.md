### <a name="crash-in-selector-when-removing-an-item-from-a-custom-incc-collection"></a><span data-ttu-id="881b8-101">Při odebírání položky z kolekce vlastní INCC havárií v selektoru</span><span class="sxs-lookup"><span data-stu-id="881b8-101">Crash in Selector when removing an item from a custom INCC collection</span></span>

|   |   |
|---|---|
|<span data-ttu-id="881b8-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="881b8-102">Details</span></span>|<span data-ttu-id="881b8-103"><code>T:System.InvalidOperationException</code> Situace může nastat v následujícím scénáři:</span><span class="sxs-lookup"><span data-stu-id="881b8-103">An <code>T:System.InvalidOperationException</code> can occur in the following scenario:</span></span><ul><li><span data-ttu-id="881b8-104">Položka ItemsSource pro <code>T:System.Windows.Controls.Primitives.Selector</code> je kolekce s vlastní implementaci <code>T:System.Collections.Specialized.INotifyCollectionChanged</code>.</span><span class="sxs-lookup"><span data-stu-id="881b8-104">The ItemsSource for a <code>T:System.Windows.Controls.Primitives.Selector</code> is a collection with a custom implementation of <code>T:System.Collections.Specialized.INotifyCollectionChanged</code>.</span></span></li><li><span data-ttu-id="881b8-105">Vybraná položka je odebrána z kolekce.</span><span class="sxs-lookup"><span data-stu-id="881b8-105">The selected item is removed from the collection.</span></span></li><li><span data-ttu-id="881b8-106"><code>T:System.Collections.Specialized.NotifyCollectionChangedEventArgs</code> Má <code>P:System.Collections.Specialized.NotifyCollectionChangedEventArgs.OldStartingIndex</code> = -1 (označující Neznámý pozice).</span><span class="sxs-lookup"><span data-stu-id="881b8-106">The <code>T:System.Collections.Specialized.NotifyCollectionChangedEventArgs</code> has <code>P:System.Collections.Specialized.NotifyCollectionChangedEventArgs.OldStartingIndex</code> = -1 (indicating an unknown position).</span></span></li></ul><span data-ttu-id="881b8-107">Zásobník volání v výjimky začíná na System.Windows.Threading.Dispatcher.VerifyAccess() v System.Windows.DependencyObject.GetValue (Vlastnost DependencyProperty distribučního bodu) v System.Windows.Controls.Primitives.Selector.GetIsSelected (DependencyObject Element) této výjimce může dojít v rozhraní .net 4.5, pokud aplikace má více než jedno vlákno dispečera.</span><span class="sxs-lookup"><span data-stu-id="881b8-107">The exception's callstack begins at System.Windows.Threading.Dispatcher.VerifyAccess() at System.Windows.DependencyObject.GetValue(DependencyProperty dp) at System.Windows.Controls.Primitives.Selector.GetIsSelected(DependencyObject element)This exception can occur in .Net 4.5 if the application has more than one Dispatcher thread.</span></span> <span data-ttu-id="881b8-108">V rozhraní .net 4.7 výjimka může dojít také v aplikacích s jedním vláknem dispečera.</span><span class="sxs-lookup"><span data-stu-id="881b8-108">In .Net 4.7 the exception can also occur in applications with a single Dispatcher thread.</span></span> <span data-ttu-id="881b8-109">Je problém vyřešen v rozhraní .net 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="881b8-109">The issue is fixed in .Net 4.7.1.</span></span>|
|<span data-ttu-id="881b8-110">Návrh</span><span class="sxs-lookup"><span data-stu-id="881b8-110">Suggestion</span></span>|<span data-ttu-id="881b8-111">Upgrade na rozhraní .net 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="881b8-111">Upgrade to .Net 4.7.1.</span></span>|
|<span data-ttu-id="881b8-112">Rozsah</span><span class="sxs-lookup"><span data-stu-id="881b8-112">Scope</span></span>|<span data-ttu-id="881b8-113">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="881b8-113">Minor</span></span>|
|<span data-ttu-id="881b8-114">Version</span><span class="sxs-lookup"><span data-stu-id="881b8-114">Version</span></span>|<span data-ttu-id="881b8-115">4.7</span><span class="sxs-lookup"><span data-stu-id="881b8-115">4.7</span></span>|
|<span data-ttu-id="881b8-116">Typ</span><span class="sxs-lookup"><span data-stu-id="881b8-116">Type</span></span>|<span data-ttu-id="881b8-117">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="881b8-117">Runtime</span></span>|
