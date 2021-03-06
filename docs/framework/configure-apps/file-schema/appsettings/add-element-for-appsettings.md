---
description: '詳細情報: <add> の要素 <appSettings>'
title: <appSettings> の <add> 要素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
ms.openlocfilehash: f10ffe517b3b25543bc7baed0c7d2af13f48ab02
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652888"
---
# <a name="add-element-for-appsettings"></a>\<appSettings> の \<add> 要素

カスタムアプリケーション設定を追加します。

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a>構文

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a>属性

|           | 説明 |
| --------- | ----------- |
| **key**   | 必須の属性です。<br><br>追加するキーの名前を指定します。 |
| **value** | 必須の属性です。<br><br>追加するキーの値を指定します。 |

## <a name="parent-element"></a>親要素

|     | 説明 |
| --- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | ファイル パス、XML Web サービス URL、またはアプリケーションのその他のカスタム構成情報など、カスタム アプリケーションの設定が含まれています。 |

## <a name="child-elements"></a>子要素

なし

## <a name="example"></a>例

次の例は、アプリケーション名のカスタム構成設定を追加する方法を示しています。

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

次の例では、要素を使用して、 `<add>` ASP.NET アプリケーションで2つの互換性設定を定義します。

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="see-also"></a>関連項目

- [.NET Framework の構成ファイルスキーマ](../index.md)
