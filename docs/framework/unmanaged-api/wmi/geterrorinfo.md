---
title: GetErrorInfo 함수 (관리 되지 않는 API 참조)
description: GetErrorInfo 함수는 이전 함수 호출에서 오류 정보를 검색합니다.
ms.date: 11/06/2017
api_name:
- GetErrorInfo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetErrorInfo
helpviewer_keywords:
- GetErrorInfo function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e33a18487da420eb3b317bb70e0ac9e68b4b8ad6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746546"
---
# <a name="geterrorinfo-function"></a>GetErrorInfo 함수
이전 함수 호출에서 오류 정보를 검색합니다.  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>구문  
  
```cpp  
IErrorInfo* GetErrorInfo(); 
```  

## <a name="return-value"></a>반환 값

에 대 한 포인터를 [IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) 함수 호출에 성공 하면 개체 또는 `null` 실패 한 경우.
  
## <a name="remarks"></a>설명

이 함수에 대 한 호출을 래핑하는 [IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) 메서드.

## <a name="requirements"></a>요구 사항  
 **플랫폼:** [시스템 요구 사항](../../../../docs/framework/get-started/system-requirements.md)을 참조하십시오.  
  
 **헤더:** WMINet_Utils.def  
  
 **.NET Framework 버전:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>참고자료

- [WMI 및 성능 카운터 (관리 되지 않는 API 참조)](index.md)
