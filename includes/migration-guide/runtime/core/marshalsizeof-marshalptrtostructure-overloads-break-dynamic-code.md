### <a name="marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a><span data-ttu-id="a0b64-101">Marshal.SizeOf a Marshal.PtrToStructure přetížení rozdělit dynamický kód</span><span class="sxs-lookup"><span data-stu-id="a0b64-101">Marshal.SizeOf and Marshal.PtrToStructure overloads break dynamic code</span></span>

|   |   |
|---|---|
|<span data-ttu-id="a0b64-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="a0b64-102">Details</span></span>|<span data-ttu-id="a0b64-103">Od verze rozhraní .NET Framework 4.5.1, dynamické vazby metody <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601>, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)>, nebo <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)>, (pomocí prostředí Windows PowerShell, IronPython nebo C# dynamické klíčové slovo, např.) může mít za následek <code>MethodInvocationExceptions</code> vzhledem k tomu, že byly přidány nové přetížení těchto metod, které mohou být nejednoznačný k skriptovacích strojů.</span><span class="sxs-lookup"><span data-stu-id="a0b64-103">Beginning in the .NET Framework 4.5.1, dynamically binding to the methods <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601>, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)>, or <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)>, (via Windows PowerShell, IronPython, or the C# dynamic keyword, for example) can result in <code>MethodInvocationExceptions</code> because new overloads of these methods have been added that may be ambiguous to the scripting engines.</span></span>|
|<span data-ttu-id="a0b64-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="a0b64-104">Suggestion</span></span>|<span data-ttu-id="a0b64-105">Aktualizace skriptů jasně znamenat přetížení, které je třeba použít.</span><span class="sxs-lookup"><span data-stu-id="a0b64-105">Update scripts to clearly indicate which overload should be used.</span></span> <span data-ttu-id="a0b64-106">To může obvykle provádí explicitně přetypování parametry typu tyto metody jako <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="a0b64-106">This can typically done by explicitly casting the methods' type parameters as <xref:System.Type>.</span></span> <span data-ttu-id="a0b64-107">V tématu [tento odkaz](https://support.microsoft.com/kb/2909958/) další podrobnosti a příklady, jak vyřešit problém.</span><span class="sxs-lookup"><span data-stu-id="a0b64-107">See [this link](https://support.microsoft.com/kb/2909958/) for more detail and examples of how to workaround the issue.</span></span>|
|<span data-ttu-id="a0b64-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="a0b64-108">Scope</span></span>|<span data-ttu-id="a0b64-109">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="a0b64-109">Minor</span></span>|
|<span data-ttu-id="a0b64-110">Version</span><span class="sxs-lookup"><span data-stu-id="a0b64-110">Version</span></span>|<span data-ttu-id="a0b64-111">4.5.1</span><span class="sxs-lookup"><span data-stu-id="a0b64-111">4.5.1</span></span>|
|<span data-ttu-id="a0b64-112">Typ</span><span class="sxs-lookup"><span data-stu-id="a0b64-112">Type</span></span>|<span data-ttu-id="a0b64-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="a0b64-113">Runtime</span></span>|
