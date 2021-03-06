---
description: '詳細については、次を参照してください: CorMethodSemanticsAttr 列挙型'
title: CorMethodSemanticsAttr 列挙型
ms.date: 03/30/2017
api_name:
- CorMethodSemanticsAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodSemanticsAttr
helpviewer_keywords:
- CorMethodSemanticsAttr enumeration [.NET Framework metadata]
ms.assetid: ca2af325-eb9d-4a91-90e4-267e45b98611
topic_type:
- apiref
ms.openlocfilehash: 4079e81ae2389ff0684fd11d0751b191a7289932
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784367"
---
# <a name="cormethodsemanticsattr-enumeration"></a>CorMethodSemanticsAttr 列挙型

メソッドとそれに関連付けられているプロパティまたはイベントとの関係を記述する値が格納されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum CorMethodSemanticsAttr {  
  
    msSetter    =   0x0001,  
    msGetter    =   0x0002,  
    msOther     =   0x0004,  
    msAddOn     =   0x0008,  
    msRemoveOn  =   0x0010,  
    msFire      =   0x0020,  
  
} CorMethodSemanticsAttr;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`msSetter`|メソッドがプロパティのアクセサーであることを指定し `set` ます。|  
|`msGetter`|メソッドがプロパティのアクセサーであることを指定し `get` ます。|  
|`msOther`|メソッドが、ここで定義されたプロパティ以外のプロパティまたはイベントへのリレーションシップを持つことを指定します。|  
|`msAddOn`|メソッドがイベントのハンドラーメソッドを追加することを指定します。|  
|`msRemoveOn`|メソッドがイベントのハンドラーメソッドを削除することを指定します。|  
|`msFire`|メソッドがイベントを発生させることを指定します。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorHdr. h  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙体](metadata-enumerations.md)
