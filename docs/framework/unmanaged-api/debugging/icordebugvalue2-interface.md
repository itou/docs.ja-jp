---
description: 詳細については、「ICorDebugValue2 インターフェイス」を参照してください。
title: ICorDebugValue2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugValue2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue2
helpviewer_keywords:
- ICorDebugValue2 interface [.NET Framework debugging]
ms.assetid: 3ff2ad2a-da5a-461b-8627-1a8eba49df9c
topic_type:
- apiref
ms.openlocfilehash: b408bb5d1732a60fc9aa8ffb93321d3542f2cab7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690263"
---
# <a name="icordebugvalue2-interface"></a>ICorDebugValue2 インターフェイス

"ICorDebugValue" インターフェイスを拡張して "テキスト" オブジェクトのサポートを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetExactType メソッド](icordebugvalue2-getexacttype-method.md)|この値のを表すオブジェクトへのインターフェイスポインターを取得し `ICorDebugType` <xref:System.Type> ます。|  
  
## <a name="remarks"></a>解説  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)

- [ICorDebugValue3 インターフェイス](icordebugvalue3-interface.md)
