---
title: ':: 연산자 - C# 참조'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ::_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: c494e8dbb18f44ce5520b21800a21d3feb03da59
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025065"
---
# <a name="-operator-c-reference"></a>:: 연산자(C# 참조)

네임스페이스 별칭 한정자(`::`)는 식별자를 조회하는 데 사용됩니다. 다음 예제와 같이 항상 두 식별자 사이에 옵니다.

[!code-csharp[csRefOperators#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#27)]

`::` 연산자는 *using 별칭 지시문*과 함께 사용할 수도 있습니다.

```csharp
// using Col=System.Collections.Generic;
var numbers = new Col::List<int> { 1, 2, 3 };
```

## <a name="remarks"></a>설명

네임스페이스 별칭 한정자는 `global`일 수 있습니다. 별칭이 지정된 네임스페이스가 아니라 전역 네임스페이스에서 조회를 호출합니다.

## <a name="for-more-information"></a>추가 정보

`::` 연산자를 사용하는 방법의 예는 다음 섹션을 참조하세요.

- [방법: 전역 네임스페이스 별칭 사용](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)

## <a name="c-language-specification"></a>C# 언어 사양

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>참고 항목

- [C# 참조](../index.md)
- [C# 연산자](index.md)
- [. 연산자](member-access-operators.md#member-access-operator-)
- [extern alias](../keywords/extern-alias.md)
