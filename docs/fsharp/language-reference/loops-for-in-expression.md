---
title: "循环：for...in 表达式 (F#)"
description: "请参阅如何 F # 为..表达式中循环构造用于循环访问的可枚举集合中的模式的匹配项。"
keywords: "visual f#, f#, 函数编程"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f54e3228-4aec-4d0a-ae37-bc3376508284
ms.openlocfilehash: d86aeb3bdd975261e59004d636354a740bd95c47
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/18/2017
---
# <a name="loops-forin-expression"></a><span data-ttu-id="96761-104">循环：for...in 表达式</span><span class="sxs-lookup"><span data-stu-id="96761-104">Loops: for...in Expression</span></span>

<span data-ttu-id="96761-105">此循环构造用于循环访问如范围表达式、 序列、 列表、 数组或其他构造，用于支持枚举的可枚举集合中的模式的匹配项。</span><span class="sxs-lookup"><span data-stu-id="96761-105">This looping construct is used to iterate over the matches of a pattern in an enumerable collection such as a range expression, sequence, list, array, or other construct that supports enumeration.</span></span>


## <a name="syntax"></a><span data-ttu-id="96761-106">语法</span><span class="sxs-lookup"><span data-stu-id="96761-106">Syntax</span></span>

```fsharp
for pattern in enumerable-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="96761-107">备注</span><span class="sxs-lookup"><span data-stu-id="96761-107">Remarks</span></span>
<span data-ttu-id="96761-108">`for...in`表达式可以相比`for each`中其他.NET 语言语句因为它用于循环访问的可枚举集合中的值。</span><span class="sxs-lookup"><span data-stu-id="96761-108">The `for...in` expression can be compared to the `for each` statement in other .NET languages because it is used to loop over the values in an enumerable collection.</span></span> <span data-ttu-id="96761-109">但是，`for...in`还支持针对的模式匹配集合，而不仅仅是迭代不必对整个集合。</span><span class="sxs-lookup"><span data-stu-id="96761-109">However, `for...in` also supports pattern matching over the collection instead of just iteration over the whole collection.</span></span>

<span data-ttu-id="96761-110">可以指定的可枚举的表达式，可枚举集合形式，或通过使用`..`运算符，作为在整数类型的范围。</span><span class="sxs-lookup"><span data-stu-id="96761-110">The enumerable expression can be specified as an enumerable collection or, by using the `..` operator, as a range on an integral type.</span></span> <span data-ttu-id="96761-111">可枚举的集合包括列表、 序列、 数组、 集、 映射和等等。</span><span class="sxs-lookup"><span data-stu-id="96761-111">Enumerable collections include lists, sequences, arrays, sets, maps, and so on.</span></span> <span data-ttu-id="96761-112">实现任何类型`System.Collections.IEnumerable`可用。</span><span class="sxs-lookup"><span data-stu-id="96761-112">Any type that implements `System.Collections.IEnumerable` can be used.</span></span>

<span data-ttu-id="96761-113">当使用表示范围`..`运算符，你可以使用以下语法。</span><span class="sxs-lookup"><span data-stu-id="96761-113">When you express a range by using the `..` operator, you can use the following syntax.</span></span>

<span data-ttu-id="96761-114">*启动*...</span><span class="sxs-lookup"><span data-stu-id="96761-114">*start* ..</span></span> <span data-ttu-id="96761-115">*完成*</span><span class="sxs-lookup"><span data-stu-id="96761-115">*finish*</span></span>

<span data-ttu-id="96761-116">你还可以使用一种包括递增调用*跳过*，如下面的代码。</span><span class="sxs-lookup"><span data-stu-id="96761-116">You can also use a version that includes an increment called the *skip*, as in the following code.</span></span>

<span data-ttu-id="96761-117">*启动*...</span><span class="sxs-lookup"><span data-stu-id="96761-117">*start* ..</span></span> <span data-ttu-id="96761-118">*跳过*...</span><span class="sxs-lookup"><span data-stu-id="96761-118">*skip* ..</span></span> <span data-ttu-id="96761-119">*完成*</span><span class="sxs-lookup"><span data-stu-id="96761-119">*finish*</span></span>

<span data-ttu-id="96761-120">当你使用作为一种模式的整数范围和一个简单的计数器变量时，典型的行为是计数器变量递增 1 在每次迭代，但如果范围还包括 skip 值，该计数器就会递增 skip 值改为。</span><span class="sxs-lookup"><span data-stu-id="96761-120">When you use integral ranges and a simple counter variable as a pattern, the typical behavior is to increment the counter variable by 1 on each iteration, but if the range includes a skip value, the counter is incremented by the skip value instead.</span></span>

<span data-ttu-id="96761-121">此外可以正文表达式中使用匹配模式中的值。</span><span class="sxs-lookup"><span data-stu-id="96761-121">Values matched in the pattern can also be used in the body expression.</span></span>

<span data-ttu-id="96761-122">下面的代码示例阐释使用`for...in`表达式。</span><span class="sxs-lookup"><span data-stu-id="96761-122">The following code examples illustrate the use of the `for...in` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5201.fs)]

<span data-ttu-id="96761-123">输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="96761-123">The output is as follows.</span></span>

```
1
5
100
450
788
```

<span data-ttu-id="96761-124">下面的示例演示如何循环访问序列，以及如何使用而不是简单变量的元组模式。</span><span class="sxs-lookup"><span data-stu-id="96761-124">The following example shows how to loop over a sequence, and how to use a tuple pattern instead of a simple variable.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5202.fs)]

<span data-ttu-id="96761-125">输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="96761-125">The output is as follows.</span></span>

```
1 squared is 1
2 squared is 4
3 squared is 9
4 squared is 16
5 squared is 25
6 squared is 36
7 squared is 49
8 squared is 64
9 squared is 81
10 squared is 100
```

<span data-ttu-id="96761-126">下面的示例演示如何循环简单整数范围内。</span><span class="sxs-lookup"><span data-stu-id="96761-126">The following example shows how to loop over a simple integer range.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5203.fs)]

<span data-ttu-id="96761-127">Function1 的输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="96761-127">The output of function1 is as follows.</span></span>

```
1 2 3 4 5 6 7 8 9 10
```

<span data-ttu-id="96761-128">下面的示例演示如何循环访问一系列具有 skip 值为 2，其中包括每个其他元素的范围。</span><span class="sxs-lookup"><span data-stu-id="96761-128">The following example shows how to loop over a range with a skip of 2, which includes every other element of the range.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5204.fs)]

<span data-ttu-id="96761-129">输出`function2`如下。</span><span class="sxs-lookup"><span data-stu-id="96761-129">The output of `function2` is as follows.</span></span>

```
1 3 5 7 9
```

<span data-ttu-id="96761-130">下面的示例演示如何使用字符范围。</span><span class="sxs-lookup"><span data-stu-id="96761-130">The following example shows how to use a character range.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5205.fs)]

<span data-ttu-id="96761-131">输出`function3`如下。</span><span class="sxs-lookup"><span data-stu-id="96761-131">The output of `function3` is as follows.</span></span>

```
a b c d e f g h i j k l m n o p q r s t u v w x y z
```

<span data-ttu-id="96761-132">下面的示例演示如何使用负的 skip 值来进行反向迭代。</span><span class="sxs-lookup"><span data-stu-id="96761-132">The following example shows how to use a negative skip value for a reverse iteration.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5208.fs)]

<span data-ttu-id="96761-133">输出`function4`如下。</span><span class="sxs-lookup"><span data-stu-id="96761-133">The output of `function4` is as follows.</span></span>

```
10 9 8 7 6 5 4 3 2 1 ... Lift off!
```

<span data-ttu-id="96761-134">开始和结束范围也可以是表达式，如函数，如以下代码所示。</span><span class="sxs-lookup"><span data-stu-id="96761-134">The beginning and ending of the range can also be expressions, such as functions, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5206.fs)]

<span data-ttu-id="96761-135">输出`function5`此输入与，如下所示。</span><span class="sxs-lookup"><span data-stu-id="96761-135">The output of `function5` with this input is as follows.</span></span>

```
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

