---
description: '詳細について: ICorProfilerCallback:: ExceptionUnwindFunctionLeave メソッド'
title: ICorProfilerCallback::ExceptionUnwindFunctionLeave メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave method [.NET Framework profiling]
- ExceptionUnwindFunctionLeave method [.NET Framework profiling]
ms.assetid: ebaad1d5-ee0a-4cb0-96bc-8ba5d371b747
topic_type:
- apiref
ms.openlocfilehash: f428230b017841e931463057144ef72cc1ead45f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705965"
---
# <a name="icorprofilercallbackexceptionunwindfunctionleave-method"></a>ICorProfilerCallback::ExceptionUnwindFunctionLeave メソッド

例外処理のアンワインドフェーズが関数のアンワインドを完了したことをプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ExceptionUnwindFunctionLeave();  
```  
  
## <a name="remarks"></a>解説  

 `ExceptionUnwindFunctionLeave`メソッドが呼び出されると、関数インスタンスとそのスタックデータがスタックから削除されます。  
  
 スタックがガベージコレクションを許可する状態ではなく、したがって、プリエンプティブガベージコレクションを有効にできないため、この呼び出し中にプロファイラーはブロックしないでください。 プロファイラーがここでブロックし、ガベージコレクションを実行しようとすると、このコールバックが戻るまでランタイムはブロックします。  
  
 また、この呼び出しでは、プロファイラーはマネージコードを呼び出さないようにするか、マネージメモリ割り当てを発生させることはできません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerCallback インターフェイス](icorprofilercallback-interface.md)
- [ExceptionUnwindFunctionEnter メソッド](icorprofilercallback-exceptionunwindfunctionenter-method.md)
