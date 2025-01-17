---
title: 라우팅 시나리오
ms.date: 03/30/2017
helpviewer_keywords:
- routing [WCF], scenarios
ms.assetid: ec22f308-665a-413e-9f94-7267cb665dab
ms.openlocfilehash: 0ab071bf7996a296563fbda68dfdc731e95ed897
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425354"
---
# <a name="routing-scenarios"></a>라우팅 시나리오
라우팅 서비스는 폭넓은 사용자 지정이 가능하지만 새 구성을 처음부터 만드는 경우 효율적인 라우팅 논리를 디자인하기란 어려운 일입니다.  다만 대부분의 라우팅 서비스 구성에 해당되는 몇 가지 일반적인 시나리오는 있습니다. 이러한 시나리오가 사용자의 특정 구성에 바로 적용되지는 않겠지만 이러한 시나리오를 처리하도록 라우팅 서비스를 구성하는 방법을 이해하면 라우팅 서비스를 더 잘 이해할 수 있습니다.  
  
## <a name="common-scenarios"></a>일반적인 시나리오  
 라우팅 서비스의 가장 기본적인 용도는 여러 대상 엔드포인트를 집계하여 클라이언트 응용 프로그램에 노출되는 엔드포인트의 수를 줄인 다음 메시지 필터를 사용하여 각 메시지를 올바른 대상으로 라우트하는 것입니다. 메시지는 특정 서비스에서 처리해야 하는 메시지 형식과 같은 논리적 또는 물리적 처리 요구 사항이나 특정 소스의 메시지 처리에 우선 순위를 제공하는 것과 같은 임의의 비즈니스 요구 사항에 따라 라우트될 수 있습니다. 다음 표에서는 몇 가지 일반적인 시나리오 및 이러한 시나리오가 발생하는 경우를 보여 줍니다.  
  
|시나리오|적용 가능한 상황|  
|--------------|--------------|  
|서비스 버전 관리|서비스의 여러 버전을 지원해야 하거나 앞으로 업데이트된 서비스를 배포할 가능성이 있는 경우|  
|서비스 데이터 분할|여러 호스트로 서비스를 분할해야 하는 경우|  
|동적 업데이트|변화하는 서비스 배포를 처리하기 위해 런타임에 라우팅 논리를 동적으로 다시 구성해야 하는 경우|  
|멀티캐스트|하나의 메시지를 여러 엔드포인트로 보내야 하는 경우|  
|프로토콜 브리징|하나의 전송 프로토콜을 통해 메시지를 받는데, 대상 엔드포인트가 이와 다른 프로토콜을 사용하는 경우|  
|오류 처리|네트워크 장애 및 통신 오류에 대비한 복구 기능을 제공해야 하는 경우|  
  
> [!NOTE]
>  여기에 제시된 시나리오의 다수는 특정 비즈니스 요구나 처리 요구 사항에 해당되지만 동적 업데이트를 지원하도록 계획하고 오류 처리를 활용하는 것은 많은 경우 최선의 방법으로 간주됩니다. 이를 통해 런타임에 라우팅 논리를 수정하여 일시적인 네트워크 및 통신 오류에서 복구할 수 있기 때문입니다.  
  
### <a name="service-versioning"></a>서비스 버전 관리  
 서비스의 새 버전을 도입할 때는 많은 경우 모든 클라이언트가 새 서비스로 전환할 때까지 이전 버전을 유지 관리해야 합니다. 이는 서비스가 완료되기까지 며칠, 몇 주 또는 몇 개월이 걸리는 장기 실행 프로세스인 경우 특히 중요합니다. 일반적으로 이를 위해서는 이전 버전에 대한 원래 엔드포인트를 유지하면서 새 서비스에 대한 새 엔드포인트 주소를 구현해야 합니다.  
  
 라우팅 서비스를 사용하면 클라이언트 응용 프로그램에서 메시지를 받도록 하나의 엔드포인트를 노출한 다음 메시지 내용에 따라 각 메시지를 올바른 서비스 버전으로 라우트할 수 있습니다. 가장 기본적인 구현은 메시지를 처리할 서비스의 버전을 나타내는 사용자 지정 헤더를 메시지에 추가하는 것입니다. 라우팅 서비스는 XPathMessageFilter를 사용하여 각 메시지에 사용자 지정 헤더가 있는지 여부를 검사하고 적절한 대상 엔드포인트로 메시지를 라우트합니다.  
  
 서비스 버전 관리 구성을 만드는 데 사용 되는 단계를 참조 하세요. [방법: 서비스 버전 관리](../../../../docs/framework/wcf/feature-details/how-to-service-versioning.md)합니다.
  
### <a name="service-data-partitioning"></a>서비스 데이터 분할  
 분산 환경을 디자인하는 경우 고가용성을 제공하고 개별 컴퓨터의 처리 로드를 줄이거나 특정 메시지 하위 집합에 전용 리소스를 제공하려면 처리 로드를 여러 컴퓨터로 분산하는 것이 바람직합니다. 라우팅 서비스는 전용 부하 분산 솔루션을 대신할 수는 없지만 내용 기반 라우팅 기능을 사용하면 내용 외에는 서로 비슷한 메시지를 특정 대상으로 라우트할 수 있습니다. 예를 들어 요구 사항에 따라 특정 클라이언트로부터 받은 메시지를 다른 클라이언트로부터 받은 메시지와 별개로 처리해야 하는 경우가 있습니다.  
  
 서비스 데이터 분할 구성을 만드는 데 단계를 참조 하세요. [방법: 서비스 데이터 분할](../../../../docs/framework/wcf/feature-details/how-to-service-data-partitioning.md)합니다.  
  
