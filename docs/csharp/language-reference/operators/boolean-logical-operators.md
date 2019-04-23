---
title: 부울 논리 연산자 - C# 참조
description: 부울 피연산자를 사용하여 논리 부정, 결합(AND) 및 포괄적/배타적 분리(OR) 작업을 수행하는 C# 연산자에 대해 알아봅니다.
ms.date: 04/08/2019
author: pkulikov
f1_keywords:
- '!_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
- '&&_CSharpKeyword'
- '||_CSharpKeyword'
helpviewer_keywords:
- logical operators [C#]
- short-circuiting operators [C#]
- logical negation operator [C#]
- NOT operator [C#]
- '! operator [C#]'
- AND operator [C#]
- ampersand operator [C#]
- conjunction operator [C#]
- '& operator [C#]'
- exclusive OR operator [C#]
- XOR operator [C#]
- ^ operator [C#]
- OR operator [C#]
- disjunction operator [C#]
- '| operator [C#]'
- conditional AND operator [C#]
- short-circuiting AND operator [C#]
- '&& operator [C#]'
- conditional OR operator [C#]
- short-circuiting OR operator [C#]
- '|| operator [C#]'
ms.openlocfilehash: de621b26334bbc9679ba7e48a9d5a0cbaec67eab
ms.sourcegitcommit: d21bee9dbd32b9540ad30f9d0e2e874227040be3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59427320"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="dd0ef-103">부울 논리 연산자(C# 참조)</span><span class="sxs-lookup"><span data-stu-id="dd0ef-103">Boolean logical operators (C# Reference)</span></span>

<span data-ttu-id="dd0ef-104">다음 연산자는 [부울](../keywords/bool.md) 피연산자를 사용하여 논리 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-104">The following operators perform logical operations with the [bool](../keywords/bool.md) operands:</span></span>

- <span data-ttu-id="dd0ef-105">단항 [`!`(논리 부정)](#logical-negation-operator-) 연산자.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="dd0ef-106">이진 [`&`(논리 AND)](#logical-and-operator-), [`|`(논리 OR)](#logical-or-operator-) 및 [`^`(논리 배타적 OR)](#logical-exclusive-or-operator-) 연산자.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="dd0ef-107">해당 연산자는 항상 두 피연산자를 모두 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="dd0ef-108">이진 [`&&`(조건부 논리 AND)](#conditional-logical-and-operator-) 및 [`||`(조건부 논리 OR)](#conditional-logical-or-operator-) 연산자.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="dd0ef-109">해당 연산자는 필요한 경우에만 두 번째 피연산자를 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-109">Those operators evaluate the second operand only if it's necessary.</span></span>

<span data-ttu-id="dd0ef-110">[정수](../keywords/integral-types-table.md) 형식 피연산자의 경우 `&`, `|` 및 `^` 연산자는 비트 논리 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-110">For the operands of [integral](../keywords/integral-types-table.md) types, the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="dd0ef-111">논리 부정 연산자 !</span><span class="sxs-lookup"><span data-stu-id="dd0ef-111">Logical negation operator !</span></span>

<span data-ttu-id="dd0ef-112">`!` 연산자는 해당 피연산자의 논리 부정을 컴퓨팅합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-112">The `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="dd0ef-113">즉, 피연산자가 `false`로 평가되는 경우 `true`를 생성하고, 피연산자가 `true`로 평가되는 경우 `false`를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-113">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Negation)]

## <a name="logical-and-operator-amp"></a><span data-ttu-id="dd0ef-114">논리 AND 연산자 &amp;</span><span class="sxs-lookup"><span data-stu-id="dd0ef-114">Logical AND operator &amp;</span></span>

<span data-ttu-id="dd0ef-115">`&` 연산자는 해당 피연산자의 논리 AND를 컴퓨팅합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-115">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="dd0ef-116">`x` 및 `y`가 모두 `true`로 평가되면 `x & y`의 결과는 `true`입니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-116">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="dd0ef-117">그렇지 않으면 결과는 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-117">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="dd0ef-118">첫 번째 피연산자가 `false`로 평가되더라도 `&` 연산자는 두 피연산자를 평가하여 두 번째 피연산자의 값에 관계없이 `false`이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-118">The `&` operator evaluates both operands even if the first operand evaluates to `false`, so that the result must be `false` regardless of the value of the second operand.</span></span>

<span data-ttu-id="dd0ef-119">다음 예제에서 `&` 연산자의 두 번째 피연산자는 첫 번째 피연산자의 값과 관계없이 수행되는 메서드 호출입니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-119">In the following example, the second operand of the `&` operator is a method call, which is performed regardless of the value of the first operand:</span></span>

[!code-csharp-interactive[logical AND](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#And)]

<span data-ttu-id="dd0ef-120">[조건부 논리 AND 연산자](#conditional-logical-and-operator-) `&&`도 해당 피연산자의 논리 AND를 컴퓨팅하지만, 첫 번째 피연산자가 `false`로 평가되는 경우에는 두 번째 피연산자를 평가하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-120">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the second operand if the first operand evaluates to `false`.</span></span>

<span data-ttu-id="dd0ef-121">정수 형식 피연산자의 경우 `&` 연산자는 해당 피연산자의 [비트 논리 AND](and-operator.md#integer-logical-bitwise-and-operator)를 컴퓨팅합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-121">For the operands of integral types, the `&` operator computes [bitwise logical AND](and-operator.md#integer-logical-bitwise-and-operator) of its operands.</span></span> <span data-ttu-id="dd0ef-122">단항 `&` 연산자는 [address-of 연산자](and-operator.md#unary-address-of-operator)입니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-122">The unary `&` operator is the [address-of operator](and-operator.md#unary-address-of-operator).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="dd0ef-123">논리 배타적 OR 연산자 ^</span><span class="sxs-lookup"><span data-stu-id="dd0ef-123">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="dd0ef-124">`^` 연산자는 해당 피연산자의 논리 XOR이라고도 하는 논리 배타적 OR을 컴퓨팅합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-124">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="dd0ef-125">`x`가 `true`로 평가되고 `y`가 `false`로 평가되거나, `x`가 `false`로 평가되고 `y`가 `true`로 평가되는 경우 `x ^ y`의 결과는 `true`입니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-125">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="dd0ef-126">그렇지 않으면 결과는 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-126">Otherwise, the result is `false`.</span></span> <span data-ttu-id="dd0ef-127">즉, `bool` 피연산자의 경우 `^` 연산자는 [같지 않음 연산자](equality-operators.md#inequality-operator-) `!=`와 같은 결과를 컴퓨팅합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-127">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Xor)]

<span data-ttu-id="dd0ef-128">정수 형식 피연산자의 경우 `^` 연산자는 해당 피연산자의 [비트 논리 배타적 OR](xor-operator.md)을 컴퓨팅합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-128">For the operands of integral types, the `^` operator computes [bitwise logical exclusive OR](xor-operator.md) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="dd0ef-129">논리 OR 연산자 |</span><span class="sxs-lookup"><span data-stu-id="dd0ef-129">Logical OR operator |</span></span>

<span data-ttu-id="dd0ef-130">`|` 연산자는 해당 피연산자의 논리 OR을 컴퓨팅합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-130">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="dd0ef-131">`x` 또는 `y`가 `true`로 평가되면 `x | y`의 결과는 `true`입니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-131">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="dd0ef-132">그렇지 않으면 결과는 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-132">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="dd0ef-133">첫 번째 피연산자가 `true`로 평가되더라도 `|` 연산자는 두 피연산자를 평가하여 두 번째 피연산자의 값에 관계없이 `true`이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-133">The `|` operator evaluates both operands even if the first operand evaluates to `true`, so that the result must be `true` regardless of the value of the second operand.</span></span>

<span data-ttu-id="dd0ef-134">다음 예제에서 `|` 연산자의 두 번째 피연산자는 첫 번째 피연산자의 값과 관계없이 수행되는 메서드 호출입니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-134">In the following example, the second operand of the `|` operator is a method call, which is performed regardless of the value of the first operand:</span></span>

[!code-csharp-interactive[logical OR](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Or)]

<span data-ttu-id="dd0ef-135">[조건부 논리 OR 연산자](#conditional-logical-or-operator-) `||`도 해당 피연산자의 논리 OR을 컴퓨팅하지만, 첫 번째 피연산자가 `true`로 평가되는 경우에는 두 번째 피연산자를 평가하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-135">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the second operand if the first operand evaluates to `true`.</span></span>

<span data-ttu-id="dd0ef-136">정수 형식 피연산자의 경우 `|` 연산자는 해당 피연산자의 [비트 논리 OR](or-operator.md)을 컴퓨팅합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-136">For the operands of integral types, the `|` operator computes [bitwise logical OR](or-operator.md) of its operands.</span></span>

## <a name="conditional-logical-and-operator-ampamp"></a><span data-ttu-id="dd0ef-137">조건부 논리 AND 연산자 &amp;&amp;</span><span class="sxs-lookup"><span data-stu-id="dd0ef-137">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="dd0ef-138">“단락(short-circuiting)” 논리 AND 연산자로도 알려진 조건부 논리 AND 연산자 `&&`는 해당 피연산자의 논리 AND를 컴퓨팅합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-138">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="dd0ef-139">`x` 및 `y`가 모두 `true`로 평가되면 `x && y`의 결과는 `true`입니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-139">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="dd0ef-140">그렇지 않으면 결과는 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-140">Otherwise, the result is `false`.</span></span> <span data-ttu-id="dd0ef-141">첫 번째 피연산자가 `false`로 평가되면 두 번째 피연산자는 평가되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-141">If the first operand evaluates to `false`, the second operand is not evaluated.</span></span>

<span data-ttu-id="dd0ef-142">다음 예제에서 `&&` 연산자의 두 번째 피연산자는 첫 번째 피연산자가 `false`로 평가되는 경우 수행되지 않는 메서드 호출입니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-142">In the following example, the second operand of the `&&` operator is a method call, which isn't performed if the first operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="dd0ef-143">[논리 AND 연산자](#logical-and-operator-) `&`도 해당 피연산자의 논리 AND를 컴퓨팅하지만 항상 두 피연산자를 모두 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-143">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="dd0ef-144">조건부 논리 OR 연산자 ||</span><span class="sxs-lookup"><span data-stu-id="dd0ef-144">Conditional logical OR operator ||</span></span>

<span data-ttu-id="dd0ef-145">“단락(short-circuiting)” 논리 OR 연산자로도 알려진 조건부 논리 OR 연산자 `||`는 해당 피연산자의 논리 OR을 컴퓨팅합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-145">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="dd0ef-146">`x` 또는 `y`가 `true`로 평가되면 `x || y`의 결과는 `true`입니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-146">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="dd0ef-147">그렇지 않으면 결과는 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-147">Otherwise, the result is `false`.</span></span> <span data-ttu-id="dd0ef-148">첫 번째 피연산자가 `true`로 평가되면 두 번째 피연산자는 평가되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-148">If the first operand evaluates to `true`, the second operand is not evaluated.</span></span>

<span data-ttu-id="dd0ef-149">다음 예제에서 `||` 연산자의 두 번째 피연산자는 첫 번째 피연산자가 `true`로 평가되는 경우 수행되지 않는 메서드 호출입니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-149">In the following example, the second operand of the `||` operator is a method call, which isn't performed if the first operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="dd0ef-150">[논리 OR 연산자](#logical-or-operator-) `|`도 해당 피연산자의 논리 OR을 컴퓨팅하지만 항상 두 피연산자를 모두 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-150">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="dd0ef-151">Nullable 부울 논리 연산자</span><span class="sxs-lookup"><span data-stu-id="dd0ef-151">Nullable Boolean logical operators</span></span>

<span data-ttu-id="dd0ef-152">`bool?` 피연산자의 경우 `&` 및 `|` 연산자는 값이 세 개인 논리를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-152">For the `bool?` operands, the `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="dd0ef-153">이러한 연산자의 의미 체계는 다음 표에서 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-153">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="dd0ef-154">x</span><span class="sxs-lookup"><span data-stu-id="dd0ef-154">x</span></span>|<span data-ttu-id="dd0ef-155">y</span><span class="sxs-lookup"><span data-stu-id="dd0ef-155">y</span></span>|<span data-ttu-id="dd0ef-156">x&y</span><span class="sxs-lookup"><span data-stu-id="dd0ef-156">x&y</span></span>|<span data-ttu-id="dd0ef-157">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="dd0ef-157">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="dd0ef-158">true</span><span class="sxs-lookup"><span data-stu-id="dd0ef-158">true</span></span>|<span data-ttu-id="dd0ef-159">true</span><span class="sxs-lookup"><span data-stu-id="dd0ef-159">true</span></span>|<span data-ttu-id="dd0ef-160">true</span><span class="sxs-lookup"><span data-stu-id="dd0ef-160">true</span></span>|<span data-ttu-id="dd0ef-161">true</span><span class="sxs-lookup"><span data-stu-id="dd0ef-161">true</span></span>|  
|<span data-ttu-id="dd0ef-162">true</span><span class="sxs-lookup"><span data-stu-id="dd0ef-162">true</span></span>|<span data-ttu-id="dd0ef-163">False</span><span class="sxs-lookup"><span data-stu-id="dd0ef-163">false</span></span>|<span data-ttu-id="dd0ef-164">false</span><span class="sxs-lookup"><span data-stu-id="dd0ef-164">false</span></span>|<span data-ttu-id="dd0ef-165">true</span><span class="sxs-lookup"><span data-stu-id="dd0ef-165">true</span></span>|  
|<span data-ttu-id="dd0ef-166">true</span><span class="sxs-lookup"><span data-stu-id="dd0ef-166">true</span></span>|<span data-ttu-id="dd0ef-167">null</span><span class="sxs-lookup"><span data-stu-id="dd0ef-167">null</span></span>|<span data-ttu-id="dd0ef-168">null</span><span class="sxs-lookup"><span data-stu-id="dd0ef-168">null</span></span>|<span data-ttu-id="dd0ef-169">true</span><span class="sxs-lookup"><span data-stu-id="dd0ef-169">true</span></span>|  
|<span data-ttu-id="dd0ef-170">False</span><span class="sxs-lookup"><span data-stu-id="dd0ef-170">false</span></span>|<span data-ttu-id="dd0ef-171">true</span><span class="sxs-lookup"><span data-stu-id="dd0ef-171">true</span></span>|<span data-ttu-id="dd0ef-172">False</span><span class="sxs-lookup"><span data-stu-id="dd0ef-172">false</span></span>|<span data-ttu-id="dd0ef-173">true</span><span class="sxs-lookup"><span data-stu-id="dd0ef-173">true</span></span>|  
|<span data-ttu-id="dd0ef-174">False</span><span class="sxs-lookup"><span data-stu-id="dd0ef-174">false</span></span>|<span data-ttu-id="dd0ef-175">False</span><span class="sxs-lookup"><span data-stu-id="dd0ef-175">false</span></span>|<span data-ttu-id="dd0ef-176">False</span><span class="sxs-lookup"><span data-stu-id="dd0ef-176">false</span></span>|<span data-ttu-id="dd0ef-177">False</span><span class="sxs-lookup"><span data-stu-id="dd0ef-177">false</span></span>|  
|<span data-ttu-id="dd0ef-178">False</span><span class="sxs-lookup"><span data-stu-id="dd0ef-178">false</span></span>|<span data-ttu-id="dd0ef-179">null</span><span class="sxs-lookup"><span data-stu-id="dd0ef-179">null</span></span>|<span data-ttu-id="dd0ef-180">False</span><span class="sxs-lookup"><span data-stu-id="dd0ef-180">false</span></span>|<span data-ttu-id="dd0ef-181">null</span><span class="sxs-lookup"><span data-stu-id="dd0ef-181">null</span></span>|  
|<span data-ttu-id="dd0ef-182">null</span><span class="sxs-lookup"><span data-stu-id="dd0ef-182">null</span></span>|<span data-ttu-id="dd0ef-183">true</span><span class="sxs-lookup"><span data-stu-id="dd0ef-183">true</span></span>|<span data-ttu-id="dd0ef-184">null</span><span class="sxs-lookup"><span data-stu-id="dd0ef-184">null</span></span>|<span data-ttu-id="dd0ef-185">true</span><span class="sxs-lookup"><span data-stu-id="dd0ef-185">true</span></span>|  
|<span data-ttu-id="dd0ef-186">null</span><span class="sxs-lookup"><span data-stu-id="dd0ef-186">null</span></span>|<span data-ttu-id="dd0ef-187">False</span><span class="sxs-lookup"><span data-stu-id="dd0ef-187">false</span></span>|<span data-ttu-id="dd0ef-188">False</span><span class="sxs-lookup"><span data-stu-id="dd0ef-188">false</span></span>|<span data-ttu-id="dd0ef-189">null</span><span class="sxs-lookup"><span data-stu-id="dd0ef-189">null</span></span>|  
|<span data-ttu-id="dd0ef-190">null</span><span class="sxs-lookup"><span data-stu-id="dd0ef-190">null</span></span>|<span data-ttu-id="dd0ef-191">null</span><span class="sxs-lookup"><span data-stu-id="dd0ef-191">null</span></span>|<span data-ttu-id="dd0ef-192">null</span><span class="sxs-lookup"><span data-stu-id="dd0ef-192">null</span></span>|<span data-ttu-id="dd0ef-193">null</span><span class="sxs-lookup"><span data-stu-id="dd0ef-193">null</span></span>|  

<span data-ttu-id="dd0ef-194">해당 연산자의 동작은 Nullable 값 형식을 사용하는 일반 연산자 동작과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-194">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="dd0ef-195">일반적으로 값 형식의 피연산자에 대해 정의된 연산자도 해당 Nullable 값 형식의 피연산자와 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-195">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="dd0ef-196">피연산자가 `null`인 경우 해당 연산자는 `null`을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-196">Such an operator produces `null` if any of its operands is `null`.</span></span> <span data-ttu-id="dd0ef-197">그러나 피연산자 중 하나가 `null`인 경우에도 `&` 및 `|` 연산자는 Null이 아닌 값을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-197">However, the `&` and `|` operators can produce non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="dd0ef-198">Nullable 형식을 사용한 연산자 동작에 대한 자세한 내용은 [nullable 형식 사용](../../programming-guide/nullable-types/using-nullable-types.md) 문서의 [연산자](../../programming-guide/nullable-types/using-nullable-types.md#operators) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-198">For more information about the operator behavior with nullable value types, see the [Operators](../../programming-guide/nullable-types/using-nullable-types.md#operators) section of the [Using nullable types](../../programming-guide/nullable-types/using-nullable-types.md) article.</span></span>

<span data-ttu-id="dd0ef-199">다음 예제와 같이 `!` 및 `^` 연산자를 `bool?` 피연산자와 함께 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-199">You can also use the `!` and `^` operators with the `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="dd0ef-200">조건부 논리 연산자 `&&` 및 `||`는 `bool?` 피연산자를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-200">The conditional logical operators `&&` and `||` don't support the `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="dd0ef-201">복합 할당</span><span class="sxs-lookup"><span data-stu-id="dd0ef-201">Compound assignment</span></span>

<span data-ttu-id="dd0ef-202">이진 연산자(`op`)의 경우 양식의 복합 할당 식</span><span class="sxs-lookup"><span data-stu-id="dd0ef-202">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="dd0ef-203">위의 식은 아래의 식과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-203">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="dd0ef-204">단, `x`가 한 번만 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-204">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="dd0ef-205">`&`, `|` 및 `^` 연산자는 다음 예제와 같이 복합 할당을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-205">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#CompoundAssignment)]

<span data-ttu-id="dd0ef-206">조건부 논리 연산자 `&&` 및 `||`는 복합 할당을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-206">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="dd0ef-207">연산자 우선 순위</span><span class="sxs-lookup"><span data-stu-id="dd0ef-207">Operator precedence</span></span>

<span data-ttu-id="dd0ef-208">다음 목록에서는 논리 연산자를 가장 높은 우선 순위부터 가장 낮은 것으로 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-208">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="dd0ef-209">논리 부정 연산자</span><span class="sxs-lookup"><span data-stu-id="dd0ef-209">Logical negation operator</span></span> `!`
- <span data-ttu-id="dd0ef-210">논리곱 연산자</span><span class="sxs-lookup"><span data-stu-id="dd0ef-210">Logical AND operator</span></span> `&`
- <span data-ttu-id="dd0ef-211">논리 배타적 OR 연산자</span><span class="sxs-lookup"><span data-stu-id="dd0ef-211">Logical exclusive OR operator</span></span> `^`
- <span data-ttu-id="dd0ef-212">이는 논리 OR 연산자입니다</span><span class="sxs-lookup"><span data-stu-id="dd0ef-212">Logical OR operator</span></span> `|`
- <span data-ttu-id="dd0ef-213">조건부 논리 AND 연산자</span><span class="sxs-lookup"><span data-stu-id="dd0ef-213">Conditional logical AND operator</span></span> `&&`
- <span data-ttu-id="dd0ef-214">조건부 논리 OR 연산자</span><span class="sxs-lookup"><span data-stu-id="dd0ef-214">Conditional logical OR operator</span></span> `||`

<span data-ttu-id="dd0ef-215">괄호(`()`)를 사용하여 연산자 우선 순위에 따라 주어진 평가 순서를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-215">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Precedence)]

<span data-ttu-id="dd0ef-216">우선 순위 수준에 따라 정렬된 전체 연산자 목록은 [C# 연산자](index.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-216">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="dd0ef-217">연산자 오버로드 가능성</span><span class="sxs-lookup"><span data-stu-id="dd0ef-217">Operator overloadability</span></span>

<span data-ttu-id="dd0ef-218">사용자 정의 형식은 `!`, `&`, `|` 및 `^` 연산자를 [오버로드](../keywords/operator.md)할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-218">A user-defined type can [overload](../keywords/operator.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="dd0ef-219">이항 연산자가 오버로드되면 해당하는 복합 대입 연산자도 암시적으로 오버로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-219">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="dd0ef-220">사용자 정의 형식은 복합 대입 연산자를 명시적으로 오버로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-220">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="dd0ef-221">사용자 정의 형식은 조건부 논리 연산자 `&&` 및 `||`를 오버로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-221">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="dd0ef-222">그러나 사용자 정의 형식이 [true 및 false 연산자](../keywords/true-false-operators.md)와 `&` 또는 `|` 연산자를 특정 방식으로 오버로드하는 경우 `&&` 또는 `||` 작업은 각각 해당 형식의 피연산자에 대해 평가될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-222">However, if a user-defined type overloads the [true and false operators](../keywords/true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="dd0ef-223">자세한 내용은 [C# 언어 사양](~/_csharplang/spec/introduction.md)의 [사용자 정의 조건부 논리 연산자](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-223">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="dd0ef-224">C# 언어 사양</span><span class="sxs-lookup"><span data-stu-id="dd0ef-224">C# language specification</span></span>

<span data-ttu-id="dd0ef-225">자세한 내용은 [C# 언어 사양](~/_csharplang/spec/introduction.md)의 다음 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dd0ef-225">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="dd0ef-226">논리 부정 연산자</span><span class="sxs-lookup"><span data-stu-id="dd0ef-226">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="dd0ef-227">논리 연산자</span><span class="sxs-lookup"><span data-stu-id="dd0ef-227">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="dd0ef-228">조건부 논리 연산자</span><span class="sxs-lookup"><span data-stu-id="dd0ef-228">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)

## <a name="see-also"></a><span data-ttu-id="dd0ef-229">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dd0ef-229">See also</span></span>

- [<span data-ttu-id="dd0ef-230">C# 참조</span><span class="sxs-lookup"><span data-stu-id="dd0ef-230">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="dd0ef-231">C# 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="dd0ef-231">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="dd0ef-232">C# 연산자</span><span class="sxs-lookup"><span data-stu-id="dd0ef-232">C# Operators</span></span>](index.md)