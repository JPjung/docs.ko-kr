---
title: '성능 최적화: 2D 그래픽 및 이미징'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], performance
- drawing [WPF], optimizing performance
- imaging [WPF], optimizing performance
- shapes [WPF], optimizing performance
- 2-D graphics [WPF]
- images [WPF], optimizing performance
ms.assetid: e335601e-28c8-4d64-ba27-778fffd55f72
ms.openlocfilehash: 25803bd772832cd22e855f530d10a3f3639c180c
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348438"
---
# <a name="optimizing-performance-2d-graphics-and-imaging"></a>성능 최적화: 2D 그래픽 및 이미징
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]는 응용 프로그램 요구 사항에 맞게 최적화할 수 있는 다양한 범위의 2D 그래픽 및 이미징 기능을 제공합니다. 이 항목에서는 이러한 영역의 성능 최적화에 대한 정보를 제공합니다.  

<a name="Drawing_and_Shapes"></a>   
## <a name="drawing-and-shapes"></a>그리기 및 도형  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 모두 제공 <xref:System.Windows.Media.Drawing> 고 <xref:System.Windows.Shapes.Shape> 그래픽 그리기 콘텐츠를 나타내는 개체입니다. 그러나 <xref:System.Windows.Media.Drawing> 개체는 보다 간단한 구문이 <xref:System.Windows.Shapes.Shape> 개체 및 더 나은 성능 특성을 제공 합니다.  
  
 <xref:System.Windows.Shapes.Shape> 화면에 그래픽 도형을 그릴 수 있습니다. 파생 되므로 합니다 <xref:System.Windows.FrameworkElement> 클래스인 <xref:System.Windows.Shapes.Shape> 패널 및 대부분의 컨트롤 내에서 개체를 사용할 수 있습니다.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]는 그래픽 및 렌더링 서비스에 대한 여러 계층의 액세스를 제공합니다. 최상위 계층 <xref:System.Windows.Shapes.Shape> 개체는 쉽게 사용 하 여 레이아웃 및 이벤트 처리 등 여러 유용한 기능을 제공 합니다. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]에서는 바로 사용할 수 있는 여러 도형 개체를 제공합니다. 모든 도형 개체에서 상속 된 <xref:System.Windows.Shapes.Shape> 클래스입니다. 사용 가능한 도형 개체를 포함 <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>를 <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>를 <xref:System.Windows.Shapes.Polyline>, 및 <xref:System.Windows.Shapes.Rectangle>합니다.  
  
 <xref:System.Windows.Media.Drawing> 개체를 다른 한편으로에서 파생 되지 않은 <xref:System.Windows.FrameworkElement> 클래스 및 렌더링 도형, 이미지 및 텍스트에 대 한 간단한 구현을 제공 합니다.  
  
 네 가지가 <xref:System.Windows.Media.Drawing> 개체:  
  
- <xref:System.Windows.Media.GeometryDrawing> 도형을 그립니다.  
  
- <xref:System.Windows.Media.ImageDrawing> 이미지를 그립니다.  
  
- <xref:System.Windows.Media.GlyphRunDrawing> 텍스트를 그립니다.  
  
- <xref:System.Windows.Media.DrawingGroup> 다른 그리기를 그립니다. 다른 그리기를 단일 합성 그리기로 결합하려면 그리기 그룹을 사용합니다.  
  
 <xref:System.Windows.Media.GeometryDrawing> 개체는 기 하 도형 콘텐츠를 렌더링 하는 데 사용 됩니다. 합니다 <xref:System.Windows.Media.Geometry> 클래스와 같은에서 파생 되는 구체적인 클래스 <xref:System.Windows.Media.CombinedGeometry>를 <xref:System.Windows.Media.EllipseGeometry>, 및 <xref:System.Windows.Media.PathGeometry>, 2D 그래픽 렌더링을 위한 수단을 제공할 뿐만 아니라 적중 테스트 및 클리핑 지원을 제공 합니다. 기하 도형 개체를 사용하면 컨트롤 영역을 정의하거나 이미지에 적용할 클립 영역을 정의하는 등의 작업을 수행할 수 있습니다. 기하 도형 개체는 사각형 및 원과 같은 단순 영역 또는 둘 이상의 기하 도형 개체에서 만들어진 복합 영역이 될 수 있습니다. 더 복잡 한 기하학적 영역을 결합 하 여 만들 수 있습니다 <xref:System.Windows.Media.PathSegment>-개체와 같은 파생 <xref:System.Windows.Media.ArcSegment>를 <xref:System.Windows.Media.BezierSegment>, 및 <xref:System.Windows.Media.QuadraticBezierSegment>합니다.  
  
 화면에는 <xref:System.Windows.Media.Geometry> 클래스 및 <xref:System.Windows.Shapes.Shape> 클래스는 매우 비슷합니다. 둘 다 2D 그래픽을 렌더링에 사용 되 고 예를 들어에서 파생 되는 유사한 구체적인 클래스 둘 다 <xref:System.Windows.Media.EllipseGeometry> 고 <xref:System.Windows.Shapes.Ellipse>입니다. 그러나 두 클래스 집합 사이에는 중요한 차이점이 있습니다. <xref:System.Windows.Media.Geometry> 클래스의 기능 중 일부에 <xref:System.Windows.Shapes.Shape> 자신을 그리는 기능과 같은 클래스입니다. 기하 도형 개체를 그리려면 DrawingContext, Drawing 또는 Path(Path가 Shape라는 것에 주의)와 같은 또 다른 클래스를 사용하여 그리기 작업을 수행해야 합니다. 채우기, 스트로크 및 스트로크 두께와 같은 렌더링 속성이 기하 도형 개체를 그리는 클래스에 있는 반면, 도형 개체는 이러한 속성을 포함합니다. 이 차이를 보여 주는 한 가지 예로, 기하 도형 개체는 원과 같은 영역을 정의하지만, 도형 개체는 영역을 정의하고 영역 채우기 및 윤곽선 그리기 방법을 정의하며 레이아웃 시스템에 참여할 수 있습니다.  
  
 이후 <xref:System.Windows.Shapes.Shape> 개체에서 파생 된 <xref:System.Windows.FrameworkElement> 클래스를 사용 하는 응용 프로그램에서 메모리 사용량이 크게 증가할을 추가할 수 있습니다. 실제로 필요 하지 않은 경우는 <xref:System.Windows.FrameworkElement> 그래픽 콘텐츠에 대해 기능 보다 간단한을 사용해 <xref:System.Windows.Media.Drawing> 개체입니다.  
  
 에 대 한 자세한 <xref:System.Windows.Media.Drawing> 개체를 참조 하세요 [Drawing 개체 개요](../graphics-multimedia/drawing-objects-overview.md)합니다.  
  
