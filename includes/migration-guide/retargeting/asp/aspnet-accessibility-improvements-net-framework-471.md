---
ms.openlocfilehash: 100b34941b045619c7424921f9315e679f173a60
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858952"
---
### <a name="aspnet-accessibility-improvements-in-net-framework-471"></a>.NET Framework 4.7.1의 ASP.NET 액세스 가능성 향상

|   |   |
|---|---|
|세부 정보|.NET Framework 4.7.1부터 ASP.NET은 ASP.NET 웹 컨트롤이 Visual Studio의 액세스 가능성 기술과 연동하는 방식을 개선하여 ASP.NET 고객을 보다 잘 지원하도록 했습니다.  여기에는 다음과 같은 변경이 포함됩니다.<ul><li>자세히 보기 마법사의 필드 추가 대화 상자 또는 ListView 마법사의 ListView 구성 대화 상자와 같이 컨트롤에서 누락된 UI 액세스 가능성 패턴을 구현하도록 변경됨.</li><li>데이터 호출기 필드 편집기와 같이 고대비 모드에서 디스플레이를 개선하도록 변경됨.</li><li>DataPager 컨트롤의 호출기 필드 편집 마법사의 필드 대화 상자, ObjectContext 구성 대화 상자 또는 데이터 원본 구성 마법사의 데이터 선택 구성 대화 상자와 같은 컨트롤의 키보드 탐색 환경을 개선하도록 변경됨.</li></ul>|
|제안|<strong>이러한 변경을 선택 또는 해제하는 방법</strong> Visual Studio Designer가 이러한 변경의 이점을 활용하도록 하려면 .NET Framework 4.7.1 이상에서 실행해야 합니다. 웹 애플리케이션은 다음과 같은 방법으로 이러한 변경의 이점을 활용할 수 있습니다.<ul><li>기본적으로 다음 AppContext 스위치를 사용하여 새로운 액세스 가능성 기능을 지원하는 Visual Studio 2017 15.3 이상을 설치합니다.</li><li>다음 예제와 같이 devenv.exe.config 파일의 <code>&lt;runtime&gt;</code> 섹션에 <code>Switch.UseLegacyAccessibilityFeatures</code> AppContext 스위치를 추가하고 이를 <code>false</code>로 설정하여 레거시 액세스 가능성 동작을 옵트아웃합니다.</li></ul><pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;...&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false&#39;  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot; /&gt;&#13;&#10;...&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>.NET Framework 4.7.1 이상을 대상으로 하고 레거시 액세스 가능성 동작을 유지하려는 애플리케이션은 이 AppContext 스위치를 <code>true</code>로 명확하게 설정하여 레거시 액세스 가능성 기능 사용을 옵트인할 수 있습니다.|
|범위|부|
|버전|4.7.1|
|형식|대상 변경|

