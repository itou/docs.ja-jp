---
description: '詳細について: ICorDebugFunction2:: EnumerateNativeCode メソッド'
title: ICorDebugFunction2::EnumerateNativeCode メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.EnumerateNativeCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::EnumerateNativeCode
helpviewer_keywords:
- ICorDebugFunction2::EnumerateNativeCode method [.NET Framework debugging]
- EnumerateNativeCode method [.NET Framework debugging]
ms.assetid: d383f5cc-1144-4b6d-b57a-db34d9134ab2
topic_type:
- apiref
ms.openlocfilehash: 617d6dbfdb596df192e2722a47d81517ae57ac1f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692252"
---
# <a name="icordebugfunction2enumeratenativecode-method"></a>ICorDebugFunction2::EnumerateNativeCode メソッド

この ICorDebugFunction2 オブジェクトによって参照される関数内のネイティブコードステートメントを格納している、コードのオブジェクトへのインターフェイスポインターを取得します。  
  
> [!NOTE]
> `EnumerateNativeCode` は、.NET Framework の現在のバージョンでは実装されていません。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumerateNativeCode (  
    [out] ICorDebugCodeEnum   **ppCodeEnum  
);  
```  
  
## <a name="requirements"></a>必要条件  

 **ヘッダー:** CorDebug.idl、CorDebug.h