<a name="StreamGeometry_Objects"></a>   
## <a name="streamgeometry-objects"></a>StreamGeometry 개체  
 합니다 <xref:System.Windows.Media.StreamGeometry> 개체가 경량 대체 <xref:System.Windows.Media.PathGeometry> 기 하 도형 만들기에 대 한 합니다. 사용 하 여는 <xref:System.Windows.Media.StreamGeometry> 복잡 한 기 하 도형을 설명 해야 합니다. <xref:System.Windows.Media.StreamGeometry> 대부분을 처리 하기 위해 최적화 됩니다 <xref:System.Windows.Media.PathGeometry> 개체와 많은 개별을 사용 하 여 비교할 때 더 잘 수행 <xref:System.Windows.Media.PathGeometry> 개체입니다.  
  
 다음 예제에서는 특성 구문을 사용 하 여 삼각형을 만드는 <xref:System.Windows.Media.StreamGeometry> 에서 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]합니다.  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 에 대 한 자세한 <xref:System.Windows.Media.StreamGeometry> 개체를 참조 하세요 [StreamGeometry를 사용 하 여 도형 만들기](../graphics-multimedia/how-to-create-a-shape-using-a-streamgeometry.md)합니다.  
  
<a name="DrawingVisual_Objects"></a>   
## <a name="drawingvisual-objects"></a>DrawingVisual 개체  
 <xref:System.Windows.Media.DrawingVisual> 개체는 경량 그리기 클래스 도형, 이미지 또는 텍스트를 렌더링 하는 데 사용 되는 합니다. 이 클래스는 성능을 향상시키는 레이아웃이나 이벤트 처리를 제공하지 않으므로 간단한 클래스로 간주됩니다. 이러한 이유 때문에 그리기는 배경 및 클립 아트에 적합합니다. 자세한 내용은 [DrawingVisual 개체 사용](../graphics-multimedia/using-drawingvisual-objects.md)을 참조하세요.  
  
<a name="Images"></a>   
## <a name="images"></a>이미지  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 이미징은 이전 버전의 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]보다 크게 향상된 이미징 기능을 제공합니다. 비트맵을 표시하거나 공용 컨트롤에 이미지를 사용하는 등의 이미징 기능은 원래 주로 Microsoft Windows GDI(그래픽 디바이스 인터페이스) 또는 Microsoft Windows GDI+ API(응용 프로그래밍 인터페이스)에 의해 처리되었습니다. 이러한 API는 기준 이미징 기능은 제공했지만 코덱 확장성 및 고품질 이미지 지원 등과 같은 기능이 없었습니다. WPF 이미징 API는 GDI 및 GDI+의 단점을 보완하고 애플리케이션 내에서 이미지를 표시 및 사용하기 위한 새로운 API 집합을 제공하도록 다시 디자인되었습니다.  
  
 이미지를 사용할 경우 더 나은 성능을 얻으려면 다음 권장 사항을 고려하세요.  
  
- 애플리케이션에서 썸네일 이미지를 표시해야 할 경우 크기를 줄인 버전의 이미지를 만듭니다. 기본적으로 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]에서는 이미지를 로드하여 전체 크기로 디코딩합니다. 썸네일 버전의 이미지만 필요한 경우 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]에서 이미지를 전체 크기로 디코딩한 다음 썸네일 크기로 배율을 조정하는 것은 불필요한 작업입니다. 이러한 불필요한 오버헤드를 방지하려면 이미지를 썸네일 크기로 디코딩하도록 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]에 요청하거나 썸네일 크기 이미지를 로드하도록 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]에 요청하면 됩니다.  
  
