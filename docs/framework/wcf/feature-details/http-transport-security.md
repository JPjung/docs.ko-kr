---
title: HTTP 전송 보안
ms.date: 03/30/2017
ms.assetid: d3439262-c58e-4d30-9f2b-a160170582bb
ms.openlocfilehash: 456df42848c009dcf42022ac674a1d27e5b33972
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487024"
---
# <a name="http-transport-security"></a>HTTP 전송 보안
HTTP를 전송으로 사용하는 경우 SSL(Secure Sockets Layer) 구현에서 보안을 제공합니다. SSL은 서비스를 클라이언트에 인증한 다음 채널에 기밀성(암호화)을 제공하기 위해 인터넷에서 널리 사용됩니다. 이 항목에서는 SSL 작동 원리 및 Windows Communication Foundation (WCF)에서 구현 되는 방법을 설명 합니다.  
  
## <a name="basic-ssl"></a>기본 SSL  
 SSL 작동 방식은 일반적인 시나리오, 이 경우 은행 웹 사이트를 통해 가장 효과적으로 설명됩니다. 이 사이트에서는 고객이 사용자 이름과 암호를 사용하여 로그온할 수 있습니다. 인증된 후 사용자는 계좌 잔고 보기, 청구서 지급, 다른 계좌로 자금 이체 등의 트랜잭션을 수행할 수 있습니다.  
  
 사용자는 먼저 사이트를 방문 하면 SSL 메커니즘은 일련의 협상, 호출을 시작 하는 한 *핸드셰이크*, 사용자의 클라이언트 (이 경우 Internet Explorer)를 사용 하 여. SSL은 먼저 은행 사이트를 고객에게 인증합니다. 고객이 먼저 사용자 이름과 암호를 입력하도록 부추기는 스푸프가 아니라 실제 사이트와 통신하고 있음을 알아야 하므로 이는 필수적인 단계입니다. SSL은 VeriSign 등의 신뢰할 수 있는 기관에서 제공한 SSL 인증서를 사용하여 이 인증을 수행합니다. 논리는 다음과 같이 이루어집니다. VeriSign이 은행 사이트의 id에 대 한 보증 합니다. Internet Explorer에서 VeriSign을 신뢰하므로 사이트가 신뢰됩니다. VeriSign에서 확인하려면 VeriSign 로고를 클릭하여 이 작업을 수행할 수도 있습니다. 만료 날짜와 발급된 대상(은행 사이트)이 포함된 인증서가 제공됩니다.  
  
 보안 세션을 시작하기 위해 클라이언트는 서명, 해시 생성, 암호화 및 해독에 사용할 수 있는 암호화 알고리즘 목록과 함께 "hello"에 해당하는 내용을 서버로 보냅니다. 이에 응답하여 사이트에서 승인 및 선택한 알고리즘 모음 중 하나를 보냅니다. 이 초기 핸드셰이크 중에 양쪽이 모두 nonce를 보내고 받습니다. A *nonce* 는 임의로 생성 된 조각에에서 사용 되는, 사이트의 공개 키와 함께 해시를 만드는 데이터입니다. A *해시* SHA1 같은 표준 알고리즘을 사용 하 여 두 번호에서 파생 된 새입니다. 또한 클라이언트와 사이트는 메시지를 교환하여 사용할 해시 알고리즘을 합의합니다. 해시는 고유하며 메시지 암호화 및 해독을 위해 클라이언트와 사이트 간의 세션에만 사용됩니다. 클라이언트와 서비스 둘 다에 원래 nonce와 인증서의 공개 키가 있으므로 양쪽이 모두 동일한 해시를 생성할 수 있습니다. 따라서 클라이언트는 (a) 합의된 알고리즘을 사용하여 데이터를 통해 해시를 계산하고 (b) 이 해시를 서비스에서 전송한 해시와 비교하여 서비스에서 전송한 해시의 유효성을 검사합니다. 두 해시가 일치하면 클라이언트에서 해시가 조작되지 않았음을 확신합니다. 클라이언트는 이 해시를 키로 사용하여 다른 새 해시가 포함된 메시지를 암호화할 수 있습니다. 서비스는 해시를 사용하여 메시지를 해독하고 최종 해시에서 두 번째 해시를 복구합니다. 이제 누적 정보(nonce, 공개 키 및 기타 데이터)가 양쪽에 알려지며 최종 해시(또는 마스터 키)를 만들 수 있습니다. 이 최종 키는 맨 마지막에서 두 번째 해시를 사용하여 암호화된 상태로 전송됩니다. 마스터 키를 세션의 나머지 부분에 대 한 메시지 암호화 및 해독에 사용 됩니다. 클라이언트와 서비스 모두 동일한 키를 사용 하므로이 라고 한 *세션 키*합니다.  
  
 세션 키는 대칭 키 또는 "공유 암호"로 간주되기도 합니다. 대칭 키가 있으면 트랜잭션의 양쪽에 필요한 계산이 감소하므로 이는 중요합니다. 모든 메시지가 nonce와 해시의 새 교환을 요구하면 성능이 저하됩니다. 따라서 SSL의 최종 목적은 대칭 키를 사용하여 보안과 효율성을 높이면서 메시지가 양쪽 간에 자유롭게 이동할 수 있게 하는 것입니다.  
  
 프로토콜이 사이트마다 다를 수 있으므로 이전 설명은 수행되는 작업의 단순한 버전입니다. 또한 클라이언트와 사이트가 모두 핸드셰이크 중에 알고리즘 방식으로 결합되어 데이터 교환 프로세스에 복잡성과 보호 기능을 추가하는 nonce를 생성할 수 있습니다.  
  
