---
title: return 문 - C# 참조
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 3e89f2f854d1f66ca2d7bf1cfa5a507c267798f8
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422716"
---
# <a name="return-c-reference"></a>return(C# 참조)

`return` 문은 해당 문이 나타나는 메서드의 실행을 종료하고 제어를 호출 메서드로 반환합니다. 선택적 값을 반환할 수도 있습니다. 메서드가 `void` 형식인 경우 `return` 문을 생략할 수 있습니다.

 return 문이 `try` 블록 안에 있으면 `finally` 블록(있는 경우)은 제어가 호출 메서드로 반환되기 전에 실행됩니다.

## <a name="example"></a>예제

 다음 예제에서 `CalculateArea()` 메서드는 `area` 로컬 변수를 [double](double.md) 값으로 반환합니다.

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a>C# 언어 사양

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>참고 항목

- [C# 참조](../index.md)
- [C# 프로그래밍 가이드](../../programming-guide/index.md)
- [C# 키워드](index.md)
- [return 문](/cpp/cpp/return-statement-cpp)
