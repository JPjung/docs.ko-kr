---
title: 연산자 오버로드 - C# 참조
description: C# 연산자를 오버로드하는 방법과 오버로드가 가능한 C# 연산자에 대해 알아봅니다.
ms.date: 07/05/2019
f1_keywords:
- operator_CSharpKeyword
helpviewer_keywords:
- operator keyword [C#]
- operator overloading [C#]
ms.openlocfilehash: f9085f2a550dfacc670857a70f5b22de9e028107
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610596"
---
# <a name="operator-overloading-c-reference"></a>연산자 오버로드(C# 참조)

사용자 정의 형식은 미리 정의된 C# 연산자를 오버로드할 수 있습니다. 즉, 하나 또는 두 피연산자가 해당 형식일 때 형식은 작업의 사용자 정의 구현을 제공할 수 있습니다. [오버로드할 수 있는 연산자](#overloadable-operators) 섹션에는 오버로드할 수 있는 C# 연산자가 나와 있습니다.

`operator` 키워드를 사용하여 연산자를 선언합니다. 연산자 선언은 다음 규칙을 충족해야 합니다.

- `public` 및 `static` 한정자를 모두 포함합니다.
- 단항 연산자는 하나의 매개 변수를 사용합니다. 이항 연산자는 두 개의 매개 변수를 사용합니다. 각각의 경우 하나 이상의 매개 변수가 `T` 또는 `T?` 유형을 가져야 하며, 여기서 `T`는 연산자 선언이 포함된 유형입니다.

다음 예제에서는 유리수를 나타내는 간단한 구조를 정의합니다. 구조체가 [산술 연산자](arithmetic-operators.md) 중 일부를 오버로드합니다.

[!code-csharp[fraction example](~/samples/csharp/language-reference/operators/OperatorOverloading.cs)]

## <a name="overloadable-operators"></a>오버로드할 수 있는 연산자

다음 표는 C# 연산자의 오버로드 가능성에 대한 정보를 제공합니다.

| 연산자 | 오버로드 가능성 |
| --------- | --------------- |
|[+](arithmetic-operators.md#unary-plus-and-minus-operators), [-](arithmetic-operators.md#unary-plus-and-minus-operators), [!](boolean-logical-operators.md#logical-negation-operator-), [~](bitwise-and-shift-operators.md#bitwise-complement-operator-), [++](arithmetic-operators.md#increment-operator-), [--](arithmetic-operators.md#decrement-operator---), [true](true-false-operators.md), [false](true-false-operators.md)|이러한 단항 연산자는 오버로드할 수 있습니다.|
|[+](addition-operator.md), [-](subtraction-operator.md), [\*](arithmetic-operators.md#multiplication-operator-), [/](arithmetic-operators.md#division-operator-), [%](arithmetic-operators.md#remainder-operator-), [&](boolean-logical-operators.md#logical-and-operator-), [&#124;](boolean-logical-operators.md#logical-or-operator-), [^](boolean-logical-operators.md#logical-exclusive-or-operator-), [\<\<](bitwise-and-shift-operators.md#left-shift-operator-), [>>](bitwise-and-shift-operators.md#right-shift-operator-), [==](equality-operators.md#equality-operator-), [!=](equality-operators.md#inequality-operator-), [\<](comparison-operators.md#less-than-operator-), [>](comparison-operators.md#greater-than-operator-), [\<=](comparison-operators.md#less-than-or-equal-operator-), [>=](comparison-operators.md#greater-than-or-equal-operator-)|이러한 이항 연산자는 오버로드할 수 있습니다. 특정 연산자는 쌍으로 오버로드되어야 합니다. 자세한 내용은 이 표 다음에 나오는 참고 사항을 참조하세요.|
|[&&](boolean-logical-operators.md#conditional-logical-and-operator-), [&#124;&#124;](boolean-logical-operators.md#conditional-logical-or-operator-)|조건부 논리 연산자는 오버로드할 수 없습니다. 그러나 오버로드된 [`true` 및 `false` 연산자](true-false-operators.md)가 있는 형식도 특정 방식으로 `&` 또는 <code>&#124;</code> 연산자를 오버로드하는 경우, `&&` 또는 <code>&#124;&#124;</code> 연산자는 각각 해당 유형의 피연산자에 대해 평가될 수 있습니다. 자세한 내용은 [C# 언어 사양](~/_csharplang/spec/introduction.md)의 [사용자 정의 조건부 논리 연산자](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) 섹션을 참조하세요.|
|[&#91;&#93;](member-access-operators.md#indexer-operator-)|요소 액세스는 오버로드 가능한 연산자로 간주되지 않지만 [인덱서](../../programming-guide/indexers/index.md)를 정의할 수 있습니다.|
|[(T)x](type-testing-and-conversion-operators.md#cast-operator-)|캐스트 연산자는 오버로드할 수 없지만 새 변환 연산자를 정의할 수 있습니다([explicit](../keywords/explicit.md) 및 [implicit](../keywords/implicit.md) 참조).|
|[+=](arithmetic-operators.md#compound-assignment), [-=](arithmetic-operators.md#compound-assignment), [\*=](arithmetic-operators.md#compound-assignment), [/=](arithmetic-operators.md#compound-assignment), [%=](arithmetic-operators.md#compound-assignment), [&=](boolean-logical-operators.md#compound-assignment), [&#124;=](boolean-logical-operators.md#compound-assignment), [^=](boolean-logical-operators.md#compound-assignment), [\<\<=](bitwise-and-shift-operators.md#compound-assignment), [>>=](bitwise-and-shift-operators.md#compound-assignment)|복합 할당 연산자를 명시적으로 오버로드할 수 없습니다. 그러나 이항 연산자가 오버로드되면 해당 복합 할당 연산자(있는 경우)도 암시적으로 오버로드됩니다. 예를 들어 `+=`는 오버로드될 수 있는 `+`를 사용하여 계산됩니다.|
|[=](assignment-operator.md), [.](member-access-operators.md#member-access-operator-), [?:](conditional-operator.md), [??](null-coalescing-operator.md), [->](pointer-related-operators.md#pointer-member-access-operator--), [=>](lambda-operator.md), [f(x)](member-access-operators.md#invocation-operator-), [as](type-testing-and-conversion-operators.md#as-operator), [checked](../keywords/checked.md), [unchecked](../keywords/unchecked.md), [default](../../programming-guide/statements-expressions-operators/default-value-expressions.md), [delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md), [is](type-testing-and-conversion-operators.md#is-operator), [nameof](../keywords/nameof.md), [new](new-operator.md), [sizeof](../keywords/sizeof.md), [typeof](type-testing-and-conversion-operators.md#typeof-operator)|이러한 연산자는 오버로드할 수 없습니다.|

> [!NOTE]
> 비교 연산자는 쌍으로 오버로드되어야 합니다. 즉, 쌍 중 하나의 연산자가 오버로드되면 다른 연산자도 오버로드되어야 합니다. 이러한 쌍은 다음과 같습니다.
>
> - `==` 및 `!=` 연산자
> - `<` 및 `>` 연산자
> - `<=` 및 `>=` 연산자

## <a name="c-language-specification"></a>C# 언어 사양

자세한 내용은 [C# 언어 사양](~/_csharplang/spec/introduction.md)의 다음 섹션을 참조하세요.

- [연산자 오버로드](~/_csharplang/spec/expressions.md#operator-overloading)
- [연산자](~/_csharplang/spec/classes.md#operators)

## <a name="see-also"></a>참고 항목

- [C# 참조](../index.md)
- [C# 연산자](index.md)
- [Why are overloaded operators always static in C#?](https://blogs.msdn.microsoft.com/ericlippert/2007/05/14/why-are-overloaded-operators-always-static-in-c/)(오버로드된 연산자가 C#에서 항상 정적인 이유)
