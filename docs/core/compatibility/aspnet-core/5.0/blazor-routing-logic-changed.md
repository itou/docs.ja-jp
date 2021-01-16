---
title: '破壊的変更:Blazor: Blazor アプリのルーティング ロジックの変更'
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: Blazor:Blazor アプリのルーティング ロジックの変更'
author: scottaddie
ms.author: scaddie
ms.date: 12/14/2020
ms.openlocfilehash: 4ab8289565c88b17eb204a11724bb12a09b033c2
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513507"
---
# <a name="blazor-route-precedence-logic-changed-in-blazor-apps"></a><span data-ttu-id="381fb-103">Blazor: Blazor アプリにおけるルート優先順位のロジックの変更</span><span class="sxs-lookup"><span data-stu-id="381fb-103">Blazor: Route precedence logic changed in Blazor apps</span></span>

<span data-ttu-id="381fb-104">Blazor のルーティング実装のバグによって、ルートの優先順位の決定方法が影響を受けました。</span><span class="sxs-lookup"><span data-stu-id="381fb-104">A bug in the Blazor routing implementation affected how the precedence of routes was determined.</span></span> <span data-ttu-id="381fb-105">このバグは、キャッチオール ルート、または Blazor アプリ内の省略可能なパラメーターを使用するルートに影響します。</span><span class="sxs-lookup"><span data-stu-id="381fb-105">This bug affects catch-all routes or routes with optional parameters within your Blazor app.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="381fb-106">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="381fb-106">Version introduced</span></span>

<span data-ttu-id="381fb-107">5.0.1</span><span class="sxs-lookup"><span data-stu-id="381fb-107">5.0.1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="381fb-108">以前の動作</span><span class="sxs-lookup"><span data-stu-id="381fb-108">Old behavior</span></span>

<span data-ttu-id="381fb-109">誤った動作により、優先順位の高いルートよりも優先順位の低いルートの方が先に検討され、照合されます。</span><span class="sxs-lookup"><span data-stu-id="381fb-109">With the erroneous behavior, routes with lower precedence are considered and matched over routes with higher precedence.</span></span> <span data-ttu-id="381fb-110">たとえば、`{*slug}` ルートが `/customer/{id}` よりも先に照合されます。</span><span class="sxs-lookup"><span data-stu-id="381fb-110">For example, the `{*slug}` route is matched before `/customer/{id}`.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="381fb-111">新しい動作</span><span class="sxs-lookup"><span data-stu-id="381fb-111">New behavior</span></span>

<span data-ttu-id="381fb-112">現在の動作は、ASP.NET Core アプリに定義されているルーティング動作により近くなりました。</span><span class="sxs-lookup"><span data-stu-id="381fb-112">The current behavior more closely matches the routing behavior defined in ASP.NET Core apps.</span></span> <span data-ttu-id="381fb-113">このフレームワークにより、まず各セグメントのルートの優先順位が決まります。</span><span class="sxs-lookup"><span data-stu-id="381fb-113">The framework determines the route precedence for each segment first.</span></span> <span data-ttu-id="381fb-114">ルートの長さは、優先順位が同じ場合の 2 番目の条件としてのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="381fb-114">The route's length is used only as a second criteria to break ties.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="381fb-115">変更理由</span><span class="sxs-lookup"><span data-stu-id="381fb-115">Reason for change</span></span>

<span data-ttu-id="381fb-116">元の動作は、実装のバグと考えられています。</span><span class="sxs-lookup"><span data-stu-id="381fb-116">The original behavior is considered a bug in the implementation.</span></span> <span data-ttu-id="381fb-117">目標として、Blazor アプリのルーティング システムは、ASP.NET Core の他の部分のルーティング システムと同じように動作する必要があります。</span><span class="sxs-lookup"><span data-stu-id="381fb-117">As a goal, the routing system in Blazor apps should behave the same way as the routing system in the rest of ASP.NET Core.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="381fb-118">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="381fb-118">Recommended action</span></span>

<span data-ttu-id="381fb-119">以前のバージョンの Blazor から 5.x にアップグレードする場合は、`Router` コンポーネントの `PreferExactMatches` 属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="381fb-119">If upgrading from previous versions of Blazor to 5.x, use the `PreferExactMatches` attribute on the `Router` component.</span></span> <span data-ttu-id="381fb-120">この属性を使用して、正しい動作を選択できます。</span><span class="sxs-lookup"><span data-stu-id="381fb-120">This attribute can be used to opt into the correct behavior.</span></span> <span data-ttu-id="381fb-121">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="381fb-121">For example:</span></span>

```razor
<Router AppAssembly="@typeof(Program).Assembly" PreferExactMatches="true">
```

<span data-ttu-id="381fb-122">`PreferExactMatches` が `true` に設定されている場合、ルートの照合時にワイルドカードよりも完全一致が優先されます。</span><span class="sxs-lookup"><span data-stu-id="381fb-122">When `PreferExactMatches` is set to `true`, route matching prefers exact matches over wildcards.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="381fb-123">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="381fb-123">Affected APIs</span></span>

<span data-ttu-id="381fb-124">なし</span><span class="sxs-lookup"><span data-stu-id="381fb-124">None</span></span>

<!--

## Category

ASP.NET Core

## Affected APIs

Not detectable via API analysis

-->