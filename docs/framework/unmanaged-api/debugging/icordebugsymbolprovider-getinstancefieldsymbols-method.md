---
title: 'Icordebugsymbolprovider:: Getinstancefieldsymbols 메서드'
ms.date: 03/30/2017
ms.assetid: a29b9233-ee67-4b53-b8bc-c00b281e7edb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 02ffabfc43861d3d295a0bd2ea09213b06b6868a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771417"
---
# <a name="icordebugsymbolprovidergetinstancefieldsymbols-method"></a>Icordebugsymbolprovider:: Getinstancefieldsymbols 메서드
typespec 서명에 해당하는 인스턴스 필드 기호를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetInstanceFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugInstanceFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a>매개 변수  
 `cbSignature`  
 [in] `typeSig` 배열의 바이트 수입니다.  
  
 `typeSig`  
 [in] `typespec` 서명이 들어 있는 바이트 배열입니다.  
  
 `cRequestedSymbols`  
 [in] 요청된 기호 수입니다.  
  
 `pcFetchedSymbols`  
 [out] 메서드에 의해 검색되는 기호 수에 대한 포인터입니다.  
  
 `pSymbols`  
 [out] 에 대 한 포인터를 [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) 요청한 인스턴스 필드 기호를 포함 하는 배열입니다.  
  
## <a name="remarks"></a>설명  
  
> [!NOTE]
>  이 메서드는 .NET 네이티브에서만 사용할 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  
 **플랫폼:** [시스템 요구 사항](../../../../docs/framework/get-started/system-requirements.md)을 참조하십시오.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>참고자료

- [GetStaticFieldSymbols 메서드](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getstaticfieldsymbols-method.md)
- [ICorDebugSymbolProvider 인터페이스](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [디버깅 인터페이스](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
