---
title: ICLRRuntimeHost 인터페이스
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost
helpviewer_keywords:
- ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: cb0c5f65-3791-47bc-b833-2f84f4101ba5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ba02373aae33baf77b72323fabf1f6ca1fe4eecf
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490237"
---
# <a name="iclrruntimehost-interface"></a>ICLRRuntimeHost 인터페이스
유사한 기능을 제공 합니다 [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) 버전 1에서는 다음과 같이 변경을 사용 하 여.NET Framework에서 제공 하는 인터페이스:  
  
- 추가 된 [SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) 호스트 컨트롤 인터페이스를 설정 하는 방법입니다.  
  
- 제공 하는 몇 가지 방법 중 생략 `ICorRuntimeHost`합니다.  
  
## <a name="methods"></a>메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[ExecuteApplication 메서드](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)|ClickOnce 배포 매니페스트 기반 시나리오에서 새 도메인에서 활성화 될 응용 프로그램을 지정 하는 데 사용 합니다.|  
|[ExecuteInAppDomain 메서드](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeinappdomain-method.md)|지정 된 <xref:System.AppDomain> 지정 된 관리 되는 코드를 실행 하는 합니다.|  
|[ExecuteInDefaultAppDomain 메서드](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeindefaultappdomain-method.md)|지정된 된 어셈블리에 지정 된 형식의 지정된 된 메서드를 호출합니다.|  
|[GetCLRControl 메서드](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|형식의 인터페이스 포인터를 가져옵니다 [ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) 호스트의 CLR (공용 언어 런타임)의 측면을 사용자 지정 하는 데 사용할 수 있는 합니다.|  
|[GetCurrentAppDomainId 메서드](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)|숫자 식별자를 가져옵니다는 <xref:System.AppDomain> 현재 실행 되는 합니다.|  
|[SetHostControl 메서드](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)|호스트 컨트롤 인터페이스를 설정합니다. 호출 해야 합니다 `SetHostControl` 호출 하기 전에 `Start`입니다.|  
|[Start 메서드](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)|프로세스에 CLR을 초기화합니다.|  
|[Stop 메서드](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-stop-method.md)|런타임에서 코드의 실행을 중지합니다.|  
|[UnloadAppDomain 메서드](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-unloadappdomain-method.md)|언로드를 <xref:System.AppDomain> 지정된 된 숫자 식별자에 해당 하는 합니다.|  
  
## <a name="remarks"></a>설명  
 .NET Framework 4부터 사용 합니다 [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) 인터페이스에 대 한 포인터를 가져오려면를 [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) 인터페이스를 고를 호출 하는 [iclrruntimeinfo:: Getinterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)에 대 한 포인터를 가져올 메서드를 `ICLRRuntimeHost`입니다. .NET Framework의 이전 버전에서는 호스트에 대 한 포인터를 가져옵니다는 `ICLRRuntimeHost` 를 호출 하 여 인스턴스 [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) 하거나 [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)합니다. .NET Framework 버전 2.0에서에서 제공 하는 기술을의 구현에 제공 하려면 사용 해야 `ICLRRuntimeHost` 대신 `ICorRuntimeHost`합니다.  
  
> [!IMPORTANT]
>  호출 하지 마십시오 합니다 [시작](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) 메서드를 호출 하기 전에 [ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) 매니페스트 기반 응용 프로그램을 활성화 하는 방법입니다. 경우는 `Start` 메서드를 먼저 호출 된 `ExecuteApplication` 메서드 호출이 실패 합니다.  
  
## <a name="requirements"></a>요구 사항  
 **플랫폼:** [시스템 요구 사항](../../../../docs/framework/get-started/system-requirements.md)을 참조하십시오.  
  
 **헤더:** MSCorEE.h  
  
 **라이브러리:** MSCorEE.dll에 리소스로 포함  
  
 **.NET Framework 버전:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>참고자료

- [CorBindToCurrentRuntime 함수](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntimeEx 함수](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [ICLRControl 인터페이스](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICorRuntimeHost 인터페이스](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [호스팅 인터페이스](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [CLRRuntimeHost Coclass](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
