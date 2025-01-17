---
title: WPF에서 System.Xaml로 마이그레이션된 형식
ms.date: 03/30/2017
helpviewer_keywords:
- WPF XAML [XAML Services], migration to System.Xaml
- XAML [XAML Services], System.Xaml and WPF
- System.Xaml [XAML Services], types migrated from WPF
ms.assetid: d79dabf5-a2ec-4e8d-a37a-67c4ba8a2b91
ms.openlocfilehash: 37433768c1bca3c013fb1e505d55bd7295f34933
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758021"
---
# <a name="types-migrated-from-wpf-to-systemxaml"></a>WPF에서 System.Xaml로 마이그레이션된 형식
.NET Framework 3.5 및.NET Framework 3.0에서 모두 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] 및 Windows Workflow Foundation XAML 언어 구현이 포함 되었습니다. WPF XAML 구현에 대해 확장성을 제공한 공용 형식은 대부분 WindowsBase, PresentationCore 및 PresentationFramework 어셈블리에 있었습니다. 마찬가지로,을 Windows Workflow Foundation XAML에 대 한 확장성을 제공한 공용 형식은 System.Workflow.ComponentModel 어셈블리에 존재 합니다. .NET Framework 4는 XAML 관련 형식 중 일부가 System.Xaml 어셈블리로 마이그레이션됩니다. XAML 언어 서비스는 일반적인.NET Framework 구현은 원래 특정 프레임 워크의 XAML 구현에서 정의 된 전체.NET Framework 4 XAML 언어 지원의 일부인 이제는 많은 XAML 확장성 시나리오를 수 있습니다. 이 항목에서는 마이그레이션되는 형식을 나열하고 마이그레이션과 관련된 문제를 논의합니다.  
  
