---
title: ICorDebugAssembly3::EnumerateContainedAssemblies 메서드
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05c4e2a5c16f11f80cc8356a65b746eab81a3899
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744402"
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a>ICorDebugAssembly3::EnumerateContainedAssemblies 메서드
이 어셈블리에 포함된 어셈블리에 대한 열거자를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
## <a name="parameters"></a>매개 변수  
 `ppAssemblies`  
 [out] 열거자는 ICorDebugAssemblyEnum 인터페이스 개체의 주소에 대 한 포인터입니다.  
  
## <a name="return-value"></a>반환 값  
 이 `S_OK` 개체가 컨테이너이면 `ICorDebugAssembly3`이고, 그러지 않으면 `S_FALSE`이며 열거형은 비어 있습니다.  
  
## <a name="remarks"></a>설명  
 포함된 어셈블리를 열거하려면 기호가 필요합니다. 기호가 없으면 메서드는 `S_FALSE`를 반환하며 올바른 열거자가 제공되지 않습니다.  
  
> [!NOTE]
>  이 메서드는 .NET 네이티브에서만 사용할 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  
 **플랫폼:** [시스템 요구 사항](../../../../docs/framework/get-started/system-requirements.md)을 참조하십시오.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>참고자료

- [ICorDebugAssembly3 인터페이스](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [디버깅 인터페이스](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
