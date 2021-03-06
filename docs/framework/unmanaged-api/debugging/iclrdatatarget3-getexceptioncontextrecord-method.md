---
title: ICLRDataTarget3::GetExceptionContextRecord メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetContextRecord
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 66076ed5-f05c-4114-9788-94cb143abb8a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 72c45e821a59c1e910b5c8422df02978046eb56b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/01/2018
ms.locfileid: "43425225"
---
# <a name="iclrdatatarget3getexceptioncontextrecord-method"></a>ICLRDataTarget3::GetExceptionContextRecord メソッド
ターゲット プロセスに関連付けられたコンテキスト レコードを取得するために、共通言語ランタイム (CLR: Common Language Runtime) データ アクセス サービスによって呼び出されます。 たとえば、ダンプ ターゲットについて、これと等価になります経由で渡されたコンテキスト レコード、`ExceptionParam`への引数、 [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) Windows デバッグ ヘルプ ライブラリ (DbgHelp) の関数。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetExceptionContextRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize)] BYTE* buffer  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `bufferSize`  
 [入力] 入力バッファー サイズ (バイト単位)。 これはコンテキスト レコードを格納するのに十分な大きさである必要があります。  
  
 `bufferUsed`  
 [出力] 実際にバッファーに書き込まれるバイト数を受け取る `ULONG32` 型へのポインター。  
  
 `buffer`  
 [出力] コンテキスト レコードのコピーを受け取るメモリ バッファーへのポインター。 例外レコードとして返されます、[コンテキスト](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context)型。  
  
## <a name="return-value"></a>戻り値  
 戻り値は、成功の場合は `S_OK` で、失敗の場合は `HRESULT` コードです。 次が `HRESULT` コードに含まれることはありますが、限定されているわけではありません。  
  
|リターン コード|説明|  
|-----------------|-----------------|  
|`S_OK`|メソッドが成功しました。 コンテキスト レコードは出力バッファーにコピーされました。|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|コンテキスト レコードはターゲットに関連付けられていません。|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|入力バッファーのサイズが足りないため、コンテキスト レコードを格納できません。|  
  
## <a name="remarks"></a>Remarks  
 [コンテキスト](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context)は Windows SDK によって提供されたヘッダーで定義されているプラットフォームに固有の構造体です。  
  
 このメソッドは、デバッグ アプリケーションの作成者によって実装されます。  
  
## <a name="requirements"></a>要件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** ClrData.idl、ClrData.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICLRDataTarget3 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 [GetExceptionRecord メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)  
 [GetExceptionThreadID メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