<a name="assemblies_and_namespaces"></a>   
## <a name="assemblies-and-namespaces"></a>어셈블리 및 네임스페이스  
 .NET Framework 3.5 및.NET Framework 3.0에서는 WPF XAML을 지원 하기 위해 구현 하는 형식에 일반적으로 된를 <xref:System.Windows.Markup> 네임 스페이스입니다. 이러한 형식은 대부분 WindowsBase 어셈블리에 있었습니다.  
  
 .NET Framework 4의 새로운 <xref:System.Xaml> 네임 스페이스와 새로운 System.Xaml 어셈블리가 있습니다. 원래 WPF XAML에 대해 구현된 많은 형식이 이제 XAML 구현에 대한 확장성 지점 또는 서비스로 제공됩니다. 보다 일반적인 시나리오에 사용할 수 있도록 하는 작업의 일부로 원래의 WPF 어셈블리에서 System.Xaml 어셈블리로 형식이 전달됩니다. 이 다른 프레임 워크 (예: WPF 및 Windows Workflow Foundation)의 어셈블리를 포함 하지 않고 XAML 확장성 시나리오를 통해.  
  
 마이그레이션된 형식의 경우 대부분의 형식이 <xref:System.Windows.Markup> 네임스페이스에 계속 유지됩니다. 이는 부분적으로 기존 구현의 CLR 네임스페이스 매핑이 파일별로 분할되지 않도록 하기 위한 것이었습니다. 결과적으로 <xref:System.Windows.Markup> .NET Framework 4의 네임 스페이스에 System.Xaml 어셈블리) (에서 일반 XAML 언어 지원 형식과 노드가 혼합 되어 및 관련 된 WPF XAML 구현 (WindowsBase 및 기타 WPF 어셈블리)의 형식입니다. System.Xaml로 마이그레이션되었지만 이전에 WPF 어셈블리에 있었던 형식은 WPF 어셈블리의 버전 4에서 형식 전달을 지원합니다.  
  
### <a name="workflow-xaml-support-types"></a>워크플로 XAML 지원 형식  
 Windows Workflow Foundation XAML 지원 형식을 제공 하 고 대부분의 경우에 해당 하는 WPF와 동일한 짧은 이름을 가졌습니다. 다음은 Windows Workflow Foundation XAML 지원 형식의 목록입니다.  
  
- <xref:System.Workflow.ComponentModel.Serialization.ContentPropertyAttribute>  
  
- <xref:System.Workflow.ComponentModel.Serialization.RuntimeNamePropertyAttribute>  
  
- <xref:System.Workflow.ComponentModel.Serialization.XmlnsPrefixAttribute>  
  
 이러한 지원.NET Framework 4 용 Windows Workflow Foundation 어셈블리에 존재 하며 수 형식 특정 Windows Workflow Foundation 응용 프로그램에 사용할 그러나 응용 프로그램이 나 Windows Workflow Foundation을 사용 하지 않는 프레임 워크에서 참조 되지 해야 합니다.  
  
<a name="markupextension"></a>   
## <a name="markupextension"></a>MarkupExtension  
 .NET Framework 3.5 및.NET Framework 3.0에는 <xref:System.Windows.Markup.MarkupExtension> WPF가 WindowsBase 어셈블리에 대 한 클래스입니다. Windows Workflow Foundation에 대 한 병렬 클래스 <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension>은 System.Workflow.ComponentModel 어셈블리에 있었습니다. .NET Framework 4에서는 <xref:System.Windows.Markup.MarkupExtension> 클래스 System.Xaml 어셈블리로 마이그레이션. .NET Framework 4에서는 <xref:System.Windows.Markup.MarkupExtension> 특정 프레임 워크에서 빌드된에 뿐 아니라.NET Framework XAML 서비스를 사용 하는 모든 XAML 확장성 시나리오를 위한 것입니다. 가능한 경우 특정 프레임워크 또는 프레임워크의 사용자 코드도 XAML 확장에 대한 <xref:System.Windows.Markup.MarkupExtension> 클래스에서 빌드되어야 합니다.  
  
<a name="markupextension_supporting_service_classes"></a>   
## <a name="markupextension-supporting-service-classes"></a>MarkupExtension 지원 서비스 클래스  
 .NET framework 3.5 및 WPF에 대 한.NET Framework 3.0을 사용할 수 있었던 여러 서비스를 제공 <xref:System.Windows.Markup.MarkupExtension> 구현자 및 <xref:System.ComponentModel.TypeConverter> XAML에서 형식/속성 사용을 지원 하기 위해 구현 합니다. 이러한 서비스는 다음과 같습니다.  
  
- <xref:System.Windows.Markup.IProvideValueTarget>  
  
- <xref:System.Windows.Markup.IUriContext>  
  
- <xref:System.Windows.Markup.IXamlTypeResolver>  
  
> [!NOTE]
>  태그 확장과 관련 된.NET Framework 3.5에서 다른 서비스는 <xref:System.Windows.Markup.IReceiveMarkupExtension> 인터페이스입니다. <xref:System.Windows.Markup.IReceiveMarkupExtension> 이 마이그레이션되지 않았으며 표시 되어 `[Obsolete]` .NET Framework 4에 대 한 합니다. 이전에 <xref:System.Windows.Markup.IReceiveMarkupExtension> 을 사용한 시나리오에서는 대신 <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute> 특성 콜백을 사용해야 합니다. <xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute> 도 `[Obsolete]`로 표시됩니다.  
  
<a name="xaml_language_features"></a>   
## <a name="xaml-language-features"></a>XAML 언어 기능  
 WPF용 여러 XAML 언어 기능과 구성 요소는 이전에 PresentationFramework 어셈블리에 있었습니다. 이러한 항목은 XAML 태그로 태그 확장 사용을 노출하는 <xref:System.Windows.Markup.MarkupExtension> 서브클래스로 구현되었습니다. .NET Framework 4에서는 이러한 컴퓨터 WPF 어셈블리를 포함 하지 않는 프로젝트가 이러한 XAML 언어 수준 기능을 사용할 수 있도록 System.Xaml 어셈블리에 존재 합니다. WPF는.NET Framework 4 응용 프로그램에 대 한 이러한 동일한 구현을 사용합니다. 이 항목에 나열된 다른 경우와 마찬가지로, 지원 형식은 이전 참조가 손상되지 않도록 계속 <xref:System.Windows.Markup> 네임스페이스에 있습니다.  
  
 다음 표에는 System.Xaml에서 정의되는 XAML 기능 지원 클래스 목록이 포함되어 있습니다.  
  
|XAML 언어 기능|사용량|  
|---------------------------|-----------|  
|<xref:System.Windows.Markup.ArrayExtension>|`<x:Array ...>`|  
|<xref:System.Windows.Markup.NullExtension>|`{x:Null}`|  
|<xref:System.Windows.Markup.StaticExtension>|`{x:Static ...}`|  
|<xref:System.Windows.Markup.TypeExtension>|`{x:Type ...}`|  
  
 System.Xaml에 특정 지원 클래스가 없을 수도 있지만 이제 XAML 언어의 언어 기능 처리를 위한 일반적인 논리가 System.Xaml과 구현된 XAML 판독기 및 XAML 작성기에 상주합니다. 예를 들어 `x:TypeArguments` 는 System.Xaml 구현의 XAML 판독기 및 XAML 작성기에서 처리되는 특성입니다. XAML 노드 스트림에 기록될 수 있고, 기본(CLR 기반) XAML 스키마 컨텍스트 처리가 있으며, XAML 형식 시스템 표현을 포함합니다. 결과적으로, 모든 XAML 언어 수준 기능에 대한 참조 설명서는 3.5 설명서 집합에서와 같이 [고급(Windows Presentation Foundation)](index.md) 의 하위 항목으로 WPF 설명서에 포함되는 대신 [XAML Services](../wpf/advanced/index.md) 의 하위 항목 및 .NET Framework 설명서 집합의 일반 영역입니다.  
  
<a name="valueserializer_and_supporting_classes"></a>   
## <a name="valueserializer-and-supporting-classes"></a>ValueSerializer 및 지원 클래스  
 <xref:System.Windows.Markup.ValueSerializer> 클래스는 특히 직렬화 시 출력에 여러 모드 또는 노드가 필요할 수 있는 XAML 직렬화 사례를 위해 문자열로의 형식 변환을 지원합니다. .NET Framework 3.5 및.NET Framework 3.0에는 <xref:System.Windows.Markup.ValueSerializer> WPF가 WindowsBase 어셈블리에 대 한 합니다. .NET Framework 4에서는 <xref:System.Windows.Markup.ValueSerializer> 클래스 system.xaml 및 WPF에서 빌드된 위한 뿐 아니라 모든 XAML 확장성 시나리오에 대 한 것입니다. <xref:System.Windows.Markup.IValueSerializerContext> (지원 서비스) 및 <xref:System.Windows.Markup.DateTimeValueSerializer> (특정 서브클래스)도 System.Xaml로 마이그레이션됩니다.  
  
<a name="xamlrelated_attributes"></a>   
## <a name="xaml-related-attributes"></a>XAML 관련 특성  
 WPF XAML은 XAML 동작에 대한 특징을 나타내기 위해 CLR 형식에 적용할 수 있는 여러 특성을 포함했습니다. 다음은.NET Framework 3.5 및.NET Framework 3.0에서 WPF 어셈블리에 존재 하는 특성의 목록입니다. 이러한 특성은.NET Framework 4에서 System.Xaml로 마이그레이션됩니다.  
  
- <xref:System.Windows.Markup.AmbientAttribute>  
  
- <xref:System.Windows.Markup.ContentPropertyAttribute>  
  
- <xref:System.Windows.Markup.ContentWrapperAttribute>  
  
- <xref:System.Windows.Markup.DependsOnAttribute>  
  
- <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>  
  
- <xref:System.Windows.Markup.NameScopePropertyAttribute>  
  
- <xref:System.Windows.Markup.RootNamespaceAttribute>  
  
- <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>  
  
- <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>  
  
- <xref:System.Windows.Markup.ValueSerializerAttribute>  
  
- <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>  
  
- <xref:System.Windows.Markup.XmlLangPropertyAttribute>  
  
- <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>  
  
- <xref:System.Windows.Markup.XmlnsDefinitionAttribute>  
  
- <xref:System.Windows.Markup.XmlnsPrefixAttribute>  
  
<a name="miscellaneous_classes"></a>   
## <a name="miscellaneous-classes"></a>기타 클래스  
 <xref:System.Windows.Markup.IComponentConnector> 인터페이스.NET Framework 3.5 및.NET Framework 3.0에서는 windowsbase에 있었지만 System.Xaml.NET Framework 4에 있습니다. <xref:System.Windows.Markup.IComponentConnector> 는 주로 도구 지원 및 XAML 태그 컴파일러에 사용됩니다.  
  
 <xref:System.Windows.Markup.INameScope> 인터페이스.NET Framework 3.5 및.NET Framework 3.0에서는 windowsbase에 있었지만 System.Xaml.NET Framework 4에 있습니다. <xref:System.Windows.Markup.INameScope> 는 XAML 네임스페이스에 대한 기본 작업을 정의합니다.  
  
<a name="xamlrelated_classes_with_shared_names_that_exist_in_wpf_and_systemxaml"></a>   
## <a name="xaml-related-classes-with-shared-names-that-exist-in-wpf-and-systemxaml"></a>WPF 및 System.Xaml에 있는 공유 이름의 XAML 관련 클래스  
 다음 클래스는 WPF 어셈블리와.NET Framework 4에서 System.Xaml 어셈블리에 존재합니다.  
  
 `XamlReader`  
  
 `XamlWriter`  
  
 `XamlParseException`  
  
 WPF 구현은 <xref:System.Windows.Markup> 네임스페이스 및 PresentationFramework 어셈블리에 있습니다. System.Xaml 구현은 <xref:System.Xaml> 네임스페이스에 있습니다. WPF 형식을 사용하거나 WPF 형식에서 파생하는 경우 일반적으로 System.Xaml 구현 대신 <xref:System.Windows.Markup.XamlReader> 및 <xref:System.Windows.Markup.XamlWriter> 의 WPF 구현을 사용해야 합니다. 자세한 내용은 <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> 및 <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>의 설명을 참조하세요.  
  
 WPF 어셈블리 및 System.Xaml에 대한 참조를 둘 다 포함하고 `include` 및 <xref:System.Windows.Markup> 네임스페이스에 모두 <xref:System.Xaml> 문을 사용하는 경우 형식을 명확하게 확인하기 위해 이러한 API에 대한 호출을 정규화해야 할 수도 있습니다.  
  
## <a name="see-also"></a>참고자료

- [XAML 서비스](index.md)