- 이미지를 항상 기본 크기가 아니라 원하는 크기로 디코딩합니다. 위에 언급한 것처럼 이미지를 기본 전체 크기가 아니라 원하는 크기로 디코딩하도록 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]에 요청합니다. 이렇게 하면 애플리케이션의 작업 집합이 줄어들 뿐만 아니라 실행 속도가 빨라집니다.  
  
- 가능한 경우 여러 이미지로 구성된 필름 스트립과 같은 단일 이미지로 이미지를 결합합니다.  
  
- 자세한 내용은 [이미징 개요](../graphics-multimedia/imaging-overview.md)를 참조하세요.  
  
### <a name="bitmapscalingmode"></a>BitmapScalingMode  
 비트맵의 배율에 애니메이션 효과를 주면 기본 고품질 이미지 샘플 다시 만들기 알고리즘에 시스템 리소스가 많이 사용되므로 프레임 속도가 떨어지고 애니메이션이 끊길 수 있습니다. 설정 하 여 합니다 <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A> 의 속성을 <xref:System.Windows.Media.RenderOptions> 개체를 <xref:System.Windows.Media.BitmapScalingMode.LowQuality> 비트맵 크기를 조정할 때 보다 부드러운 애니메이션을 만들 수 있습니다. <xref:System.Windows.Media.BitmapScalingMode.LowQuality> 모드 지시를 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 이미지를 처리할 때 품질 최적화 알고리즘에서 속도 최적화 알고리즘을 전환 하려면 렌더링 엔진입니다.  
  
 다음 예제에서는 설정 하는 방법의 <xref:System.Windows.Media.BitmapScalingMode> 이미지 개체에 대 한 합니다.  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet2)]
 [!code-vb[RenderOptions#RenderOptionsSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet2)]  
  
### <a name="cachinghint"></a>CachingHint  
 기본적으로 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 의 렌더링된 된 콘텐츠를 캐시 하지 않습니다 <xref:System.Windows.Media.TileBrush> 개체와 같은 <xref:System.Windows.Media.DrawingBrush> 고 <xref:System.Windows.Media.VisualBrush>입니다. 정적 시나리오에서 있는 내용을 아니고 사용을 <xref:System.Windows.Media.TileBrush> 에서 장면 변경, 합리적이 지 비디오 메모리를 절약 하기 때문입니다. 경우 수행 하지는 <xref:System.Windows.Media.TileBrush> 정적 콘텐츠를 사용 하 여 정적이 지 않은 방식으로 사용 됩니다-등의 경우 정적 <xref:System.Windows.Media.DrawingBrush> 또는 <xref:System.Windows.Media.VisualBrush> 회전 3D 개체 표면에 매핑된. 기본 동작 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 의 콘텐츠 전체를 다시 렌더링 하는 것은 <xref:System.Windows.Media.DrawingBrush> 또는 <xref:System.Windows.Media.VisualBrush> 모든 프레임에 대 한도 콘텐츠가 변경 되지 합니다.  
  
 설정 하 여 합니다 <xref:System.Windows.Media.RenderOptions.CachingHint%2A> 의 속성을 <xref:System.Windows.Media.RenderOptions> 개체를 <xref:System.Windows.Media.CachingHint.Cache> 타일된 브러시 개체의 캐시 된 버전을 사용 하 여 성능을 향상 시킬 수 있습니다.  
  
 <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A> 및 <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> 속성 값은 시기를 결정 하는 상대 크기 값을 <xref:System.Windows.Media.TileBrush> 확장의 변경으로 인해 개체를 다시 생성 해야 합니다. 설정 하 여 예를 들어, 합니다 <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> 속성을 2.0으로 캐시를 <xref:System.Windows.Media.TileBrush> 만 크기로 현재 캐시의 크기 두 배를 초과 하는 경우 다시 생성 해야 합니다.  
  
 다음 예제에 대 한 캐싱 힌트 옵션을 사용 하는 방법을 보여 줍니다는 <xref:System.Windows.Media.DrawingBrush>합니다.  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet3)]
 [!code-vb[RenderOptions#RenderOptionsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet3)]  
  
## <a name="see-also"></a>참고자료

- [WPF 응용 프로그램 성능 최적화](optimizing-wpf-application-performance.md)
- [애플리케이션 성능 계획](planning-for-application-performance.md)
- [하드웨어 이용](optimizing-performance-taking-advantage-of-hardware.md)
- [레이아웃 및 디자인](optimizing-performance-layout-and-design.md)
- [개체 동작](optimizing-performance-object-behavior.md)
- [애플리케이션 리소스](optimizing-performance-application-resources.md)
- [텍스트](optimizing-performance-text.md)
- [데이터 바인딩](optimizing-performance-data-binding.md)
- [기타 성능 권장 사항](optimizing-performance-other-recommendations.md)
- [애니메이션에 대한 유용한 정보](../graphics-multimedia/animation-tips-and-tricks.md)
