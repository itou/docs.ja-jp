---
title: イベント ベースの非同期パターン (EAP)
description: .NET のイベント ベースの非同期パターン (EAP) に関する記事へのリンクを示します。これには、実装、ベスト プラクティス、EAP クライアントの実装などについての記事が含まれます。
ms.date: 07/23/2018
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
ms.openlocfilehash: c15bb6c9ec6ea737e6f240376e12bf8de3aa61bc
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830403"
---
# <a name="event-based-asynchronous-pattern-eap"></a>イベント ベースの非同期パターン (EAP)

非同期機能をクライアント コードに公開する方法は数多くあります。 イベント ベースの非同期パターンは、クラスが非同期動作を示す 1 つの方法を規定します。  
  
> [!NOTE]
> .NET Framework 4 以降では、非同期および並列プログラミング用の新しいモデルがタスク並列ライブラリに用意されています。 詳細については、「[タスク並列ライブラリ (TPL)](../parallel-programming/task-parallel-library-tpl.md)」および「[タスク ベースの非同期パターン (TAP)](task-based-asynchronous-pattern-tap.md)」を参照してください。
  
## <a name="in-this-section"></a>このセクションの内容

 [イベントベースの非同期パターンの概要](event-based-asynchronous-pattern-overview.md)  
 イベント ベースの非同期パターンによって、マルチスレッド デザイン固有の多くの複雑な問題を気にせずに、マルチスレッド アプリケーションの利点を活用できるしくみを説明します。  
  
 [イベントベースの非同期パターンの実装](implementing-the-event-based-asynchronous-pattern.md)  
 非同期機能を持つクラスをパッケージ化するための標準的な方法について説明します。  
  
 [イベントベースの非同期パターンを実装するための推奨される手順](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 イベント ベースの非同期パターンに従って非同期機能を公開するための要件について説明します。  
  
 [イベントベースの非同期パターンをいつ実装するかの決定](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 どのような場合に、[非同期プログラミング モデル (APM)](asynchronous-programming-model-apm.md) で表される <xref:System.IAsyncResult> パターンではなく、イベント ベースの非同期パターンの実装を選択するかを判断する方法について説明します。
  
 [方法: イベントベースの非同期パターンをサポートするコンポーネントを実装する](component-that-supports-the-event-based-asynchronous-pattern.md)  
 イベント ベースの非同期パターンを実装するコンポーネントの作成方法について説明します。 これは、<xref:System.ComponentModel?displayProperty=nameWithType> 名前空間のヘルパー クラスを使用して実装します。これにより、コンポーネントは任意のアプリケーション モデルで正常に動作します。  

 [方法: イベントベースの非同期パターンのクライアントを実装する](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)  
 イベント ベースの非同期パターンを実装するコンポーネントを使用するクライアントの作成方法について説明します。
  
 [方法: イベントベースの非同期パターンをサポートするコンポーネントを使用する](how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 イベント ベースの非同期パターンをサポートするコンポーネントの使用方法について説明します。  
  
## <a name="reference"></a>関連項目

 <xref:System.ComponentModel.AsyncOperation>  
 <xref:System.ComponentModel.AsyncOperation> クラスについて説明し、すべてのメンバーへのリンクの一覧を示します。  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <xref:System.ComponentModel.AsyncOperationManager> クラスについて説明し、すべてのメンバーへのリンクの一覧を示します。  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.BackgroundWorker> コンポーネントについて説明し、すべてのメンバーへのリンクの一覧を示します。  
  
## <a name="related-sections"></a>関連項目

 [タスク並列ライブラリ (TPL)](../parallel-programming/task-parallel-library-tpl.md)  
 非同期操作および並列操作のプログラミング モデルについて説明します。  
  
 [スレッド化](../threading/index.md)  
 .NET のマルチスレッド機能について説明します。  
  
## <a name="see-also"></a>関連項目

- [マネージド スレッド処理の実施](../threading/managed-threading-best-practices.md)
- [イベント](../events/index.md)
- [非同期プログラミングのデザイン パターン](index.md)
