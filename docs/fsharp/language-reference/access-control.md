---
title: アクセス制御
description: F#プログラミング言語で、型、メソッド、関数などのプログラミング要素へのアクセスを制御する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: fe204a883a440794fdd033c54d6d8d4fb68e0ce2
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425112"
---
# <a name="access-control"></a>アクセス制御

*アクセス制御*とは、型、メソッド、関数など、特定のプログラム要素を使用できるクライアントを宣言することを指します。

## <a name="basics-of-access-control"></a>Access Control の基礎

でF#は、アクセス制御指定子 `public`、`internal`、および `private` をモジュール、型、メソッド、値定義、関数、プロパティ、および明示的なフィールドに適用できます。

- `public` は、すべての呼び出し元がエンティティにアクセスできることを示します。

- `internal` は、同じアセンブリからエンティティにアクセスできることを示します。

- `private` は、外側の型またはモジュールからのみエンティティにアクセスできることを示します。

> [!NOTE]
> アクセス指定子 `protected` はでF#は使用されませんが、`protected` アクセスをサポートする言語で作成された型を使用している場合は許容されます。 したがって、保護されたメソッドをオーバーライドすると、メソッドはクラスとその子孫内でのみアクセス可能な状態になります。

一般に、指定子は、`mutable` または `inline` 指定子が使用されている場合を除き、エンティティの名前の前に配置されます。これは、アクセス制御指定子の後に表示されます。

アクセス指定子が使用されていない場合、既定値は `public`になります。ただし、型の `let` バインディングの場合は、常に型に `private` ます。

のシグネチャF#には、プログラム要素へのF#アクセスを制御するための別のメカニズムが用意されています。 アクセス制御に署名は必要ありません。 詳細については、「[シグネチャ](signature-files.md)」を参照してください。

## <a name="rules-for-access-control"></a>Access Control の規則

アクセス制御には、次の規則が適用されます。

- 継承宣言 (つまり、クラスの基底クラスを指定するために `inherit` を使用する)、インターフェイス宣言 (つまり、クラスがインターフェイスを実装することを指定する) と、抽象メンバーは、外側の型と同じアクセシビリティを常に持っています。 したがって、アクセス制御指定子は、これらのコンストラクトでは使用できません。

- 判別共用体の個々のケースのアクセシビリティは、判別共用体自体のアクセシビリティによって決まります。 つまり、特定の共用体ケースは、共用体自体よりもアクセシビリティが低くなります。

- レコード型の個々のフィールドのアクセシビリティは、レコード自体のアクセシビリティによって決まります。 つまり、特定のレコードラベルは、レコード自体よりもアクセスできなくなります。

## <a name="example"></a>例

次のコードは、アクセス制御指定子の使用方法を示しています。 プロジェクトには、`Module1.fs` と `Module2.fs`の2つのファイルがあります。 各ファイルは暗黙的にモジュールです。 したがって、`Module1` と `Module2`の2つのモジュールがあります。 プライベート型と内部型は `Module1`で定義されます。 プライベート型に `Module2`からアクセスすることはできませんが、内部型ではアクセスできます。

[!code-fsharp[Main](~/samples/snippets/fsharp/access-control/snippet1.fs)]

次のコードは、`Module1.fs`で作成された型のアクセシビリティをテストします。

[!code-fsharp[Main](~/samples/snippets/fsharp/access-control/snippet2.fs)]

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [シグネチャ](signature-files.md)
