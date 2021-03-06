---
description: '詳細情報: 方法:StreamWriter を使用してファイルにテキストを書き込む (Visual Basic)'
title: '方法: StreamWriter を使用してファイルにテキストを書き込む'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
ms.openlocfilehash: d5528d0b5e7de40062558d29c0d3bebc227583a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797355"
---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a>方法: StreamWriter を使用してファイルにテキストを書き込む (Visual Basic)

この例では、`My.Computer.FileSystem.OpenTextFileWriter` メソッドで <xref:System.IO.StreamWriter> オブジェクトを開き、そのオブジェクトを使用し、<xref:System.IO.StreamWriter> クラスの <xref:System.IO.TextWriter.WriteLine%2A> メソッドでテキスト ファイルに文字列を書き込みます。  
  
## <a name="example"></a>例  

 [!code-vb[VbFileIOWrite#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#5)]  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  

 次の条件を満たす場合は、例外が発生する可能性があります。  
  
- ファイルが存在するものの、読み取り専用の場合 (<xref:System.IO.IOException>)  
  
- ディスクの空き領域がない場合 (<xref:System.IO.IOException>)  
  
- パス名が長すぎる場合 (<xref:System.IO.PathTooLongException>)。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  

 次のコード例では、ファイルが存在しない場合は新規にファイルを作成します。 アプリケーションでファイルを作成する必要がある場合、そのアプリケーションにはフォルダーに対する `Create` アクセスが必要です。 ファイルが既に存在する場合、アプリケーションに必要なのは、より低い権限である `Write` アクセスだけです。 フォルダーに対して `Read` アクセスを許可するのではなく、可能な限りアプリケーションの配置時にファイルを作成しておき、1 つのファイルに対してのみ `Create` アクセスを許可する方が安全です。  
  
## <a name="see-also"></a>関連項目

- <xref:System.IO.StreamWriter>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- [方法: テキスト ファイルからデータを読み取る](how-to-read-from-text-files.md)
- [ファイルへの書き込み](writing-to-files.md)
