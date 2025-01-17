---
title: ICLRRuntimeHost::ExecuteApplication 메서드
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteApplication
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteApplication
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteApplication method [.NET Framework hosting]
- ExecuteApplication method [.NET Framework hosting]
ms.assetid: 5f28cc4e-7176-4e00-aa1f-58ae6ee52fe4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca8db6fd1296420011dcbfbbb0e5682f8a484dc9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768819"
---
# <a name="iclrruntimehostexecuteapplication-method"></a>ICLRRuntimeHost::ExecuteApplication 메서드
ClickOnce 배포 매니페스트 기반 시나리오에서 새 도메인에서 활성화 될 응용 프로그램을 지정 하는 데 사용 합니다. 이러한 시나리오에 대 한 자세한 내용은 참조 하세요. [ClickOnce 보안 및 배포](/visualstudio/deployment/clickonce-security-and-deployment)합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT ExecuteApplication(  
    [in] LPCWSTR   pwzAppFullName,  
    [in] DWORD     dwManifestPaths,  
    [in] LPCWSTR   *ppwzManifestPaths,  
    [in] DWORD     dwActivationData,  
    [in] LPCWSTR   *ppwzActivationData,  
    [out] int      *pReturnValue  
);  
```  
  
## <a name="parameters"></a>매개 변수  
 `pwzAppFullName`  
 [in] 에 대해 정의 된 응용 프로그램의 전체 이름을 <xref:System.ApplicationIdentity>입니다.  
  
 `dwManifestPaths`  
 [in] 에 포함 된 문자열의 수는 `ppwzManifestPaths` 배열입니다.  
  
 `ppwzManifestPaths`  
 [in] 선택적 항목으로, 응용 프로그램에 대 한 매니페스트 경로 포함 하는 문자열 배열입니다.  
  
 `dwActivationData`  
 [in] 에 포함 된 문자열의 수는 `ppwzActivationData` 배열입니다.  
  
 `ppwzActivationData`  
 [in] 선택적 항목으로, 웹을 통해 배포 된 응용 프로그램에 대 한 URL의 쿼리 문자열 부분 등의 응용 프로그램의 정품 인증 데이터를 포함 하는 문자열 배열입니다.  
  
 `pReturnValue`  
 [out] 응용 프로그램의 진입점에서 반환 된 값입니다.  
  
## <a name="return-value"></a>반환 값  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`ExecuteApplication` 성공적으로 반환 합니다.|  
|HOST_E_CLRNOTAVAILABLE|프로세스에는 CLR (공용 언어 런타임)에 로드 되지 또는 CLR 상태인는 관리 코드를 실행 하거나 호출을 처리할 수 없습니다.|  
|HOST_E_TIMEOUT|호출 시간이 초과 되었습니다.|  
|HOST_E_NOT_OWNER|호출자가 잠금을 소유 하지 않습니다.|  
|HOST_E_ABANDONED|이벤트가 차단 된 스레드가 취소 된 또는 파이버를 대기 하 고 있습니다.|  
|E_FAIL|알 수 없는 치명적인 오류가 발생 했습니다. 메서드가 E_FAIL을 반환 하는 경우 CLR은 프로세스 내에서 사용할 수 없습니다. 메서드를 호스트 하는 데 대 한 후속 호출 HOST_E_CLRNOTAVAILABLE를 반환 합니다.|  
  
## <a name="remarks"></a>설명  
 `ExecuteApplication` 새로 만든된 응용 프로그램 도메인에서 ClickOnce 응용 프로그램을 활성화 하는 데 사용 됩니다.  
  
 `pReturnValue` 응용 프로그램에 의해 반환 된 값 출력 매개 변수는 설정입니다. Null 값을 제공 하는 경우 `pReturnValue`, `ExecuteApplication` 실패 하지 않습니다 하지만 값을 반환 하지 않습니다.  
  
> [!IMPORTANT]
>  호출 하지 마십시오는 [메서드 시작](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) 메서드를 호출 하기 전에 `ExecuteApplication` 매니페스트 기반 응용 프로그램을 활성화 하는 방법입니다. 경우는 `Start` 메서드를 먼저 호출 된 `ExecuteApplication` 메서드 호출이 실패 합니다.  
  
## <a name="requirements"></a>요구 사항  
 **플랫폼:** [시스템 요구 사항](../../../../docs/framework/get-started/system-requirements.md)을 참조하십시오.  
  
 **헤더:** MSCorEE.h  
  
 **라이브러리:** MSCorEE.dll에 리소스로 포함  
  
 **.NET Framework 버전:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>참고자료

- <xref:System.ActivationContext>
- <xref:System.AppDomainManager>
- <xref:System.ApplicationIdentity>
- [ICLRRuntimeHost 인터페이스](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [SetAppDomainManager 메서드](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)
- [연습: 디자이너를 사용하여 ClickOnce 배포 API에서 요청 시 어셈블리 다운로드](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer)
