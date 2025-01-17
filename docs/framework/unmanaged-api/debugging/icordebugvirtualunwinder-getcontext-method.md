---
title: ICorDebugVirtualUnwinder::GetContext 메서드
ms.date: 03/30/2017
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8377c374ae71c45cf198446d66a5f9a235a2142f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775368"
---
# <a name="icordebugvirtualunwindergetcontext-method"></a>ICorDebugVirtualUnwinder::GetContext 메서드
이 해제기의 현재 컨텍스트를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
## <a name="parameters"></a>매개 변수  
 `contextFlags`  
 [in] WinNT.h에 정의된 반환할 컨텍스트 부분을 지정하는 플래그입니다.  
  
 `cbContextBuf`  
 [in] `contextBuf`의 바이트 수입니다.  
  
 `contextSize`  
 [out] 실제로 `contextBuf`에 기록되는 바이트 수에 대한 포인터입니다.  
  
 `contextBuf`  
 [out] 이 해제기의 현재 컨텍스트를 포함하는 바이트 배열입니다.  
  
## <a name="return-value"></a>반환 값  
 mscordbi에 수신되는 모든 오류 HRESULT는 심각한 오류로 간주하여 ICorDebug API에서 `CORDBG_E_DATA_TARGET_ERROR`가 반환됩니다.  
  
## <a name="remarks"></a>설명  
 초기 값을 설정 합니다 `contextBuf` 인수를 호출 하 여 반환 되는 상황에 맞는 버퍼를 [icordebugstackwalk:: Getcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) 메서드.  
  
> [!NOTE]
>  이 메서드는 .NET 네이티브에서만 사용할 수 있습니다.  
  
 해제하면 레지스터 하위 집합만(예: 비휘발성 레지스터만) 복원될 수 있으므로 컨텍스트가 실제 메서드 호출 시 레지스터 상태와 정확히 일치하지 않을 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  
 **플랫폼:** [시스템 요구 사항](../../../../docs/framework/get-started/system-requirements.md)을 참조하십시오.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>참고자료

- [ICorDebugMemoryBuffer 인터페이스](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [디버깅 인터페이스](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
