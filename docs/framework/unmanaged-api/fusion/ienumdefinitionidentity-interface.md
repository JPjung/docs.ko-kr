---
title: IEnumDefinitionIdentity 인터페이스
ms.date: 03/30/2017
api_name:
- IEnumDefinitionIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumDefinitionIdentity
helpviewer_keywords:
- IEnumDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: 8263e75d-251b-4abc-8a1a-c62884142232
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4bbd8476b7778de6d0023f3a8522a44be6626884
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751519"
---
# <a name="ienumdefinitionidentity-interface"></a>IEnumDefinitionIdentity 인터페이스
컬렉션의 열거자 역할을 `IDefinitionIdentity` 개체입니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
IEnumDefinitionIdentity : IUnknown {  
  
    HRESULT Clone (  
        [out] IEnumDefinitionIdentity **ppIEnumDefinitionIdentity  
    );  
  
    HRESULT Next (  
        [in]  ULONG               celt,  
        [out, length_is(celt), size_is(*pceltWritten)]  
              IDefinitionIdentity *rgpIDefinitionIdentity[],  
        [out] ULONG               *pceltWritten  
    );  
  
    HRESULT Reset ();  
  
    HRESULT Skip (  
        [in] ULONG celt  
    );  
  
};  
```  
  
## <a name="methods"></a>메서드  
  
|메서드|Description|  
|------------|-----------------|  
|`IEnumDefinitionIdentity::Clone`|새 인터페이스 포인터를 가져옵니다 `IEnumDefinitionIdentity` 이 동일한 멤버를 포함 하는 개체 `IEnumDefinitionIdentity`합니다.|  
|`IEnumDefinitionIdentity::Next`|지정 된 수를 가져옵니다 `IDefinitionIdentity` 개체를 현재 위치에서 시작 합니다.|  
|`IEnumDefinitionIdentity::Reset`|이 부분에 명령 포인터를 이동 `IEnumDefinitionIdentity`합니다.|  
|`IEnumDefinitionIdentity::Skip`|요소를 현재 위치부터 지정한 수 만큼 앞으로 명령 포인터를 이동 합니다.|  
  
## <a name="requirements"></a>요구 사항  
 **플랫폼:** [시스템 요구 사항](../../../../docs/framework/get-started/system-requirements.md)을 참조하십시오.  
  
 **헤더:** Isolation.h  
  
 **.NET Framework 버전:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>참고자료

- [Fusion 인터페이스](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [IDefinitionIdentity 인터페이스](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)
