---
title: 클라이언트 쪽 UI 자동화 공급자 구현
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, client-side provider implementation
- client-side UI Automation provider, implementation
- provider implementation, UI Automation
ms.assetid: 3584c0a1-9cd0-4968-8b63-b06390890ef6
ms.openlocfilehash: 02d77dfeb7a00292639131cad72cff7e079704c5
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802218"
---
# <a name="client-side-ui-automation-provider-implementation"></a>클라이언트 쪽 UI 자동화 공급자 구현
> [!NOTE]
>  이 설명서는 <xref:System.Windows.Automation> 네임스페이스에 정의된 관리되는 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 클래스를 사용하려는 .NET Framework 개발자를 위한 것입니다. 에 대 한 최신 정보에 대 한 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]를 참조 하세요 [Windows Automation API: UI 자동화](https://go.microsoft.com/fwlink/?LinkID=156746)합니다.  
  
 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] , [!INCLUDE[TLA#tla_ms](../../../includes/tlasharptla-ms-md.md)] , 및 [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]를 포함하여 서로 다른 여러 [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]프레임워크가 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]운영 체제 내에서 사용 중입니다. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 이 UI 요소에 대한 정보를 클라이언트에 노출합니다. 그러나 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 자체는 이러한 프레임워크에 있는 여러 형식의 컨트롤과 컨트롤에서 정보를 추출하는 데 필요한 기술은 인식하지 않습니다. 대신, 이 작업은 공급자라고 하는 개체가 담당합니다. 공급자는 특정 컨트롤에서 정보를 추출하고 이 정보를 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]에 전달한 다음 일관된 방식으로 클라이언트에게 제공합니다.  
  
 공급자는 서버쪽 또는 클라이언트쪽에 존재할 수 있습니다. 서버쪽 공급자는 컨트롤 자체에서 구현됩니다. [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 으로 작성된 모든 타사 컨트롤에 유의하여 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 요소가 공급자를 구현합니다.  
  
 그러나 [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] 및 [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] 에 있는 컨트롤과 같은 이전의 컨트롤은 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]을 직접 지원하지 않습니다. 이러한 컨트롤은 클라이언트 프로세스에 존재하며 크로스 프로세스 통신을 사용하여(예: 컨트롤에서 창 메시지 모니터링) 컨트롤에 대한 정보를 얻는 공급자가 대신 제공합니다. 이러한 클라이언트쪽 공급자를 프록시라고도 합니다.  
  
 [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] 표준에 대 한 공급자 제공 [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] 및 Windows Forms 컨트롤입니다. 또한 대체 (fallback) 공급자를 제공 부분 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 하지만 Microsoft Active Accessibility 구현이 프록시 또는 다른 서버 쪽 공급자가 제공 하지는 모든 컨트롤에 지원 합니다. 이러한 공급자는 모두 자동으로 로드되며 클라이언트 애플리케이션에 사용할 수 있습니다.  
  
 지원에 대 한 자세한 내용은 [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] Windows Forms 컨트롤 살펴보고 [표준 컨트롤에 대 한 UI 자동화 지원](../../../docs/framework/ui-automation/ui-automation-support-for-standard-controls.md)합니다.  
  
 애플리케이션이 다른 클라이언트쪽 공급자를 등록할 수도 있습니다.  
  
<a name="Distributing_Client-Side_Providers"></a>   
## <a name="distributing-client-side-providers"></a>클라이언트쪽 공급자 배포  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 이 관리 코드 어셈블리에서 클라이언트쪽 공급자를 찾아야 합니다. 이 어셈블리의 네임스페이스 이름은 어셈블리와 동일해야 합니다. 예를 들어, ContosoProxies.dll이라는 어셈블리에는 ContosoProxies 네임스페이스가 포함됩니다. 네임스페이스 내에서 <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders> 클래스를 만듭니다. 정적 <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders.ClientSideProviderDescriptionTable> 필드의 구현에서, 공급자를 설명하는 <xref:System.Windows.Automation.ClientSideProviderDescription> 구조의 배열을 만듭니다.  
  
<a name="Registering_and_Configuring_Client-Side_Providers"></a>   
## <a name="registering-and-configuring-client-side-providers"></a>클라이언트쪽 공급자 등록 및 구성  
 [!INCLUDE[TLA#tla_dll](../../../includes/tlasharptla-dll-md.md)] 의 클라이언트쪽 공급자는 <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviderAssembly%2A>을 호출하여 로드됩니다. 공급자를 사용하기 위해 클라이언트 애플리케이션에 추가적인 조치가 필요하지 않습니다.  
  
 클라이언트의 자체 코드에 구현된 공급자가 <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>을 사용하여 등록됩니다. 이 메서드는 <xref:System.Windows.Automation.ClientSideProviderDescription> 구조의 배열을 인수로 사용하고, 각각 다음과 같은 속성을 지정합니다.  
  
- 공급자 개체를 만드는 콜백 함수.  
  
- 공급자가 제공하는 컨트롤의 클래스 이름.  
  
- 공급자가 제공하는 애플리케이션의 이미지 이름(일반적으로 실행 파일의 전체 이름).  
  
- 대상 애플리케이션에서 발견된 창 클래스에 대해 클래스 이름이 일치되는 방법을 제어하는 플래그.  
  
 마지막 두 매개 변수는 선택 사항입니다. 클라이언트가 여러 애플리케이션에 다양한 공급자를 사용하려는 경우 대상 애플리케이션의 이미지 이름을 지정할 수 있습니다. 예를 들어, 클라이언트는 Multiple View 패턴을 지원하는 알려진 애플리케이션에서 [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] 목록 뷰 컨트롤에 특정 공급자를 사용하고, 이 패턴을 지원하지 않는 다른 알려진 애플리케이션에서 비슷한 컨트롤에 다른 공급자를 사용할 수 있습니다.  
  
## <a name="see-also"></a>참고자료

- [클라이언트 쪽 UI 자동화 공급자 만들기](../../../docs/framework/ui-automation/create-a-client-side-ui-automation-provider.md)
- [클라이언트 응용 프로그램에서 UI 자동화 공급자 구현](../../../docs/framework/ui-automation/implement-ui-automation-providers-in-a-client-application.md)
