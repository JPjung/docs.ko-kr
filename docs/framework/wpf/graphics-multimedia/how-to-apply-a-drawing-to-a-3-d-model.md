---
title: '방법: 3차원 모델에 그리기 적용'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 8ac24fdf8d7e407e10764c17fcc12121aa5f51d7
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662806"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a>방법: 3차원 모델에 그리기 적용
사용 하는 방법을 보여 주는이 예제는 <xref:System.Windows.Media.DrawingBrush> 으로 <xref:System.Windows.Media.Media3D.Material> 3d 모델에 적용 합니다.  
  
 다음 코드는 정의 <xref:System.Windows.Media.DrawingGroup> 의 내용으로는 <xref:System.Windows.Media.DrawingBrush>합니다.  <xref:System.Windows.Media.DrawingBrush> 으로 설정 됩니다는 <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> 의 속성은 <xref:System.Windows.Media.Media3D.DiffuseMaterial> 3 차원 평면에 적용 합니다.  
  
 **참고:** 코드를 단순화 하 고 다시 사용할 수 있는 리소스로 복잡 한 개체 및 아래의 그림과 같은 값을 정의 하는 것이 좋습니다. 참조 [XAML 리소스](../advanced/xaml-resources.md) 자세한 내용은 합니다.  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]  
  
## <a name="example"></a>예제  
 다음 코드에는 전체 샘플을 보여 줍니다.  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]  
  
## <a name="see-also"></a>참고자료

- [XAML 리소스](../advanced/xaml-resources.md)
- [3차원 장면 만들기](how-to-create-a-3-d-scene.md)
- [Drawing 개체 개요](drawing-objects-overview.md)
- [3차원 그래픽 개요](3-d-graphics-overview.md)