<span data-ttu-id="96761-136">元素不需要在循环中时下, 一个示例演示了利用通配符字符 (_)。</span><span class="sxs-lookup"><span data-stu-id="96761-136">The next example shows the use of a wildcard character (_) when the element is not needed in the loop.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5207.fs)]

<span data-ttu-id="96761-137">输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="96761-137">The output is as follows.</span></span>

```
Number of elements in list1: 5
```

<span data-ttu-id="96761-138">`Note`你可以使用`for...in`序列表达式和其他计算表达式，在这种情况下的自定义的版本`for...in`使用表达式。</span><span class="sxs-lookup"><span data-stu-id="96761-138">`Note` You can use `for...in` in sequence expressions and other computation expressions, in which case a customized version of the `for...in` expression is used.</span></span> <span data-ttu-id="96761-139">有关详细信息，请参阅[序列](sequences.md)，[异步工作流](asynchronous-workflows.md)，和[计算表达式](computation-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="96761-139">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="96761-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="96761-140">See Also</span></span>
[<span data-ttu-id="96761-141">F# 语言参考</span><span class="sxs-lookup"><span data-stu-id="96761-141">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="96761-142">循环：`for...to` 表达式</span><span class="sxs-lookup"><span data-stu-id="96761-142">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)

[<span data-ttu-id="96761-143">循环：`while...do` 表达式</span><span class="sxs-lookup"><span data-stu-id="96761-143">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)