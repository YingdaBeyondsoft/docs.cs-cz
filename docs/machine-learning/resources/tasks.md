---
title: Úkoly strojového učení
description: Prozkoumejte různé strojového učení úlohy v ML.NET podporovány.
ms.date: 06/04/2018
author: aditidugar
ms.author: johalex
ms.openlocfilehash: 22249ac2d275a4168dbd8b03b90d9698fe90f2d1
ms.sourcegitcommit: d8bf4976eafe3289275be3811e7cb721bfff7e1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "35017274"
---
# <a name="machine-learning-tasks"></a><span data-ttu-id="6b00d-103">Úkoly strojového učení</span><span class="sxs-lookup"><span data-stu-id="6b00d-103">Machine learning tasks</span></span>

<span data-ttu-id="6b00d-104">Při sestavování strojového učení modelu, musíte nejprve definovat, co jsou doufá k dosažení s daty.</span><span class="sxs-lookup"><span data-stu-id="6b00d-104">When building a machine learning model, you first need to define what you are hoping to achieve with your data.</span></span> <span data-ttu-id="6b00d-105">Po můžete si vybrat správné strojového učení úloh pro vaši situaci.</span><span class="sxs-lookup"><span data-stu-id="6b00d-105">After, you can pick the right machine learning task for your situation.</span></span> <span data-ttu-id="6b00d-106">Následující seznam popisuje různé strojového učení úlohy, které můžete vybrat z a některé běžné případy použití.</span><span class="sxs-lookup"><span data-stu-id="6b00d-106">The following list describes the different machine learning tasks that you can choose from and some common use cases.</span></span> 

