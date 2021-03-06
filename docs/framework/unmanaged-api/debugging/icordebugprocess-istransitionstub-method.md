---
description: '詳細については、次を参照してください: IsTransitionStub Method:: メソッド'
title: ICorDebugProcess::IsTransitionStub メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsTransitionStub
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsTransitionStub
helpviewer_keywords:
- ICorDebugProcess::IsTransitionStub method [.NET Framework debugging]
- IsTransitionStub method [.NET Framework debugging]
ms.assetid: f7653317-7e48-4163-be03-f50f1a4b0f70
topic_type:
- apiref
ms.openlocfilehash: 0da8527538c2573b1ec0d26f8711644fe8fcca2a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782001"
---
# <a name="icordebugprocessistransitionstub-method"></a>ICorDebugProcess::IsTransitionStub メソッド

アドレスが、マネージコードへの遷移を発生させるスタブ内にあるかどうかを示す値を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
## <a name="parameters"></a>パラメーター  

 `address`  
 から `CORDB_ADDRESS` 対象のアドレスを示す値です。  
  
 `pbTransitionStub`  
 入出力`true`指定されたアドレスが、マネージコードへの遷移を発生させるスタブ内にある場合は、それ以外の場合 `pbTransitionStub` はとなるブール値へのポインター。 `false`  
  
## <a name="remarks"></a>解説  

 `IsTransitionStub`アンマネージステッピングコードでは、メソッドを使用して、管理対象のステッパにステップ実行コントロールをいつ返すかを決定できます。  
  
 ポータブル実行可能 (PE) ファイルの情報を参照して、遷移スタブを識別することもできます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
