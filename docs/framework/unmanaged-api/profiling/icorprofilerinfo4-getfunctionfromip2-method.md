---
title: ICorProfilerInfo4::GetFunctionFromIP2 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetFunctionFromIP2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2
helpviewer_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2 method [.NET Framework profiling]
- GetFunctionFromIP2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 46ff70f4-13e9-40a0-802a-0a40abcfc6a0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7281f1aa0da417eba618b748ac68ba1fefb4907d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780846"
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a>ICorProfilerInfo4::GetFunctionFromIP2 메서드
관리 코드 명령 포인터는 함수의 JIT 다시 컴파일된 버전에 매핑됩니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
## <a name="parameters"></a>매개 변수  
 `ip`  
 [in] 관리 코드에서 명령 포인터입니다.  
  
 `pFunctionId`  
 [out] 함수 id입니다.  
  
 `pReJitId`  
 [out] 함수의 JIT 다시 컴파일된 버전의 id입니다.  
  
## <a name="remarks"></a>설명  
 `GetFunctionFromIP2` 비슷합니다 `GetFunctionFromIP`한다는 점을 제외 하는 지정 된 IP 주소를 포함 하는 함수의 함수 ID가 아닌 JIT 다시 컴파일된 ID를 가져옵니다.  
  
> [!NOTE]
>  `GetFunctionFromIP2` 반면 가비지 수집을 트리거할 수 `GetFunctionFromIP` 것입니다.  자세한 내용은 [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md)합니다.  
  
## <a name="requirements"></a>요구 사항  
 **플랫폼:** [시스템 요구 사항](../../../../docs/framework/get-started/system-requirements.md)을 참조하십시오.  
  
 **헤더:** CorProf.idl, CorProf.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>참고자료

- [ICorProfilerInfo 인터페이스](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
