---
title: PublicKeyBlob 구조체
ms.date: 03/30/2017
api_name:
- PublicKeyBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- PublicKeyBlob
helpviewer_keywords:
- PublicKeyBlob structure [.NET Framework strong naming]
ms.assetid: b9240712-829c-4c8d-9a09-a6e7aa63f63a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75ba3fd634b108c996e848f48000ffcd0600b00c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774591"
---
# <a name="publickeyblob-structure"></a>PublicKeyBlob 구조체
공개/개인 키 쌍의 공개 키를 이진 형식으로 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;   
```  
  
## <a name="members"></a>멤버  
  
|멤버|Description|  
|------------|-----------------|  
|`SigAlgId`|서명 알고리즘에 대 한 식별자 (형식 `ALG_ID`WinCrypt.h에 정의 된 대로) 공개 키입니다.|  
|`HashAlgId`|해시 알고리즘에 대 한 식별자 (형식의 `ALG_ID`WinCrypt.h에 정의 된 대로) 공개 키입니다.|  
|`cbPublicKey`|바이트의 키 길이입니다.|  
|`PublicKey`|CryptoAPI에 의해 반환 된 형식으로 키 값을 포함 하는 가변 길이 바이트 배열입니다.|  
  
## <a name="remarks"></a>설명  
 합니다 `PublicKeyBlob` 구조체를 사용 [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)를 [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md), 함수와 다른 강력한 이름 공개/개인 키 쌍의 공개 키를 나타냅니다.  
  
## <a name="requirements"></a>요구 사항  
 **플랫폼:** [시스템 요구 사항](../../../../docs/framework/get-started/system-requirements.md)을 참조하십시오.  
  
 **헤더:** StrongName.h  
  
 **라이브러리:** MsCorEE.dll에 리소스로 포함  
  
 **.NET Framework 버전:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>참고자료

- [StrongNameGetPublicKey 함수](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)
- [StrongNameSignatureGeneration 함수](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)
