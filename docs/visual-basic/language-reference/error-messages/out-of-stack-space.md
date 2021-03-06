---
description: '詳細情報: スタック領域が不足しています。(Visual Basic)'
title: スタック領域が不足しています。
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: a32ca0d2becade33177596501b7eabde4251e0a9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795489"
---
# <a name="out-of-stack-space-visual-basic"></a>スタック領域が不足しています。(Visual Basic)

スタックは、実行中のプログラムの要求に応じて、動的に拡張および縮小されるメモリの作業領域です。 その制限を超えました。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. プロシージャの入れ子が深すぎないことをチェックします。  
  
2. 再帰プロシージャが正常に終了することを確認します。  
  
3. ローカル変数で、使用可能な量よりも多くのローカル変数領域が必要な場合は、一部の変数をモジュール レベルで宣言してみてください。 また、`Static` を `Property`、`Sub`、または `Function` キーワードの前に付けて、プロシージャ内のすべての変数を静的に宣言することもできます。 または、`Static` ステートメントを使用して、プロシージャ内で個々の静的変数を宣言することもできます。  
  
4. 固定長文字列は可変長文字列よりも多くのスタック領域を使用するため、一部の固定長文字列を可変長文字列として再定義します。 スタック領域を必要としない、モジュール レベルで文字列を定義することもできます。  
  
5. `Calls` ダイアログ ボックスを使用して、スタック上でアクティブになっているプロシージャを表示して、入れ子になった `DoEvents` 関数呼び出しの数をチェックします。  
  
6. 既にスタックにあるイベント プロシージャを呼び出すイベントをトリガーすることによって、"イベントのカスケード" が発生していないことを確認します。 イベントのカスケードは、未終了の再帰プロシージャ呼び出しに似ていますが、コード内の明示的な呼び出しではなく Visual Basic によって呼び出しが行われるため、目立ちません。 `Calls` ダイアログ ボックスを使用すると、スタック上でアクティブになっているプロシージャが表示されます。  
  
## <a name="see-also"></a>関連項目

- [[メモリ] ウィンドウ](/visualstudio/debugger/memory-windows)
