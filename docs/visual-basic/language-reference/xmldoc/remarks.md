---
description: 詳細については、以下をご覧ください。 <remarks> (Visual Basic)
title: <remarks>
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: 4b0584abbe85a7ecc73e25dd1f6ec321962b88a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640408"
---
# <a name="remarks-visual-basic"></a>\<remarks> (Visual Basic)

メンバーの解説セクションを指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a>パラメーター  

 `description`  
 メンバーの説明。  
  
## <a name="remarks"></a>Remarks  

 `<remarks>` タグを使用して、型の情報を追加し、[\<summary>](summary.md) で指定された情報を補足します。  
  
 この情報はオブジェクト ブラウザーに表示されます。 オブジェクト ブラウザーについては、「[コードの構造の表示](/visualstudio/ide/viewing-the-structure-of-code)」を参照してください。  
  
 コンパイル時に [-doc](../../reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  

 この例では、`<remarks>` タグを使用して `UpdateRecord` メソッドの動作を説明します。  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>関連項目

- [XML のコメント用タグ](index.md)
