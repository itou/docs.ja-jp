---
ms.openlocfilehash: 5b49dcae45e44bfd9ec3e150ad25c3f21d62c18e
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955339"
---
### <a name="jsonserializerserialize-throws-argumentnullexception-when-type-parameter-is-null"></a><span data-ttu-id="5820b-101">型パラメーターが null の場合に JsonSerializer.Serialize によって ArgumentNullException がスローされる</span><span class="sxs-lookup"><span data-stu-id="5820b-101">JsonSerializer.Serialize throws ArgumentNullException when type parameter is null</span></span>

<span data-ttu-id="5820b-102"><xref:System.Type> パラメーターに `null` が渡されるたびに、<xref:System.Type> パラメーターを持つ <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>、<xref:System.Text.Json.JsonSerializer.SerializeAsync%2A?displayProperty=nameWithType>、<xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> のオーバーロードによって <xref:System.ArgumentNullException> がスローされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="5820b-102"><xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>, <xref:System.Text.Json.JsonSerializer.SerializeAsync%2A?displayProperty=nameWithType>, and <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> overloads that have a <xref:System.Type> parameter now throw an <xref:System.ArgumentNullException> whenever `null` is passed for the <xref:System.Type> parameter.</span></span>

#### <a name="change-description"></a><span data-ttu-id="5820b-103">変更内容</span><span class="sxs-lookup"><span data-stu-id="5820b-103">Change description</span></span>

<span data-ttu-id="5820b-104">.NET Core 3.1 では、`Type inputType` パラメーターに `null` が渡されると、<xref:System.Type> パラメーターを持つ <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>、<xref:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType>、<xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> のオーバーロードによって <xref:System.ArgumentNullException> がスローされますが、`Object value` パラメーターも `null` の場合はされません。</span><span class="sxs-lookup"><span data-stu-id="5820b-104">In .NET Core 3.1, the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>, <xref:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType>, and <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> overloads that have a <xref:System.Type> parameter throw an <xref:System.ArgumentNullException> when `null` is passed for the `Type inputType` parameter, but not if the `Object value` parameter is also `null`.</span></span> <span data-ttu-id="5820b-105">.NET 5.0 以降では、`null` が <xref:System.Type> パラメーターに渡されると、これらのメソッドによって "*常に*" <xref:System.ArgumentNullException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="5820b-105">Starting in .NET 5.0, these methods *always* throw an <xref:System.ArgumentNullException> when `null` is passed for the <xref:System.Type> parameter.</span></span>

<span data-ttu-id="5820b-106">.NET Core 3.1 での動作:</span><span class="sxs-lookup"><span data-stu-id="5820b-106">Behavior in .NET Core 3.1:</span></span>

```csharp
// Returns a string with value "null".
JsonSerializer.Serialize(null, null);

// Returns a byte array with value "null".
JsonSerializer.SerializeToUtf8Bytes(null, null);
```

<span data-ttu-id="5820b-107">.NET 5.0 以降での動作:</span><span class="sxs-lookup"><span data-stu-id="5820b-107">Behavior in .NET 5.0 and later:</span></span>

```csharp
// Throws ArgumentNullException: "Value cannot be null. (Parameter 'inputType')".
JsonSerializer.Serialize(null, null);

// Throws ArgumentNullException: "Value cannot be null. (Parameter 'inputType')".
JsonSerializer.SerializeToUtf8Bytes(null, null);
```

#### <a name="version-introduced"></a><span data-ttu-id="5820b-108">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="5820b-108">Version introduced</span></span>

<span data-ttu-id="5820b-109">5.0</span><span class="sxs-lookup"><span data-stu-id="5820b-109">5.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="5820b-110">変更理由</span><span class="sxs-lookup"><span data-stu-id="5820b-110">Reason for change</span></span>

<span data-ttu-id="5820b-111">`Type inputType` パラメーターに `null` を渡すことは許容されておらず、常に <xref:System.ArgumentNullException> をスローする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5820b-111">Passing in `null` for the `Type inputType` parameter is unacceptable and should always throw an <xref:System.ArgumentNullException>.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5820b-112">推奨される操作</span><span class="sxs-lookup"><span data-stu-id="5820b-112">Recommended action</span></span>

<span data-ttu-id="5820b-113">これらのメソッドの `Type inputType` パラメーターに `null` が渡されていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="5820b-113">Make sure that you are not passing `null` for the `Type inputType` parameter of these methods.</span></span>

#### <a name="category"></a><span data-ttu-id="5820b-114">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="5820b-114">Category</span></span>

<span data-ttu-id="5820b-115">シリアル化</span><span class="sxs-lookup"><span data-stu-id="5820b-115">Serialization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5820b-116">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="5820b-116">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Serialize(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.Serialize(System.Text.Json.Utf8JsonWriter,System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Text.Json.JsonSerializer.Serialize(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)`
- `M:System.Text.Json.JsonSerializer.Serialize(System.Text.Json.Utf8JsonWriter,System.Object,System.Type,System.Text.Json.JsonSerializerOptions)`
- `M:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)`
- `M:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)`

-->