### <a name="certificates-and-public-key-infrastructure"></a>인증서 및 공개 키 인프라  
 핸드셰이크 중에 서비스는 해당 SSL 인증서를 클라이언트로 보냅니다. 인증서에는 만료 날짜, 발급 기관, 사이트의 URI(Uniform Resource Identifier) 같은 정보가 들어 있습니다. 클라이언트는 원래 연결한 URI와 이 URI를 비교하여 일치하는지 확인하고 날짜 및 발급 기관도 확인합니다.  
  
 두 이라고 하며 모든 인증서에 두 개의 키, 개인 키와 공개 키를 *교환 키 쌍*합니다. 간단히 말해서 개인 키는 인증서의 소유자에게만 알려지고 공개 키는 인증서에서 읽을 수 있습니다. 한 키를 사용하여 다이제스트, 해시 또는 다른 키를 암호화하거나 해독할 수 있지만 반대 작업으로만 사용할 수 있습니다. 예를 들어 클라이언트가 공개 키로 암호화되는 경우에만 사이트에서 개인 키를 사용하여 메시지를 해독할 수 있습니다. 마찬가지로 사이트가 개인 키로 암호화되는 경우 클라이언트는 공개 키를 사용하여 해독할 수 있습니다. 이 경우 개인 키로 암호화된 메시지만 공개 키로 해독할 수 있으므로 개인 키의 소유자하고만 메시지가 교환된다는 것을 클라이언트에 보증할 수 있습니다. 사이트는 공개 키를 사용하여 암호화한 클라이언트와 메시지를 교환합니다. 그러나 이 교환은 초기 핸드셰이크에 대해서만 보안이 유지되며, 이 때문에 실제 대칭 키를 만들기 위해 훨씬 더 많은 작업이 수행됩니다. 그렇지만 모든 통신을 수행하려면 서비스에 올바른 SSL 인증서가 있어야 합니다.  
  
## <a name="implementing-ssl-with-wcf"></a>WCF를 사용하여 SSL 구현  
 HTTP 전송 보안 (또는 SSL) WCF 외부에서 제공 됩니다. 다음 두 가지 방법 중 하나로 SSL을 구현할 수 있습니다. 결정 요인은 응용 프로그램 호스팅 방법입니다.  
  
- 인터넷 정보 서비스 (IIS) WCF 호스트를 사용 하는 경우 SSL 서비스를 설정 하려면 IIS 인프라를 사용 합니다.  
  
- 자체 호스팅된 WCF 응용 프로그램을 만드는 경우 HttpCfg.exe 도구를 사용 하 여 주소에 SSL 인증서를 바인딩할 수 있습니다.  
  
### <a name="using-iis-for-transport-security"></a>전송 보안에 IIS 사용  
  
#### <a name="iis-70"></a>IIS 7.0  
 IIS 7.0을 보안 호스트 (SSL 사용)를 설정 하려면을 참조 하세요 [IIS 7.0에서 Secure Sockets Layer 구성](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc771438(v=ws.10))합니다.  
  
IIS 7.0을 사용 하 여 사용할 인증서를 구성 하려면 [IIS 7.0에서 서버 인증서 구성](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10))합니다.  
  
#### <a name="iis-60"></a>IIS 6.0  
 IIS 6.0을 보안 호스트 (SSL 사용)를 설정 하려면을 참조 하세요 [Secure Sockets Layer 구성](https://go.microsoft.com/fwlink/?LinkId=88601)합니다.  
  
 IIS 6.0을 사용 하 여 사용할 인증서를 구성 하려면 [Certificates_IIS_SP1_Ops](https://go.microsoft.com/fwlink/?LinkId=88602)합니다.  
  
### <a name="using-httpcfg-for-ssl"></a>SSL에 HttpCfg 사용  
 자체 호스팅된 WCF 응용 프로그램을 만드는 경우에 사용 가능한 HttpCfg.exe 도구를 다운로드 합니다 [Windows XP 서비스 팩 2 지원 도구 사이트](https://go.microsoft.com/fwlink/?LinkId=29002)합니다.  
  
 HttpCfg.exe 도구를 사용 하 여 X.509 인증서로 포트를 설정 하는 방법에 대 한 자세한 내용은 참조 하세요. [방법: SSL 인증서로 포트 구성](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)합니다.  
  
## <a name="see-also"></a>참고자료

- [전송 보안](../../../../docs/framework/wcf/feature-details/transport-security.md)
- [메시지 보안](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)