> [!NOTE]
> <span data-ttu-id="6b00d-107">ML.NET je aktuálně ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="6b00d-107">ML.NET is currently in Preview.</span></span> <span data-ttu-id="6b00d-108">Ne všechny úkoly strojového učení jsou aktuálně podporovány.</span><span class="sxs-lookup"><span data-stu-id="6b00d-108">Not all machine learning tasks are currently supported.</span></span> <span data-ttu-id="6b00d-109">Chcete-li odeslat žádost o konkrétní úlohu, otevřete problém v [úložiště dotnet/machinelearning](https://github.com/dotnet/machinelearning/issues).</span><span class="sxs-lookup"><span data-stu-id="6b00d-109">To submit a request for a certain task, open an issue in the [dotnet/machinelearning repository](https://github.com/dotnet/machinelearning/issues).</span></span>

> [!NOTE]
> <span data-ttu-id="6b00d-110">ML.NET v současné době nepodporuje úkoly strojového učení s obrázky.</span><span class="sxs-lookup"><span data-stu-id="6b00d-110">Currently, ML.NET does not support machine learning tasks with images.</span></span> <span data-ttu-id="6b00d-111">Podpora budou přidané do budoucích verzí.</span><span class="sxs-lookup"><span data-stu-id="6b00d-111">Support will be added in future releases.</span></span> 

## <a name="binary-classification"></a><span data-ttu-id="6b00d-112">binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="6b00d-112">Binary classification</span></span>

<span data-ttu-id="6b00d-113">A [počítač učení se supervizí](glossary.md#supervised-machine-learning) úlohu, která je použít k předpovědi, které instance dat patří do dvou tříd (kategorie).</span><span class="sxs-lookup"><span data-stu-id="6b00d-113">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict which of two classes (categories) an instance of data belongs to.</span></span> <span data-ttu-id="6b00d-114">Vstup klasifikační algoritmus je sada s popiskem příklady, kde každý popisek je celé číslo 0 nebo 1.</span><span class="sxs-lookup"><span data-stu-id="6b00d-114">The input of a classification algorithm is a set of labeled examples, where each label is an integer of either 0 or 1.</span></span> <span data-ttu-id="6b00d-115">Výstup binární klasifikace algoritmem je třídění, který můžete použít k předpovědi třídu nové instance služby bez popisku.</span><span class="sxs-lookup"><span data-stu-id="6b00d-115">The output of a binary classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="6b00d-116">Příklady scénářů binární klasifikace:</span><span class="sxs-lookup"><span data-stu-id="6b00d-116">Examples of binary classification scenarios include:</span></span>

* <span data-ttu-id="6b00d-117">[Principy postojích Twitter komentářů](../tutorials/sentiment-analysis.md) jako "pozitivní" nebo "negativní".</span><span class="sxs-lookup"><span data-stu-id="6b00d-117">[Understanding sentiment of Twitter comments](../tutorials/sentiment-analysis.md) as either "positive" or "negative".</span></span>
* <span data-ttu-id="6b00d-118">Diagnostikování zda pacienta má určitá nákazy, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="6b00d-118">Diagnosing whether a patient has a certain disease or not.</span></span>
* <span data-ttu-id="6b00d-119">Rozhodování označit e-mailu jako "spamu", nebo ne.</span><span class="sxs-lookup"><span data-stu-id="6b00d-119">Making a decision to mark an email as "spam" or not.</span></span>

## <a name="multi-class-classification"></a><span data-ttu-id="6b00d-120">Klasifikace více – třída</span><span class="sxs-lookup"><span data-stu-id="6b00d-120">Multi-class classification</span></span>

<span data-ttu-id="6b00d-121">A [počítač učení se supervizí](glossary.md#supervised-machine-learning) úlohu, která se používá k předvídání – třída (kategorie) instance data.</span><span class="sxs-lookup"><span data-stu-id="6b00d-121">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the class (category) of an instance of data.</span></span> <span data-ttu-id="6b00d-122">Vstup klasifikační algoritmus je sada s popiskem příklady.</span><span class="sxs-lookup"><span data-stu-id="6b00d-122">The input of a classification algorithm is a set of labeled examples.</span></span> <span data-ttu-id="6b00d-123">Každý popisek je celé číslo mezi 0 a k-1, kde k je počet tříd.</span><span class="sxs-lookup"><span data-stu-id="6b00d-123">Each label is an integer between 0 and k-1, where k is the number of classes.</span></span> <span data-ttu-id="6b00d-124">Výstup klasifikační algoritmus je třídění, který můžete použít k předpovědi třídu nové instance služby bez popisku.</span><span class="sxs-lookup"><span data-stu-id="6b00d-124">The output of a classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="6b00d-125">Příklady scénářů více třída klasifikace:</span><span class="sxs-lookup"><span data-stu-id="6b00d-125">Examples of multi-class classification scenarios include:</span></span>

* <span data-ttu-id="6b00d-126">Zjišťuje se druh PSA jako "Siberian Husky", "Zlatá načítací modul pro", "Co", atd.</span><span class="sxs-lookup"><span data-stu-id="6b00d-126">Determining the breed of a dog as a "Siberian Husky", "Golden Retriever", "Poodle", etc.</span></span>
* <span data-ttu-id="6b00d-127">Principy film zkontroluje jako "pozitivní", "neutrální" nebo "negativní".</span><span class="sxs-lookup"><span data-stu-id="6b00d-127">Understanding movie reviews as "positive", "neutral", or "negative".</span></span>
* <span data-ttu-id="6b00d-128">Kategorizaci hotelů zkontroluje jako "místo", "cena", "čistoty", atd.</span><span class="sxs-lookup"><span data-stu-id="6b00d-128">Categorizing hotel reviews as "location", "price", "cleanliness", etc.</span></span>

## <a name="regression"></a><span data-ttu-id="6b00d-129">Regrese</span><span class="sxs-lookup"><span data-stu-id="6b00d-129">Regression</span></span>

<span data-ttu-id="6b00d-130">A [počítač učení se supervizí](glossary.md#supervised-machine-learning) úlohu, která se používá k předvídání hodnotu popisku ze sady souvisejících funkcí.</span><span class="sxs-lookup"><span data-stu-id="6b00d-130">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the value of the label from a set of related features.</span></span> <span data-ttu-id="6b00d-131">Popisek může být jakékoli skutečné hodnoty a nikoli z konečného počtu permutací nastavena hodnot jako klasifikace úlohy.</span><span class="sxs-lookup"><span data-stu-id="6b00d-131">The label can be of any real value and is not from a finite set of values as in classification tasks.</span></span> <span data-ttu-id="6b00d-132">Jsou nastaveny regresní model algoritmy závislost popisek na jeho souvisejících funkcí k určení, jak se změní štítek jako hodnoty funkcí.</span><span class="sxs-lookup"><span data-stu-id="6b00d-132">Regression algorithms model the dependency of the label on its related features to determine how the label will change as the values of the features are varied.</span></span> <span data-ttu-id="6b00d-133">Vstup regresní algoritmus je sada příklady s popisky známé hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6b00d-133">The input of a regression algorithm is a set of examples with labels of known values.</span></span> <span data-ttu-id="6b00d-134">Výstup regresní algoritmus je funkce, který můžete použít k předpovědi hodnotu popisku pro všechny nové sady vstupní funkcí.</span><span class="sxs-lookup"><span data-stu-id="6b00d-134">The output of a regression algorithm is a function, which you can use to predict the label value for any new set of input features.</span></span> <span data-ttu-id="6b00d-135">Příklady scénářů regrese:</span><span class="sxs-lookup"><span data-stu-id="6b00d-135">Examples of regression scenarios include:</span></span>

* <span data-ttu-id="6b00d-136">Předpověď ceny Domů na základě atributů úklidové jako Počet ložnic, umístění a velikost.</span><span class="sxs-lookup"><span data-stu-id="6b00d-136">Predicting house prices based on house attributes such as number of bedrooms, location, or size.</span></span>
* <span data-ttu-id="6b00d-137">Předpovídat budoucí uložených ceny na základě historických dat a aktuální vývoj trhu.</span><span class="sxs-lookup"><span data-stu-id="6b00d-137">Predicting future stock prices based on historical data and current market trends.</span></span>
* <span data-ttu-id="6b00d-138">Předpověď prodeje podle inzerování rozpočty produktu.</span><span class="sxs-lookup"><span data-stu-id="6b00d-138">Predicting sales of a product based on advertising budgets.</span></span>

> [!NOTE]
> <span data-ttu-id="6b00d-139">V současné době ML.NET je stále vytváření podporu pro regresní úlohy, které zahrnují časové řady.</span><span class="sxs-lookup"><span data-stu-id="6b00d-139">Currently, ML.NET is still building support for regression tasks that involve time series.</span></span>

## <a name="clustering"></a><span data-ttu-id="6b00d-140">Clustering</span><span class="sxs-lookup"><span data-stu-id="6b00d-140">Clustering</span></span>

<span data-ttu-id="6b00d-141">[Supervize počítač](glossary.md#unsupervised-machine-learning) úlohu, která se používá k skupiny instance dat do clusterů obsahující podobné charakteristiky.</span><span class="sxs-lookup"><span data-stu-id="6b00d-141">An [unsupervised machine learning](glossary.md#unsupervised-machine-learning) task that is used to group instances of data into clusters that contain similar characteristics.</span></span> <span data-ttu-id="6b00d-142">Clustering lze také identifikovat vztahy v datovou sadu, která nemusí být logicky podle procházení nebo jednoduše pozorování.</span><span class="sxs-lookup"><span data-stu-id="6b00d-142">Clustering can also be used to identify relationships in a dataset that you might not logically derive by browsing or simple observation.</span></span> <span data-ttu-id="6b00d-143">Vstupy a výstupy clustering algoritmu závisí na zvolené metody.</span><span class="sxs-lookup"><span data-stu-id="6b00d-143">The inputs and outputs of a clustering algorithm depends on the methodology chosen.</span></span> <span data-ttu-id="6b00d-144">Může trvat distribuce, těžiště, připojení nebo na základě hustotu přístup.</span><span class="sxs-lookup"><span data-stu-id="6b00d-144">You can take a distribution, centroid, connectivity, or density-based approach.</span></span> <span data-ttu-id="6b00d-145">ML.NET aktuálně podporuje použití clusteringu K-Means o přístupu na základě těžiště.</span><span class="sxs-lookup"><span data-stu-id="6b00d-145">ML.NET currently supports a centroid-based approach using K-Means clustering.</span></span> <span data-ttu-id="6b00d-146">Příklady scénáře clusteringu:</span><span class="sxs-lookup"><span data-stu-id="6b00d-146">Examples of clustering scenarios include:</span></span>

* <span data-ttu-id="6b00d-147">Principy segmenty hotelů hostů na základě zvyklosti a charakteristika hotelů volby.</span><span class="sxs-lookup"><span data-stu-id="6b00d-147">Understanding segments of hotel guests based on habits and characteristics of hotel choices.</span></span>
* <span data-ttu-id="6b00d-148">Identifikace segmenty zákazníků a demografie usnadňující tvorbu cílové reklamní kampaně.</span><span class="sxs-lookup"><span data-stu-id="6b00d-148">Identifying customer segments and demographics to help build targeted advertising campaigns.</span></span>
* <span data-ttu-id="6b00d-149">Kategorizaci inventáře podle výrobní metriky.</span><span class="sxs-lookup"><span data-stu-id="6b00d-149">Categorizing inventory based on manufacturing metrics.</span></span>

## <a name="anomaly-detection-coming-soon"></a><span data-ttu-id="6b00d-150">Detekce anomálií (*připravuje*)</span><span class="sxs-lookup"><span data-stu-id="6b00d-150">Anomaly detection (*coming soon*)</span></span>

## <a name="ranking-coming-soon"></a><span data-ttu-id="6b00d-151">Řazení (*připravuje*)</span><span class="sxs-lookup"><span data-stu-id="6b00d-151">Ranking (*coming soon*)</span></span>

## <a name="recommendation-coming-soon"></a><span data-ttu-id="6b00d-152">Doporučení (*připravuje*)</span><span class="sxs-lookup"><span data-stu-id="6b00d-152">Recommendation (*coming soon*)</span></span>
