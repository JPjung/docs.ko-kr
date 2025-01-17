---
ms.openlocfilehash: c8a6870a9d34889dd8f5305035744bfc63be6af6
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67856981"
---
### <a name="support-special-relative-uri-notation-when-unicode-is-present"></a>유니코드가 있는 경우 특별한 상대 URI 표기법 지원

|   |   |
|---|---|
|세부 정보|유니코드를 포함하는 특정 상대 URI에서 <xref:System.Uri.TryCreate%2A>를 호출할 때 <xref:System.Uri>는 더 이상 <xref:System.NullReferenceException>을 throw하지 않습니다. <xref:System.NullReferenceException>의 가장 간단한 재현은 동등한 두 개의 명령문을 사용하여 아래와 같습니다.<pre><code class="lang-csharp">bool success = Uri.TryCreate(&quot;http:%C3%A8&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;bool success = Uri.TryCreate(&quot;http:&#232;&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;</code></pre><xref:System.NullReferenceException>을 재현하려면 다음 항목은 true여야 합니다.<ul><li>‘http:’를 앞에 추가하고 ‘//’를 뒤에 오지 않게 하여 URI를 상대로 지정해야 합니다.</li><li>URI는 백분율로 인코딩된 유니코드 또는 예약되지 않은 기호를 포함해야 합니다.</li></ul>|
|제안|이 동작에 따라 사용자는 상대 URI를 허용하지 않도록 URI를 만들 때 대신 <xref:System.UriKind.Absolute?displayProperty=nameWithType>을 지정해야 합니다.|
|범위|Microsoft Edge|
|버전|4.7.2|
|형식|런타임|
|영향을 받는 API|<ul><li><xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li></ul>|

