---
description: '詳細情報: ICorProfilerThreadEnum:: Clone メソッド'
title: ICorProfilerThreadEnum::Clone メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Clone
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Clone method [.NET Framework profiling]
ms.assetid: 5a278bc9-88e2-4c69-b035-9d550dd77081
topic_type:
- apiref
ms.openlocfilehash: 00920484ed6f089f40281ea2590e6d9c27cd3268
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783795"
---
# <a name="icorprofilerthreadenumclone-method"></a>ICorProfilerThreadEnum::Clone メソッド

この [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) インターフェイスのコピーへのインターフェイスポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Clone (    [out] ICorProfilerThreadEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ppEnum`  
 入出力インターフェイスポインターへのポインター。これにより、この [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) インターフェイスのコピーが参照されます。 列挙子のコピーは、この列挙子とは別に独自の列挙状態を保持します。 ただし、コピーの最初のカーソル位置は、この列挙子の現在のカーソル位置と同じです。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md)
- [プロファイリングのインターフェイス](profiling-interfaces.md)
