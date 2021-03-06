---
title: ワークステーションとサーバーのガベージ コレクション (GC)
description: .NET でのワークステーションとサーバーのガベージ コレクションについて説明します。
ms.date: 04/21/2020
helpviewer_keywords:
- garbage collection, workstation
- garbage collection, server
- workstation garbage collection
- server garbage collection
ms.openlocfilehash: 640b5f42c1f841c2537284e4721e827248e3d300
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2020
ms.locfileid: "87917010"
---
# <a name="workstation-and-server-garbage-collection"></a>ワークステーションとサーバーのガベージ コレクション

ガベージ コレクターは、さまざまなシナリオに対応できるように自動的に調整されます。 ただし、作業負荷の特性に基づいて[ガベージ コレクションの種類を設定](../../core/run-time-config/garbage-collector.md#flavors-of-garbage-collection)できます。 CLR には、次の種類のガベージ コレクションが用意されています。

- ワークステーションのガベージ コレクション (GC)。これは、クライアント アプリ向けに設計されています。 これはスタンドアロン アプリの既定の GC フレーバーです。 ホストされているアプリ (ASP.NET によってホストされるアプリなど) の場合、ホストにより既定の GC フレーバーが決定されます。

  ワークステーションのガベージ コレクションは、同時実行または非同時実行のどちらかで実行できます。 同時実行 (または "*バックグラウンド*") ガベージ コレクションでは、ガベージ コレクションの実行中にマネージド スレッドの操作を続けることができます。 .NET Framework 4 以降では、[同時実行ガベージ コレクション](background-gc.md#concurrent-garbage-collection)は、[バックグラウンド ガベージ コレクション](background-gc.md)に置き換えられています。

- サーバーのガベージ コレクション。高いスループットとスケーラビリティが必要なサーバー アプリケーションを対象としたオプションです。

  - .NET Core では、サーバーのガベージ コレクションは、非同時実行ガベージ コレクションまたはバックグラウンド ガベージ コレクションである場合があります。

  - .NET Framework 4.5 以降のバージョンでは、サーバーのガベージ コレクションは、非同時実行またはバックグラウンドである場合があります。 .NET Framework 4 以前のバージョンでは、サーバー ガベージ コレクションは非同時実行になります。

次の図は、サーバー上でガベージ コレクションを実行する専用のスレッドを示しています。

![サーバー ガベージ コレクションのスレッド](media/gc-server.png)

## <a name="performance-considerations"></a>パフォーマンスに関する考慮事項

### <a name="workstation-gc"></a>ワークステーションの GC

ワークステーションのガベージ コレクションにおける、スレッド処理とパフォーマンスについての注意点を次に示します。

- コレクションは、ガベージ コレクションをトリガーしたユーザー スレッドで、それと同じ優先順位で実行されます。 ユーザー スレッドは一般に通常の優先順位で実行されるため、その場合 (通常の優先順位のスレッドで実行された場合)、ガベージ コレクターの CPU 時間が他のスレッドと競合します。 (ネイティブ コードを実行するスレッドは、サーバーまたはワークステーションのガベージ コレクションでは中断されません)

- プロセッサが 1 つしかないコンピューターでは、[構成設定](../../core/run-time-config/garbage-collector.md#workstation-vs-server)に関係なく、常にワークステーションのガベージ コレクションが使用されます。

### <a name="server-gc"></a>サーバーの GC

サーバーのガベージ コレクションにおける、スレッド処理とパフォーマンスについての注意点を次に示します。

- コレクションは、 `THREAD_PRIORITY_HIGHEST` の優先順位で実行される複数の専用スレッドで実行されます。

- ヒープおよびガベージ コレクションを実行するための専用スレッドは CPU ごとに 1 つずつ用意され、複数のヒープのコレクションが同時に行われます。 各ヒープには小さなオブジェクト ヒープと大きなオブジェクト ヒープがあり、どのヒープもユーザー コードからアクセスできます。 異なるヒープのオブジェクトを相互に参照できます。

- 複数のガベージ コレクション スレッドが連携して処理を行うため、同じサイズのヒープを処理した場合、サーバーのガベージ コレクションの方がワークステーションのガベージ コレクションよりも高速です。

- 一般に、サーバーのガベージ コレクションの方が、格納されるセグメントのサイズは大きくなります。 ただし、これは一般論に過ぎません。セグメントのサイズは実装に固有であり、変更されることがあります。 アプリをチューニングするときに、ガベージ コレクターによって割り当てられるセグメントのサイズに関して何らかの仮定をすることは避けてください。

- サーバーのガベージ コレクションでは、リソースが大量に消費されることがあります。 たとえば、プロセッサが 4 つのコンピューターで実行されているサーバー GC が 12 個のプロセスで使用されているとします。 すべてのプロセスで偶然、同時にガベージを回収すると、互いに干渉することになります。同じプロセッサで 12 のスレッドがスケジュールされるためです。 プロセスがアクティブの場合、すべてのプロセスでサーバー GC を使用することはお勧めしません。

実行するアプリケーションのインスタンスが数百に及ぶ場合は、同時実行ガベージ コレクションを無効にしてワークステーションのガベージ コレクションを使用することを検討してください。 これによって、コンテキストの切り替えが少なくなり、パフォーマンスが向上します。

## <a name="see-also"></a>関連項目

- [バックグラウンド ガベージ コレクション](background-gc.md)
- [ガベージ コレクションの実行時構成オプション](../../core/run-time-config/garbage-collector.md)
