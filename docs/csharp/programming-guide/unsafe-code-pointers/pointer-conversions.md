---
title: 포인터 변환 - C# 프로그래밍 가이드
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: 3cef2f2d2af2d285504daea14aa57c55b9e9a21b
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833468"
---
# <a name="pointer-conversions-c-programming-guide"></a>포인터 변환(C# 프로그래밍 가이드)
다음 표에서는 미리 정의된 암시적 포인터 변환을 보여 줍니다. 암시적 변환은 메서드 호출, 할당 문을 비롯한 대부분의 경우에서 발생할 수 있습니다.  
  
## <a name="implicit-pointer-conversions"></a>암시적 포인터 변환  
  
|시작|대상|  
|----------|--------|  
|임의의 포인터 형식|void*|  
|null|임의의 포인터 형식|  
  
 명시적 포인터 변환은 캐스트 식을 통해 암시적 변환이 없는 변환을 수행하는 데 사용됩니다. 다음 표에는 이러한 변환이 나와 있습니다.  
  
## <a name="explicit-pointer-conversions"></a>명시적 포인터 변환  
  
|시작|대상|  
|----------|--------|  
|임의의 포인터 형식|다른 포인터 형식|  
|sbyte, byte, short, ushort, int, uint, long 또는 ulong|임의의 포인터 형식|  
|임의의 포인터 형식|sbyte, byte, short, ushort, int, uint, long 또는 ulong|  
  
## <a name="example"></a>예  
 다음 예제에서 `int`에 대한 포인터는 `byte`에 대한 포인터로 변환됩니다. 포인터는 변수의 최하위 주소 지정 바이트를 가리킵니다. `int` 크기(4바이트)까지 결과를 연속적으로 증가할 경우 변수의 나머지 바이트를 표시할 수 있습니다.  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a>참고 항목

- [C# 프로그래밍 가이드](../../../csharp/programming-guide/index.md)
- [포인터 형식](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [유형](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [fixed 문](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/operators/stackalloc.md)
