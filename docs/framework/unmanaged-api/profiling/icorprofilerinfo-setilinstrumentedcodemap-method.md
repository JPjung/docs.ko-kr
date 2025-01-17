---
title: ICorProfilerInfo::SetILInstrumentedCodeMap 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetILInstrumentedCodeMap method [.NET Framework profiling]
ms.assetid: bce1dcf8-b4ec-4e73-a917-f2df1ad49c8a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e41df91ceb9e4b776c2aa1ce864b7e09ec485fd5
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661950"
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a>ICorProfilerInfo::SetILInstrumentedCodeMap 메서드

지정한 Microsoft 중간 언어 (MSIL) 맵 항목을 사용 하 여 지정된 된 함수에 대 한 코드 맵을 설정 합니다.

> [!NOTE]
> 호출.NET framework 버전 2.0 `SetILInstrumentedCodeMap` 에 `FunctionID` 는 특정 응용 프로그램 도메인에서 제네릭 함수를 나타내는 모든 인스턴스에 적용 됩니다 응용 프로그램 도메인에서 해당 함수의 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetILInstrumentedCodeMap(
    [in]  FunctionID functionId,
    [in]  BOOL       fStartJit,
    [in]  ULONG      cILMapEntries,
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);
```

## <a name="parameters"></a>매개 변수

`functionId`\
[in] 코드 맵 설정 하려는 함수의 ID입니다.

`fStartJit`\
[in] 지정 하는 부울 값 여부를 호출 합니다 `SetILInstrumentedCodeMap` 메서드는 특정 작업에 대해 첫 번째 `FunctionID`. 설정 `fStartJit` 하 `true` 첫 번째 호출에서 `SetILInstrumentedCodeMap` 에 대 한을 지정 `FunctionID`, 및 `false` 이후입니다.

`cILMapEntries`\
[in] 요소 수를 `cILMapEntries` 배열입니다.

`rgILMapEntries`\
[in] MSIL 오프셋을 지정 하는 각 COR_IL_MAP 구조체의 배열입니다.

## <a name="remarks"></a>설명

프로파일러 (예: 지정 된 소스 줄에 도달 하면 알림) 계측을 위해 메서드의 소스 코드 내에서 문을 삽입 하는 경우가 있습니다. `SetILInstrumentedCodeMap` 프로파일러를 원래 MSIL 명령을 새 위치로 매핑할 수 있습니다. 프로파일러를 사용 하 여 수를 [icorprofilerinfo:: Getiltonativemapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) 메서드는 지정 된 네이티브 오프셋에 대 한 원래 MSIL 오프셋을 가져올 수 있습니다.

디버거에서 msil 오프셋 원래, 수정 되지 않은 MSIL 코드 내에서 각 이전 오프셋 나타내며 각 새 오프셋 새, 계측 된 코드 내에서 MSIL 오프셋 가리킵니다 가정 합니다. 지도 오름차순으로 정렬 되어야 합니다. 단계별 코드 실행이 제대로 작동 하려면, 다음이 지침을 따르세요.

- 계측 된 MSIL 코드 순서를 변경 하지 않습니다.

- 원래 MSIL 코드를 제거 하지 마십시오.

- 지도에 프로그램 데이터베이스 (PDB) 파일에서 모든 시퀀스 위치에 대 한 항목을 포함 합니다. 지도 누락 된 항목을 보간하지 않습니다. 따라서 다음과 같은 맵을 지정:

  (0, 이전 0 새)

  (5 오래 10 새)

  (9 이전, 20 새)

  - 이전 오프셋 0, 1, 2, 3 또는 4의 새 오프셋 0에 매핑됩니다.

  - 5, 6, 7 또는 8 이전 오프셋 새 오프셋 10으로 매핑됩니다.

  - 9 이상 이전 오프셋 20 새 오프셋에 매핑됩니다.

  - 새 오프셋 0, 1, 2, 3, 4, 5, 6, 7, 8 또는 9 이전 오프셋 0에 매핑됩니다.

  - 10, 11, 12, 13, 14, 15, 16, 17, 18 또는 19 새 오프셋 5 이전 오프셋에 매핑됩니다.

  - 20 이상의 새 오프셋을 9 이전 오프셋에 매핑됩니다.

## <a name="requirements"></a>요구 사항

**플랫폼:** [시스템 요구 사항](../../../../docs/framework/get-started/system-requirements.md)을 참조하십시오.

**헤더:** CorProf.idl, CorProf.h

**라이브러리:** CorGuids.lib

**.NET Framework 버전:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]

## <a name="see-also"></a>참고자료

- [ICorProfilerInfo 인터페이스](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
