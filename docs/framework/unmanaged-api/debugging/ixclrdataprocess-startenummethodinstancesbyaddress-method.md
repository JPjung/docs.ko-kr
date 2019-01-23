---
title: IXCLRDataProcess::StartEnumMethodInstancesByAddress 메서드
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 88ce9dd928871d71058fe28c243a9fb51b729778
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416688"
---
# <a name="ixclrdataprocessstartenummethodinstancesbyaddress-method"></a>IXCLRDataProcess::StartEnumMethodInstancesByAddress 메서드

메서드 인스턴스를 열거 핸들을 제공 `AppDomain` 지정된 된 주소에서 시작 합니다.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>구문

```
HRESULT StartEnumMethodInstancesByAddress(
    [in] CLRDATA_ADDRESS     address,
    [in] IXCLRDataAppDomain *appDomain,
    [out] CLRDATA_ENUM      *handle
);
```

### <a name="parameters"></a>매개 변수

`address` [in] 첫 번째 메서드 인스턴스의 주소입니다.

`appDomain` [in] 메서드 인스턴스의 AppDomain 합니다.

`handle` [out] 메서드 인스턴스를 열거 하는 것에 대 한 핸들입니다.

## <a name="remarks"></a>설명

제공 된 메서드는의 일부는 `IXCLRDataProcess` 인터페이스 및 가상 메서드 테이블의 27 슬롯에 해당 합니다.

## <a name="requirements"></a>요구 사항

**플랫폼:** [시스템 요구 사항](../../../../docs/framework/get-started/system-requirements.md)을 참조하십시오.  
**헤더:** 없음  
**라이브러리:** 없음  
**.NET Framework 버전:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>참고 항목

- [CLRDataSourceType 열거형](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [디버깅](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [IXCLRDataProcess 인터페이스](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)