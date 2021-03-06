---
description: '詳細情報: Instance Encoding オプション'
title: インスタンス エンコーディング オプション
ms.date: 03/30/2017
ms.assetid: 89e4b029-4f68-438c-8117-9b21fe094ef4
ms.openlocfilehash: 8cca7fd536673ca99b1014173e172508e3d97b7c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631165"
---
# <a name="instance-encoding-option"></a>インスタンス エンコーディング オプション

SQL ワークフローインスタンスストアの **インスタンスエンコードオプション** プロパティを使用すると、永続性データベースに情報を保存する前に、sql 永続化プロバイダーで、GZip アルゴリズムを使用してワークフローインスタンスの状態情報を圧縮するかどうかを指定できます。 このプロパティに使用できる値は GZip と None です。 既定値は None です。 これらのオプションを次の一覧で説明します。  
  
1. **GZip**。 永続化プロバイダーは、永続性データベースに状態情報を永続化する前に、GZip アルゴリズムを使用して状態情報をエンコードします。  
  
2. **なし**。 永続化プロバイダーは、永続性データベースに情報を保存する前は、状態情報をエンコードしません。  
  
 GZip を使用してワークフロー インスタンスの状態情報をエンコードすると、SQL データベースのメモリ消費量が減ります。また、ワークフロー サービス ホストが実行されているコンピューターとは異なるコンピューターがネットワーク上にあり、そこにデータベースが配置されている場合、ネットワークの消費量も減ります。 一般的なガイダンスとして、ワークフローインスタンスの状態が小さい場合は、 **インスタンスエンコーディングオプション** プロパティを **None** に設定します。
