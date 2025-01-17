---
title: ICorProfilerInfo4::GetCodeInfo3 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetCodeInfo3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetCodeInfo3
helpviewer_keywords:
- GetCodeInfo3 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetCodeInfo3 method [.NET Framework profiling]
ms.assetid: bb8c105e-4d9a-4684-8c05-ed6909cc1b8c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0aefc9b21381f77fbe80db36da3e9932ad483750
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780834"
---
# <a name="icorprofilerinfo4getcodeinfo3-method"></a>ICorProfilerInfo4::GetCodeInfo3 메서드
지정된 함수의 JIT 다시 컴파일된 버전과 연결된 네이티브 코드의 범위를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetCodeInfo3(  
    [in]  FunctionID functionID,  
    [in]  ReJITID reJitId,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a>매개 변수  
 `functionID`  
 [in] 네이티브 코드가 연결된 함수의 ID입니다.  
  
 `reJitId`  
 [in] JIT 다시 컴파일된 함수의 ID입니다.  
  
 `cCodeInfos`  
 [in] `codeInfos` 배열의 크기입니다.  
  
 `pcCodeInfos`  
 [out] 총 수에 대 한 포인터 [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) 구조를 사용할 수 있습니다.  
  
 `codeInfos`  
 [out] 호출자가 제공한 버퍼입니다. 메서드가 반환된 후에는 각각 네이티브 코드 블록을 설명하는 `COR_PRF_CODE_INFO` 구조체의 배열을 포함합니다.  
  
## <a name="remarks"></a>설명  
 합니다 `GetCodeInfo3` 메서드는 비슷합니다 [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)한다는 점을 제외 하는 지정 된 IP 주소가 포함 된 함수의 JIT 다시 컴파일된 ID를 찾으면 됩니다.  
  
> [!NOTE]
>  `GetCodeInfo3` 반면 가비지 수집을 트리거할 수 있습니다 [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) 것입니다. 자세한 내용은 참조는 [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) HRESULT입니다.  
  
 범위는 CIL(Common Intermediate Language) 오프셋의 오름차순으로 정렬됩니다.  
  
 후 `GetCodeInfo3` 반환 되어 있는지 확인 해야 합니다는 `codeInfos` 버퍼가 모두 포함 하기에 충분 합니다 [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) 구조입니다. 이렇게 하려면 `cCodeInfos` 값을 `cchName` 매개 변수의 값과 비교합니다. 하는 경우 `cCodeInfos` 의 크기로 나눈를 [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) 구조 보다 작습니다 `pcCodeInfos`, 더 큰 할당 `codeInfos` 버퍼, 업데이트 `cCodeInfos` 호출이 고 큰 새 크기로 사용 하 여 `GetCodeInfo3` 다시 실행 합니다.  
  
 또는 길이가 0인 `codeInfos` 버퍼로 `GetCodeInfo3`를 먼저 호출하여 올바른 버퍼 크기를 구합니다. 설정할 수 있습니다 합니다 `codeInfos` 버퍼 크기에서 반환 된 값 `pcCodeInfos`의 크기를 곱한 값을 [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) 구조 및 호출 `GetCodeInfo3` 다시 합니다.  
  
## <a name="requirements"></a>요구 사항  
 **플랫폼:** [시스템 요구 사항](../../../../docs/framework/get-started/system-requirements.md)을 참조하십시오.  
  
 **헤더:** CorProf.idl, CorProf.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>참고자료

- [GetCodeInfo2 메서드](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)
- [ICorProfilerInfo4 인터페이스](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [프로파일링 인터페이스](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [프로파일링](../../../../docs/framework/unmanaged-api/profiling/index.md)
