---
title: System.Text.Json でプロパティを無視する方法
description: .NET の System.Text.Json を使用してシリアル化するときにプロパティを無視する方法について説明します。
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 6d703156d50a3e00a33cea5e15be2df911ed7c1b
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97008813"
---
# <a name="how-to-ignore-properties-with-no-locsystemtextjson"></a><span data-ttu-id="a406d-103">System.Text.Json でプロパティを無視する方法</span><span class="sxs-lookup"><span data-stu-id="a406d-103">How to ignore properties with System.Text.Json</span></span>

<span data-ttu-id="a406d-104">C# オブジェクトを JavaScript Object Notation (JSON) にシリアル化する場合、既定では、すべてのパブリック プロパティがシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="a406d-104">When serializing C# objects to JavaScript Object Notation (JSON), by default, all public properties are serialized.</span></span> <span data-ttu-id="a406d-105">生成される JSON にその一部を出現させないようにするには、いくつかのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="a406d-105">If you don't want some of them to appear in the resulting JSON, you have several options.</span></span> <span data-ttu-id="a406d-106">この記事では、さまざまな条件に基づいてプロパティを無視する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a406d-106">In this article you learn how to ignore properties based on various criteria:</span></span>

::: zone pivot="dotnet-5-0"

* [<span data-ttu-id="a406d-107">個々のプロパティ</span><span class="sxs-lookup"><span data-stu-id="a406d-107">Individual properties</span></span>](#ignore-individual-properties)
* [<span data-ttu-id="a406d-108">すべての読み取り専用プロパティ</span><span class="sxs-lookup"><span data-stu-id="a406d-108">All read-only properties</span></span>](#ignore-all-read-only-properties)
* [<span data-ttu-id="a406d-109">すべての null 値プロパティ</span><span class="sxs-lookup"><span data-stu-id="a406d-109">All null-value properties</span></span>](#ignore-all-null-value-properties)
* [<span data-ttu-id="a406d-110">すべての既定値のプロパティ</span><span class="sxs-lookup"><span data-stu-id="a406d-110">All default-value properties</span></span>](#ignore-all-default-value-properties)
::: zone-end

::: zone pivot="dotnet-core-3-1"

* [<span data-ttu-id="a406d-111">個々のプロパティ</span><span class="sxs-lookup"><span data-stu-id="a406d-111">Individual properties</span></span>](#ignore-individual-properties)
* [<span data-ttu-id="a406d-112">すべての読み取り専用プロパティ</span><span class="sxs-lookup"><span data-stu-id="a406d-112">All read-only properties</span></span>](#ignore-all-read-only-properties)
* [<span data-ttu-id="a406d-113">すべての null 値プロパティ</span><span class="sxs-lookup"><span data-stu-id="a406d-113">All null-value properties</span></span>](#ignore-all-null-value-properties)
::: zone-end

## <a name="ignore-individual-properties"></a><span data-ttu-id="a406d-114">個々のプロパティを無視する</span><span class="sxs-lookup"><span data-stu-id="a406d-114">Ignore individual properties</span></span>

<span data-ttu-id="a406d-115">個々のプロパティを無視するには、[[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) 属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="a406d-115">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="a406d-116">シリアル化する型と JSON 出力の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a406d-116">Here's an example type to serialize and JSON output:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithIgnoreAttribute":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

::: zone pivot="dotnet-5-0"
<span data-ttu-id="a406d-117">[[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) 属性の `Condition` プロパティを設定することによって、条件付き除外を指定できます。</span><span class="sxs-lookup"><span data-stu-id="a406d-117">You can specify conditional exclusion by setting the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute's `Condition` property.</span></span> <span data-ttu-id="a406d-118"><xref:System.Text.Json.Serialization.JsonIgnoreCondition> 列挙型には、次のオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="a406d-118">The <xref:System.Text.Json.Serialization.JsonIgnoreCondition> enum provides the following options:</span></span>

* <span data-ttu-id="a406d-119">`Always` - プロパティを常に無視します。</span><span class="sxs-lookup"><span data-stu-id="a406d-119">`Always` - The property is always ignored.</span></span> <span data-ttu-id="a406d-120">`Condition` を指定しないと、このオプションが想定されます。</span><span class="sxs-lookup"><span data-stu-id="a406d-120">If no `Condition` is specified, this option is assumed.</span></span>
* <span data-ttu-id="a406d-121">`Never` - グローバル設定 `DefaultIgnoreCondition`、`IgnoreReadOnlyProperties`、`IgnoreReadOnlyFields` に関係なく、プロパティは常にシリアル化および逆シリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="a406d-121">`Never` - The property is always serialized and deserialized, regardless of the `DefaultIgnoreCondition`, `IgnoreReadOnlyProperties`, and `IgnoreReadOnlyFields` global settings.</span></span>
* <span data-ttu-id="a406d-122">`WhenWritingDefault` - プロパティが参照型 `null`、null 許容値型 `null`、または値型 `default` の場合、シリアル化時に無視されます。</span><span class="sxs-lookup"><span data-stu-id="a406d-122">`WhenWritingDefault` - The property is ignored on serialization if it's a reference type `null`, a nullable value type `null`, or a value type `default`.</span></span>
* <span data-ttu-id="a406d-123">`WhenWritingNull` - プロパティが参照型 `null` または null 許容値型 `null` の場合、シリアル化時に無視されます。</span><span class="sxs-lookup"><span data-stu-id="a406d-123">`WhenWritingNull` - The property is ignored on serialization if it's a reference type `null`, or a nullable value type `null`.</span></span>

<span data-ttu-id="a406d-124">次の例では、[[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) 属性の `Condition` プロパティの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a406d-124">The following example illustrates use of the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute's `Condition` property:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/JsonIgnoreAttributeExample.cs" highlight="10,13,16":::
::: zone-end

## <a name="ignore-all-read-only-properties"></a><span data-ttu-id="a406d-125">すべての読み取り専用プロパティを無視する</span><span class="sxs-lookup"><span data-stu-id="a406d-125">Ignore all read-only properties</span></span>

<span data-ttu-id="a406d-126">パブリック ゲッターが含まれていてもパブリック セッターがない場合、プロパティは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="a406d-126">A property is read-only if it contains a public getter but not a public setter.</span></span> <span data-ttu-id="a406d-127">シリアル化のときにすべての読み取り専用プロパティを無視するには、次の例で示されているように、<xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="a406d-127">To ignore all read-only properties when serializing, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeExcludeReadOnlyProperties.cs" id="Serialize":::

<span data-ttu-id="a406d-128">シリアル化する型と JSON 出力の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a406d-128">Here's an example type to serialize and JSON output:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithROProperty":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="a406d-129">このオプションは、シリアル化にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="a406d-129">This option applies only to serialization.</span></span> <span data-ttu-id="a406d-130">逆シリアル化中、既定では読み取り専用プロパティが無視されます。</span><span class="sxs-lookup"><span data-stu-id="a406d-130">During deserialization, read-only properties are ignored by default.</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="a406d-131">このオプションは、プロパティにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="a406d-131">This option applies only to properties.</span></span> <span data-ttu-id="a406d-132">[フィールドをシリアル化する](system-text-json-how-to.md#include-fields)ときに読み取り専用フィールドを無視するには、<xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> グローバル設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="a406d-132">To ignore read-only fields when [serializing fields](system-text-json-how-to.md#include-fields), use the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> global setting.</span></span>
::: zone-end

## <a name="ignore-all-null-value-properties"></a><span data-ttu-id="a406d-133">すべての null 値プロパティを無視する</span><span class="sxs-lookup"><span data-stu-id="a406d-133">Ignore all null-value properties</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="a406d-134">すべての null 値プロパティを無視するには、次の例で示されているように、<xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> プロパティを <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingNull> に設定します。</span><span class="sxs-lookup"><span data-stu-id="a406d-134">To ignore all null-value properties, set the <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> property to <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingNull>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreNullOnSerialize.cs" highlight="28":::

::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="a406d-135">シリアル化のときにすべての null 値プロパティを無視するには、次の例で示されているように、<xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="a406d-135">To ignore all null-value properties when serializing, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeExcludeNullValueProperties.cs" id="Serialize":::

<span data-ttu-id="a406d-136">シリアル化するオブジェクトと JSON 出力の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a406d-136">Here's an example object to serialize and JSON output:</span></span>

| <span data-ttu-id="a406d-137">プロパティ</span><span class="sxs-lookup"><span data-stu-id="a406d-137">Property</span></span>             | <span data-ttu-id="a406d-138">値</span><span class="sxs-lookup"><span data-stu-id="a406d-138">Value</span></span>                         |
|----------------------|-------------------------------|
| `Date`               | `8/1/2019 12:00:00 AM -07:00` |
| `TemperatureCelsius` | `25`                          |
| `Summary`            | `null`                        |

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

::: zone-end

## <a name="ignore-all-default-value-properties"></a><span data-ttu-id="a406d-139">既定値のプロパティをすべて無視する</span><span class="sxs-lookup"><span data-stu-id="a406d-139">Ignore all default-value properties</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="a406d-140">値型プロパティで既定値がシリアル化されないようにするには、次の例で示されているように、<xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> プロパティを <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault> に設定します。</span><span class="sxs-lookup"><span data-stu-id="a406d-140">To prevent serialization of default values in value type properties, set the <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> property to <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreValueDefaultOnSerialize.cs" highlight="28":::
::: zone-end

<span data-ttu-id="a406d-141"><xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault> を設定すると、null 値参照型および null 許容値型のプロパティもシリアル化されなくなります。</span><span class="sxs-lookup"><span data-stu-id="a406d-141">The <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault> setting also prevents serialization of null-value reference type and nullable value type properties.</span></span>

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="a406d-142">.NET Core 3.1 の `System.Text.Json` で、値型の既定値のプロパティがシリアル化されないようにするための組み込みの方法はありません。</span><span class="sxs-lookup"><span data-stu-id="a406d-142">There is no built-in way to prevent serialization of properties with value type defaults in `System.Text.Json` in .NET Core 3.1.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="a406d-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="a406d-143">See also</span></span>

* [<span data-ttu-id="a406d-144">System.Text.Json の概要</span><span class="sxs-lookup"><span data-stu-id="a406d-144">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="a406d-145">JSON をシリアル化および逆シリアル化する方法</span><span class="sxs-lookup"><span data-stu-id="a406d-145">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="a406d-146">JsonSerializerOptions インスタンスのインスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="a406d-146">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="a406d-147">大文字と小文字を区別しない一致を有効にする</span><span class="sxs-lookup"><span data-stu-id="a406d-147">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="a406d-148">プロパティの名前と値をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="a406d-148">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="a406d-149">無効な JSON を許可する</span><span class="sxs-lookup"><span data-stu-id="a406d-149">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="a406d-150">オーバーフロー JSON の処理</span><span class="sxs-lookup"><span data-stu-id="a406d-150">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="a406d-151">参照を保持する</span><span class="sxs-lookup"><span data-stu-id="a406d-151">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="a406d-152">変更できない型と非パブリック アクセサー</span><span class="sxs-lookup"><span data-stu-id="a406d-152">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="a406d-153">ポリモーフィックなシリアル化</span><span class="sxs-lookup"><span data-stu-id="a406d-153">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="a406d-154">Newtonsoft.Json から System.Text.Json に移行する</span><span class="sxs-lookup"><span data-stu-id="a406d-154">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="a406d-155">文字エンコードをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="a406d-155">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="a406d-156">カスタム シリアライザーと逆シリアライザーを作成する</span><span class="sxs-lookup"><span data-stu-id="a406d-156">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="a406d-157">JSON シリアル化のためのカスタム コンバーターの作成</span><span class="sxs-lookup"><span data-stu-id="a406d-157">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="a406d-158">DateTime および DateTimeOffset のサポート</span><span class="sxs-lookup"><span data-stu-id="a406d-158">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="a406d-159">[System.Text.Json API リファレンス](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="a406d-159">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="a406d-160">[System.Text.Json.Serialization API リファレンス](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="a406d-160">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>