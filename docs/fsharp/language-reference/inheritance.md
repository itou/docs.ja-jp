---
title: 継承
description: "' Inherit ' キーワードを使用して F # の継承関係を指定する方法について説明します。"
ms.date: 05/16/2016
ms.openlocfilehash: 5ab891a93528427a66e4eb8f7bfeccbf6e4d2c7e
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223844"
---
# <a name="inheritance"></a>継承

継承は、オブジェクト指向プログラミングの "the a" リレーションシップ (サブタイプ) をモデル化するために使用されます。

## <a name="specifying-inheritance-relationships"></a>継承関係の指定

継承関係を指定するには、 `inherit` クラス宣言でキーワードを使用します。 基本的な構文形式を次の例に示します。

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

クラスは、最大で1つの直接基底クラスを持つことができます。 キーワードを使用して基底クラスを指定しない場合、 `inherit` クラスはから暗黙的に継承され `System.Object` ます。

## <a name="inherited-members"></a>継承メンバー

クラスが別のクラスから継承する場合、派生クラスのユーザーは、派生クラスの直接のメンバーであるかのように、基底クラスのメソッドとメンバーを使用できます。

すべての let バインドとコンストラクターパラメーターはクラスに対してプライベートであるため、派生クラスからアクセスすることはできません。

キーワードは、 `base` 派生クラスで使用でき、基底クラスのインスタンスを参照します。 これは、自己識別子のように使用されます。

## <a name="virtual-methods-and-overrides"></a>仮想メソッドとオーバーライド

仮想メソッド (およびプロパティ) は、他の .NET 言語と比較して F # で多少異なる動作をします。 新しい仮想メンバーを宣言するには、キーワードを使用し `abstract` ます。 この操作は、そのメソッドの既定の実装を提供するかどうかに関係なく行います。 したがって、基本クラスの仮想メソッドの完全な定義は、次のパターンに従います。

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

派生クラスでは、この仮想メソッドのオーバーライドは次のパターンに従います。

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

基本クラスで既定の実装を省略した場合、基本クラスは抽象クラスになります。

基底クラスでの新しい仮想メソッドの宣言 `function1` と、派生クラスでオーバーライドする方法を次のコード例に示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]

## <a name="constructors-and-inheritance"></a>コンストラクターと継承

基底クラスのコンストラクターは、派生クラスで呼び出す必要があります。 基底クラスのコンストラクターの引数は、句の引数リストに表示され `inherit` ます。 使用される値は、派生クラスのコンストラクターに渡される引数から決定される必要があります。

次のコードは、基底クラスと派生クラスを示しています。派生クラスは、継承句で基底クラスのコンストラクターを呼び出します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

複数のコンストラクターの場合は、次のコードを使用できます。 派生クラスのコンストラクターの最初の行は `inherit` 句で、フィールドはキーワードで宣言された明示的なフィールドとして表示され `val` ます。 詳細については、「 [明示的なフィールド: `val` キーワード](./members/explicit-fields-the-val-keyword.md)」を参照してください。

```fsharp
type BaseClass =
    val string1 : string
    new (str) = { string1 = str }
    new () = { string1 = "" }

type DerivedClass =
    inherit BaseClass

    val string2 : string
    new (str1, str2) = { inherit BaseClass(str1); string2 = str2 }
    new (str2) = { inherit BaseClass(); string2 = str2 }

let obj1 = DerivedClass("A", "B")
let obj2 = DerivedClass("A")
```

## <a name="alternatives-to-inheritance"></a>継承の代替手段

型の軽微な変更が必要な場合は、継承の代わりにオブジェクト式を使用することを検討してください。 次の例は、新しい派生型を作成する代わりに、オブジェクト式を使用する方法を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

オブジェクト式の詳細については、「 [オブジェクト式](object-expressions.md)」を参照してください。

オブジェクト階層を作成する場合は、継承の代わりに判別共用体を使用することを検討してください。 判別共用体は、一般的な全体の種類を共有するさまざまなオブジェクトのさまざまな動作をモデル化することもできます。 単一の判別共用体を使用すると、多くの場合、相互に軽微なバリエーションを持つ多数の派生クラスが不要になります。 判別共用体の詳細については、「 [判別共用体](discriminated-unions.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [オブジェクト式](object-expressions.md)
- [F# 言語リファレンス](index.md)
