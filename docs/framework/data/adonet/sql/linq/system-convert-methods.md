---
description: '詳細情報: System.Convert メソッド'
title: System.Convert メソッド
ms.date: 03/30/2017
ms.assetid: 3ca6c5b6-ea5d-4ab0-b675-f082135b342c
ms.openlocfilehash: a323f8d0c3c4a8d1248409d2ec27565acdc58222
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681410"
---
# <a name="systemconvert-methods"></a>System.Convert メソッド

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、次の <xref:System.Convert> メソッドをサポートしていません。

- <xref:System.IFormatProvider> パラメーターを持つ形式。

- 文字配列またはバイト配列を扱うメソッド。

  - <xref:System.Convert.FromBase64CharArray%2A>

  - <xref:System.Convert.ToBase64CharArray%2A>

  - <xref:System.Convert.FromBase64String%2A>

  - <xref:System.Convert.ToBase64String%2A>

- 次のメソッド。

  - `public static <Type2> To<Type2>(<Type1> value);` (

    `Type1` および `Type2` は `sbyte`、`uint`、`ulong`、`ushort` のいずれか)

  - C#:

    `int To<int type>(string value, int fromBase),`

    `ToString(... value, int toBase)`

  - Visual Basic:

    `Function To(Of [Numeric])(value as String, fromBase As Integer)`

    `As [Numeric], ToString( value As …, toBase As Integer)`

  - <xref:System.Convert.IsDBNull%2A>

  - <xref:System.Convert.GetTypeCode%2A>

  - <xref:System.Convert.ChangeType%2A>

## <a name="see-also"></a>関連項目

- [データ型と関数](data-types-and-functions.md)
