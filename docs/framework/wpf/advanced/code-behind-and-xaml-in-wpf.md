---
title: WPF의 코드 숨김 및 XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], code-behind
- code-behind files [WPF], XAML
ms.assetid: 9df6d3c9-aed3-471c-af36-6859b19d999f
ms.openlocfilehash: 6a47f5a93cb161c9a87df25403cc86247619cd81
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610528"
---
# <a name="code-behind-and-xaml-in-wpf"></a>WPF의 코드 숨김 및 XAML
<a name="introduction"></a> 코드 숨김 태그 정의 된 개체와 결합 되는 코드를 설명 하는 용어는 때를 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 페이지는 태그 컴파일된 합니다. 이 항목에서는 코드에 대 한 대체 인라인 코드 메커니즘 및 코드 숨김에 대 한 요구 사항 설명 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]합니다.  
  
 이 항목에는 다음과 같은 단원이 포함되어 있습니다.  
  
- [필수 조건](#Prerequisites)  
  
- [코드 숨김 및 XAML 언어](#codebehind_and_the_xaml_language)  
  
- [코드 숨김, 이벤트 처리기 및 WPF의 Partial 클래스 요구 사항](#Code_behind__Event_Handler__and_Partial_Class)  
  
- [x:Code](#x_Code)  
  
- [인라인 코드 제한 사항](#Inline_Code_Limitations)  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>전제 조건  
 이 항목에서는 읽었다고 가정 합니다 [XAML 개요 (WPF)](xaml-overview-wpf.md) 대 한 기본 지식이 있고는 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 및 개체 지향 프로그래밍 합니다.  
  
<a name="codebehind_and_the_xaml_language"></a>   
## <a name="code-behind-and-the-xaml-language"></a>코드 숨김 및 XAML 언어  
 XAML 언어 태그 파일에서에서 태그 파일을 사용 하 여 코드 파일을 연결할 수 있게 해 주는 언어 수준 기능을 포함 합니다. XAML 언어에서 언어 기능을 정의 하는 특히 [X:class 지시문](../../xaml-services/x-class-directive.md)를 [X:subclass 지시문](../../xaml-services/x-subclass-directive.md), 및 [X:classmodifier 지시문](../../xaml-services/x-classmodifier-directive.md)합니다. 정확히 어떻게 코드를 생성 하는 방법과 태그와 코드를 통합 하는 XAML 언어에서 지정 하는 새로운의 일부가 아닙니다. 코드를 통합 하는 방법을 결정 하는 WPF와 같은 프레임 워크 에서만, 모든이 위해서는 XAML을 사용 하 여 응용 프로그램 프로그래밍 모델 및 빌드 작업 또는 기타 지원 하는 방법입니다.  
  
<a name="Code_behind__Event_Handler__and_Partial_Class"></a>   
## <a name="code-behind-event-handler-and-partial-class-requirements-in-wpf"></a>코드 숨김, 이벤트 처리기 및 WPF의 Partial 클래스 요구 사항  
  
- Partial 클래스는 루트 요소를 지 원하는 형식에서 파생 되어야 합니다.  
  
- 태그 컴파일 빌드 작업의 기본 동작에 따라 비워 둘 수 있습니다 파생 partial 클래스 정의의 코드 숨김 우변 note 합니다. 컴파일된 결과 지정 되지 않은 경우에 부분 클래스에 대 한 기본 지원 형식 페이지 루트를 가정 합니다. 그러나이 동작에 의존 아닙니다이 가장 좋습니다.  
  
- 코드 숨김에 쓰기 이벤트 처리기는 인스턴스 메서드여야 하 고 정적 메서드 일 수 없습니다. 이러한 메서드는 partial 클래스에서 지정 된 CLR 네임 스페이스 내에서 정의 해야 `x:Class`합니다. 지시 하기 위해 이벤트 처리기의 이름을 정규화 할 수 없습니다는 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 프로세서가 다른 클래스 범위에서 이벤트 연결에 대 한 이벤트 처리기를 찾도록 합니다.  
  
- 처리기는 지원 형식 시스템에서 적절 한 이벤트에 대 한 대리자를 일치 해야 합니다.  
  
- Microsoft Visual Basic 언어에 대 한 특히 따르면 언어별 `Handles` 인스턴스 및 이벤트 처리기의 선언에서 특성을 사용 하 여 처리기를 연결 하는 대신에서 사용 하 여 처리기를 연결할 키워드 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]합니다. 그러나이 기술은는 몇 가지 제한 사항이 있으므로 합니다 `Handles` 키워드의 특정 기능을 모두 지원할 수 없습니다는 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 같은 특정 이벤트 시스템 라우트된 이벤트 시나리오 또는 연결 된 이벤트입니다. 자세한 내용은 참조 하세요 [Visual Basic 및 WPF 이벤트 처리](visual-basic-and-wpf-event-handling.md)합니다.  
  
<a name="x_Code"></a>   
## <a name="xcode"></a>x:Code  
 [X:code](../../xaml-services/x-code-intrinsic-xaml-type.md) 에 정의 된 지시문 요소 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]합니다. `x:Code` 지시문 요소 인라인 프로그래밍 코드를 포함할 수 있습니다. 정의 된 인라인이 있는 코드와 상호 작용할 수는 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 동일한 페이지에 있습니다. 다음 예제에서는 인라인 C# 코드를 보여 줍니다. 내는 코드를 `x:Code` 요소 및 코드로 묶어야 `<CDATA[`... `]]>` 에 대 한 콘텐츠를 이스케이프 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]되도록를 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 프로세서 (중 하나를 해석 합니다 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 스키마 또는 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 스키마) 내용을 해석 하려고 시도 하지 것입니다 글자 그대로 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)].  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithInlineCode](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page4.xaml#buttonwithinlinecode)]  
  
<a name="Inline_Code_Limitations"></a>   
## <a name="inline-code-limitations"></a>인라인 코드 제한 사항  
 인라인 코드의 사용을 제한 하거나 방지를 고려해 야 합니다. 아키텍처 및 코딩 개념 측면에서 태그와 코드 숨김 간의 분리를 유지 관리 하는 유지 디자이너와 개발자 역할 훨씬 고유 합니다. 자세한 기술 수준에서 인라인 코드에 작성 하는 코드 좋지 않을 수 있습니다를 작성 하려면 항상 쓸 때문에 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 생성 된 partial 클래스 및 기본 XML 네임 스페이스 매핑을 사용할 수 있습니다. 추가할 수 없으므로 `using` 문을 정규화 해야 다양 한 확인 하는 API 호출 합니다. 기본값 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 전부는 아니지만 대부분의 매핑을 포함 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 에 있는 네임 스페이스는 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 어셈블리 형식 및 다른 CLR 네임 스페이스 내에 포함 된 멤버에 대 한 호출을 정규화 해야 합니다. 도 정의할 수 없습니다 partial 클래스 이외의 다른 항목에서 인라인 코드를 참조 하는 모든 사용자 코드 엔터티 멤버 또는 변수로 생성 된 partial 클래스 내에 있어야 합니다. 다른 언어 프로그래밍 같은 특정 기능이 매크로 또는 `#ifdef` 전역 변수 또는 빌드 변수 로부터 사용할 수 없는 합니다. 자세한 내용은 [X:code 내장 XAML 형식](../../xaml-services/x-code-intrinsic-xaml-type.md)합니다.  
  
## <a name="see-also"></a>참고자료

- [XAML 개요(WPF)](xaml-overview-wpf.md)
- [x:Code 내장 XAML 형식](../../xaml-services/x-code-intrinsic-xaml-type.md)
- [WPF 응용 프로그램 빌드](../app-development/building-a-wpf-application-wpf.md)
- [XAML 구문 정보](xaml-syntax-in-detail.md)
