---
title: 알고리즘 이름을 암호화 클래스에 매핑
ms.date: 03/30/2017
helpviewer_keywords:
- mapping algorithm names
- cryptography, mapping algorithm names
- cryptographic algorithms
- names [.NET Framework], algorithm mapping
ms.assetid: 01327c69-c5e1-4ef6-b73f-0a58351f0492
ms.openlocfilehash: c76f80273d37f838ca52efd3b8f8c028b76a4d30
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66832679"
---
# <a name="mapping-algorithm-names-to-cryptography-classes"></a>알고리즘 이름을 암호화 클래스에 매핑
네 가지 방법으로 개발자는 Windows 소프트웨어 개발 키트 (SDK)를 사용 하는 암호화 개체를 만들 수 있습니다.  
  
- 사용 하 여 개체를 만들 합니다 **새** 연산자입니다.  
  
- 호출 하 여 특정 암호화 알고리즘을 구현 하는 개체를 만드는 합니다 **만들기** 해당 알고리즘에 대 한 추상 클래스에서 메서드.  
  
- 호출 하 여 특정 암호화 알고리즘을 구현 하는 개체를 만들기는 <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> 메서드.  
  
- 호출 하 여 (예: 대칭 블록 암호화) 암호화 알고리즘의 클래스를 구현 하는 개체 만들기를 **만들기** 알고리즘의 해당 형식에 대 한 추상 클래스에서 메서드 (같은 <xref:System.Security.Cryptography.SymmetricAlgorithm>).  
  
 예를 들어, 개발자는 바이트 집합의 SHA1 해시를 계산 합니다. <xref:System.Security.Cryptography> 네임 스페이스에는 SHA1 알고리즘, 하나의 순수 하 게 관리 되는 구현과 CryptoAPI를 래핑하는 것의 두 가지 구현이 포함 되어 있습니다. 개발자는 특정 SHA1 구현을 인스턴스화할 수도 (같은 <xref:System.Security.Cryptography.SHA1Managed>)를 호출 하 여는 **새** 연산자입니다. 그러나 SHA1 해시 알고리즘을 구현 하는 클래스와 공용 언어 런타임을 로드 하는 클래스는 중요 하지 않습니다, 경우 개발자 개체를 만들 수를 호출 하 여는 <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> 메서드. 이 메서드를 호출 **System.Security.Cryptography.CryptoConfig.CreateFromName("System.Security.Cryptography.SHA1")** 에 SHA1 해시 알고리즘의 구현을 반환 해야 합니다.  
  
 개발자를 호출할 수도 **System.Security.Cryptography.CryptoConfig.CreateFromName("SHA1")** 하므로 기본적으로 암호화 구성에는.NET Framework에서 제공 하는 알고리즘에 대 한 짧은 이름을 포함 됩니다.  
  
 개발자를 호출할 수 있는 해시 알고리즘을 사용 하는 중요 하지 않습니다, 경우를 <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> 해시 변환을 구현 하는 개체를 반환 하는 메서드.  
  
## <a name="mapping-algorithm-names-in-configuration-files"></a>구성 파일에서 알고리즘 이름 매핑  
 기본적으로 런타임에 반환을 <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> 모든 네 가지 시나리오에 대 한 개체입니다. 그러나 컴퓨터 관리자 마지막 두 시나리오의 메서드가 반환 하는 개체의 형식을 변경할 수 있습니다. 이 위해 컴퓨터 구성 파일 (Machine.config)에서 사용 하려면 클래스에 알고리즘 이름을 매핑해야 합니다.  
  
 다음 예제에서는 런타임을 구성 하는 방법을 보여 줍니다 있도록 **System.Security.Cryptography.SHA1.Create**하십시오 **System.Security.CryptoConfig.CreateFromName("SHA1")** , 및  **System.Security.Cryptography.HashAlgorithm.Create** 반환을 `MySHA1HashClass` 개체입니다.  
  
```xml  
<configuration>  
   <!-- Other configuration settings. -->  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass MySHA1Hash="MySHA1HashClass, MyAssembly  
                  Culture='en', PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="SHA1" class="MySHA1Hash"/>  
            <nameEntry name="System.Security.Cryptography.SHA1"  
                       class="MySHA1Hash"/>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MySHA1Hash"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
 특성의 이름을 지정할 수 있습니다 합니다 [< cryptoClass\> 요소](../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) (이전 예제에서는 특성의 이름을 `MySHA1Hash`). 특성의 값을  **\<cryptoClass >** 요소는 공용 언어 런타임 클래스를 찾고 사용 하는 문자열입니다. 에 지정 된 요구 사항을 충족 하는 모든 문자열을 사용할 수 있습니다 [정규화 된 형식 이름 지정](../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)합니다.  
  
 많은 알고리즘 이름이 동일한 클래스에 매핑할 수 있습니다. 합니다 [ \<m t r y > 요소](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) 클래스에 한 개의 알고리즘 이름을 매핑합니다. **이름을** 특성을 호출할 때 사용 되는 문자열로 수 합니다 **System.Security.Cryptography.CryptoConfig.CreateFromName** 합니다 에서추상암호화클래스의이름또는메서드<xref:System.Security.Cryptography> 네임 스페이스입니다. 값을 **클래스** 특성은 특성의 이름 합니다  **\<cryptoClass >** 요소입니다.  
  
> [!NOTE]
>  SHA1 알고리즘을 호출 하 여 가져올 수는 <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> 또는 **Security.CryptoConfig.CreateFromName("SHA1")** 메서드. 각 메서드는 SHA1 알고리즘을 구현 하는 개체를 반환 하는 것만 보장 합니다. 각 알고리즘의 이름을 구성 파일에서 동일한 클래스에 매핑할 필요가 없습니다.  
  
 기본 이름 및 매핑할 클래스의 목록을 참조 하세요. <xref:System.Security.Cryptography.CryptoConfig>합니다.  
  
## <a name="see-also"></a>참고자료

- [Cryptographic Services](../../../docs/standard/security/cryptographic-services.md)
- [암호화 클래스 구성](../../../docs/framework/configure-apps/configure-cryptography-classes.md)
