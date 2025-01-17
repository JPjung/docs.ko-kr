---
title: C++ 템플릿과 C# 제네릭의 차이점 - C# 프로그래밍 가이드
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], vs. C++ templates
ms.assetid: 1da6beeb-d4a4-4da0-87b7-0cfbe04920b7
ms.openlocfilehash: 8151d426d1f0d3da5a5ce5fe795635348efd9696
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423528"
---
# <a name="differences-between-c-templates-and-c-generics-c-programming-guide"></a>C++ 템플릿과 C# 제네릭의 차이점(C# 프로그래밍 가이드)
C# 제네릭 및 C++ 템플릿은 둘 다 매개 변수가 있는 형식을 지원하는 언어 기능입니다. 그러나 둘 사이에는 많은 차이가 있습니다. 구문 수준에서 C# 제네릭은 매개 변수가 있는 형식에 대한 더 간단한 접근 방식으로, C++ 템플릿의 복잡함이 없습니다. 또한 C#은 C++ 템플릿에서 제공하는 기능 중 일부를 제공하지 않습니다. 구현 수준에서 주요 차이점은 런타임에 C# 제네릭 형식 대체가 수행되어 인스턴스화된 개체에 대해 제네릭 형식 정보가 유지된다는 점입니다. 자세한 내용은 [런타임의 제네릭](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)을 참조하세요.  
  
 다음은 C# 제네릭 및 C++ 템플릿 사이의 주요 차이점입니다.  
  
- C# 제네릭은 C++ 템플릿과 동일한 수준의 유연성을 제공하지 않습니다. 예를 들어 C# 제네릭 클래스에서 산술 연산자는 호출할 수 없지만 사용자 정의 연산자는 호출할 수 있습니다.  
  
- C#에서는 `template C<int i> {}` 같은 비형식 템플릿 매개 변수를 허용하지 않습니다.  
  
- C#은 명시적 특수화 즉, 특정 형식에 대한 템플릿의 사용자 지정 구현을 지원하지 않습니다.  
  
- C#은 부분 특수화 즉, 형식 인수의 하위 집합에 대한 사용자 지정 구현을 지원하지 않습니다.  
  
- C#에서는 형식 매개 변수를 제네릭 형식에 대한 기본 클래스로 사용할 수 없습니다.  
  
- C#에서는 형식 매개 변수가 기본 형식을 사용할 수 없습니다.  
  
- C#에서 제네릭 형식 매개 변수 자체는 제네릭이 될 수 없지만 생성된 형식은 제네릭으로 사용할 수 있습니다. C++에서는 템플릿 매개 변수를 허용합니다.  
  
- C++에서는 템플릿의 일부 형식 매개 변수에 적합하지 않아 형식 매개 변수로 사용되는 특정 형식을 확인하는 코드를 허용합니다. C#에서는 제약 조건을 충족하는 모든 형식에서 작동하는 방식으로 작성할 코드가 클래스에 필요합니다. 예를 들어 C++에서는 산술 연산자 `+` 및 `-`를 사용하는 함수를 형식 매개 변수의 개체에서 작성하여 이러한 연산자를 지원하지 않는 형식으로 템플릿을 인스턴스화할 때 오류를 생성할 수 있습니다. C#에서는 이를 허용하지 않습니다. 허용되는 유일한 언어 구문은 제약 조건에서 추론할 수 있는 구문입니다.  
  
## <a name="see-also"></a>참고 항목

- [C# 프로그래밍 가이드](../../../csharp/programming-guide/index.md)
- [제네릭 소개](../../../csharp/programming-guide/generics/index.md)
- [템플릿](/cpp/cpp/templates-cpp)