### <a name="dynamic-routing"></a>동적 라우팅  
 변화하는 비즈니스 요구를 충족하기 위해 더 새 버전의 서비스에 대한 경로를 추가하거나 라우팅 조건을 변경하거나 필터가 특정 메시지를 라우트하는 대상 엔드포인트를 변경하는 등 라우팅 구성을 수정해야 하는 경우가 많습니다. 라우팅 서비스를 사용하면 런타임 중에 새 RoutingConfiguration을 제공할 수 있도록 하는 <xref:System.ServiceModel.Routing.RoutingExtension>을 통해 이를 수행할 수 있습니다. 새 구성은 즉시 적용되지만 라우팅 서비스에서 처리하는 새 세션에만 영향을 미칩니다.  
  
 동적 라우팅을 구현 하는 단계를 참조 하세요. [방법: 동적 업데이트](../../../../docs/framework/wcf/feature-details/how-to-dynamic-update.md)합니다.
  
### <a name="multicast"></a>멀티캐스트  
 메시지를 라우트할 때는 일반적으로 각 메시지를 하나의 특정 대상 엔드포인트로 라우트합니다.  그러나 하나의 메시지 복사본을 여러 대상 엔드포인트로 라우트해야 하는 경우도 있습니다. 멀티캐스트 라우팅을 수행하려면 다음 조건이 충족되어야 합니다.  
  
- 요청-회신에서는 클라이언트 응용 프로그램이 요청에 대한 응답으로 하나의 회신만 수신할 수 있으므로 채널 셰이프가 요청-회신이면 안 됩니다.  
  
- 여러 필터를 반환 해야 합니다 **true** 메시지를 평가할 때.  
  
 이러한 조건이 충족되면 true를 반환하는 필터에 연결된 각 대상 엔드포인트가 메시지 복사본을 받게 됩니다.  
  
### <a name="protocol-bridging"></a>프로토콜 브리징  
 서로 다른 SOAP 프로토콜 사이에서 메시지를 라우트하는 경우 라우팅 서비스는 WCF API를 사용하여 메시지의 프로토콜을 다른 프로토콜로 변환합니다. 이 동작은 라우팅 서비스에 의해 노출되는 서비스 엔드포인트가 메시지가 라우트되는 클라이언트 엔드포인트와 다른 프로토콜을 사용하는 경우 자동으로 발생합니다. 사용되는 프로토콜이 표준이 아닌 경우 이 동작을 비활성화할 수 있지만 그러면 사용자가 직접 브리징 코드를 제공해야 합니다.
  
### <a name="error-handling"></a>오류 처리  
 분산 환경에서는 일시적인 네트워크 또는 통신 오류가 종종 발생합니다. 라우팅 서비스와 같은 매개 서비스가 없는 경우 이러한 오류를 처리하는 데 따르는 부담은 클라이언트 응용 프로그램의 몫입니다. 클라이언트 응용 프로그램에 네트워크 또는 통신 오류가 발생할 경우 재시도를 수행하기 위한 특정 논리 및 대체 위치에 대한 정보가 포함되지 않은 경우 사용자는 메시지가 대상 서비스에 의해 성공적으로 처리될 때까지 여러 차례 메시지를 전송해야 하는 시나리오에 직면할 수 있습니다. 이 경우 응용 프로그램이 불안정한 것으로 인식되어 고객 불만족으로 이어질 수 있습니다.  
  
 라우팅 서비스는 네트워크 또는 통신 관련 오류에 직면한 메시지를 위한 견고한 오류 처리 기능을 제공하여 이 시나리오의 해결을 시도합니다. 가능한 대상 엔드포인트 목록을 만들고 이 목록을 각 메시지 필터와 연결하면 가능한 대상이 하나밖에 없는 경우 발생하는 단일 장애 지점을 제거할 수 있습니다. 오류가 발생하는 경우 라우팅 서비스는 메시지가 배달되거나 통신 이외의 오류가 발생하거나 모든 엔드포인트가 소진될 때까지 목록의 다음 엔드포인트로 메시지 배달을 시도합니다.  
  
 오류 처리를 구성 하는 단계를 참조 하세요. [방법: 오류 처리](../../../../docs/framework/wcf/feature-details/how-to-error-handling.md)합니다.
  
### <a name="in-this-section"></a>섹션 내용  
 [방법: 서비스 버전 관리](../../../../docs/framework/wcf/feature-details/how-to-service-versioning.md)  
  
 [방법: 서비스 데이터 분](../../../../docs/framework/wcf/feature-details/how-to-service-data-partitioning.md)  
  
 [방법: 동적 업데이트](../../../../docs/framework/wcf/feature-details/how-to-dynamic-update.md)  
  
 [방법: 오류 처리](../../../../docs/framework/wcf/feature-details/how-to-error-handling.md)  
  
## <a name="see-also"></a>참고자료

- [라우팅 소개](../../../../docs/framework/wcf/feature-details/routing-introduction.md)
