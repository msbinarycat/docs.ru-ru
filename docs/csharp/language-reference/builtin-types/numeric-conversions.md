---
title: Встроенные числовые преобразования — справочник по C#
ms.date: 10/22/2019
helpviewer_keywords:
- implicit numeric conversions [C#]
- explicit numeric conversion [C#]
- numeric conversions [C#], implicit
- numeric conversions [C#], explicit
- conversions [C#], implicit numeric
- conversions [C#], explicit numeric
ms.openlocfilehash: 5380e8480c39d1940df13b2ecb50a0f394367388
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72776021"
---
# <a name="built-in-numeric-conversions-c-reference"></a><span data-ttu-id="8af13-102">Встроенные числовые преобразования (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="8af13-102">Built-in numeric conversions (C# reference)</span></span>

<span data-ttu-id="8af13-103">C# предоставляет набор [целочисленных](integral-numeric-types.md) типов и типы [с плавающей запятой](floating-point-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="8af13-103">C# provides a set of [integral](integral-numeric-types.md) and [floating-point](floating-point-numeric-types.md) numeric types.</span></span> <span data-ttu-id="8af13-104">Существует преобразование между любыми двумя числовыми типами: неявное или явное.</span><span class="sxs-lookup"><span data-stu-id="8af13-104">There exists a conversion between any two numeric types, either implicit or explicit.</span></span> <span data-ttu-id="8af13-105">Используйте [оператор приведения `()`](../operators/type-testing-and-cast.md#cast-operator-) для вызова явного преобразования.</span><span class="sxs-lookup"><span data-stu-id="8af13-105">You must use the [cast operator `()`](../operators/type-testing-and-cast.md#cast-operator-) to invoke an explicit conversion.</span></span>

## <a name="implicit-numeric-conversions"></a><span data-ttu-id="8af13-106">Неявные числовые преобразования</span><span class="sxs-lookup"><span data-stu-id="8af13-106">Implicit numeric conversions</span></span>

<span data-ttu-id="8af13-107">В следующей таблице приведены предопределенные неявные преобразования между встроенными числовыми типами:</span><span class="sxs-lookup"><span data-stu-id="8af13-107">The following table shows the predefined implicit conversions between the built-in numeric types:</span></span>

|<span data-ttu-id="8af13-108">Исходный тип</span><span class="sxs-lookup"><span data-stu-id="8af13-108">From</span></span>|<span data-ttu-id="8af13-109">Кому</span><span class="sxs-lookup"><span data-stu-id="8af13-109">To</span></span>|
|----------|--------|
|[<span data-ttu-id="8af13-110">sbyte</span><span class="sxs-lookup"><span data-stu-id="8af13-110">sbyte</span></span>](integral-numeric-types.md)|<span data-ttu-id="8af13-111">`short`, `int`, `long`, `float`, `double` или `decimal`</span><span class="sxs-lookup"><span data-stu-id="8af13-111">`short`, `int`, `long`, `float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="8af13-112">byte</span><span class="sxs-lookup"><span data-stu-id="8af13-112">byte</span></span>](integral-numeric-types.md)|<span data-ttu-id="8af13-113">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double` или `decimal`</span><span class="sxs-lookup"><span data-stu-id="8af13-113">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="8af13-114">short</span><span class="sxs-lookup"><span data-stu-id="8af13-114">short</span></span>](integral-numeric-types.md)|<span data-ttu-id="8af13-115">`int`, `long`, `float`, `double` или `decimal`</span><span class="sxs-lookup"><span data-stu-id="8af13-115">`int`, `long`, `float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="8af13-116">ushort</span><span class="sxs-lookup"><span data-stu-id="8af13-116">ushort</span></span>](integral-numeric-types.md)|<span data-ttu-id="8af13-117">`int`, `uint`, `long`, `ulong`, `float`, `double` или `decimal`</span><span class="sxs-lookup"><span data-stu-id="8af13-117">`int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="8af13-118">int</span><span class="sxs-lookup"><span data-stu-id="8af13-118">int</span></span>](integral-numeric-types.md)|<span data-ttu-id="8af13-119">`long`, `float`, `double` или `decimal`</span><span class="sxs-lookup"><span data-stu-id="8af13-119">`long`, `float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="8af13-120">uint</span><span class="sxs-lookup"><span data-stu-id="8af13-120">uint</span></span>](integral-numeric-types.md)|<span data-ttu-id="8af13-121">`long`, `ulong`, `float`, `double` или `decimal`</span><span class="sxs-lookup"><span data-stu-id="8af13-121">`long`, `ulong`, `float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="8af13-122">long</span><span class="sxs-lookup"><span data-stu-id="8af13-122">long</span></span>](integral-numeric-types.md)|<span data-ttu-id="8af13-123">`float`, `double`или `decimal`</span><span class="sxs-lookup"><span data-stu-id="8af13-123">`float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="8af13-124">ulong</span><span class="sxs-lookup"><span data-stu-id="8af13-124">ulong</span></span>](integral-numeric-types.md)|<span data-ttu-id="8af13-125">`float`, `double`или `decimal`</span><span class="sxs-lookup"><span data-stu-id="8af13-125">`float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="8af13-126">float</span><span class="sxs-lookup"><span data-stu-id="8af13-126">float</span></span>](floating-point-numeric-types.md)|`double`|

> [!NOTE]
> <span data-ttu-id="8af13-127">Неявные преобразования из `int`, `uint`, `long` или `ulong` в `float` и из `long` или `ulong` в `double` могут приводить к потере точности, но не к потере порядка величин.</span><span class="sxs-lookup"><span data-stu-id="8af13-127">The implicit conversions from `int`, `uint`, `long`, or `ulong` to `float` and from `long` or `ulong` to `double` may cause a loss of precision, but never a loss of an order of magnitude.</span></span> <span data-ttu-id="8af13-128">Другие неявные числовые преобразования никогда не теряют никаких сведений.</span><span class="sxs-lookup"><span data-stu-id="8af13-128">The other implicit numeric conversions never lose any information.</span></span>

<span data-ttu-id="8af13-129">Также обратите внимание на следующее.</span><span class="sxs-lookup"><span data-stu-id="8af13-129">Also note that</span></span>

- <span data-ttu-id="8af13-130">Любой [целочисленный тип](integral-numeric-types.md) неявно преобразуется в любой [числовой тип с плавающей запятой](floating-point-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="8af13-130">Any [integral numeric type](integral-numeric-types.md) is implicitly convertible to any [floating-point numeric type](floating-point-numeric-types.md).</span></span>

- <span data-ttu-id="8af13-131">Не поддерживается неявное преобразование в типы `byte` и `sbyte`.</span><span class="sxs-lookup"><span data-stu-id="8af13-131">There are no implicit conversions to the `byte` and `sbyte` types.</span></span> <span data-ttu-id="8af13-132">Не поддерживается неявное преобразование из типов `double` и `decimal`.</span><span class="sxs-lookup"><span data-stu-id="8af13-132">There are no implicit conversions from the `double` and `decimal` types.</span></span>

- <span data-ttu-id="8af13-133">Не поддерживается неявное преобразование между типом `decimal` и типами `float` или `double`.</span><span class="sxs-lookup"><span data-stu-id="8af13-133">There are no implicit conversions between the `decimal` type and the `float` or `double` types.</span></span>

- <span data-ttu-id="8af13-134">Значение константного выражения типа `int` (например, значение, представленное целочисленным литералом) может быть неявно преобразовано в `sbyte`, `byte`, `short`, `ushort`, `uint` или `ulong`, если оно находится в диапазоне целевого типа:</span><span class="sxs-lookup"><span data-stu-id="8af13-134">A value of a constant expression of type `int` (for example, a value represented by an integer literal) can be implicitly converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`, if it's within the range of the destination type:</span></span>

  ```csharp
  byte a = 13;
  byte b = 300;  // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

  <span data-ttu-id="8af13-135">Как показано в предыдущем примере, если значение константы выходит за пределы диапазона целевого типа, возникает ошибка компилятора [CS0031](../../misc/cs0031.md).</span><span class="sxs-lookup"><span data-stu-id="8af13-135">As the preceding example shows, if the constant value is not within the range of the destination type, a compiler error [CS0031](../../misc/cs0031.md) occurs.</span></span>

## <a name="explicit-numeric-conversions"></a><span data-ttu-id="8af13-136">Явные числовые преобразования</span><span class="sxs-lookup"><span data-stu-id="8af13-136">Explicit numeric conversions</span></span>

<span data-ttu-id="8af13-137">В следующей таблице показаны предопределенные явные преобразования между встроенными числовыми типами, для которых нет [неявного преобразования](#implicit-numeric-conversions):</span><span class="sxs-lookup"><span data-stu-id="8af13-137">The following table shows the predefined explicit conversions between the built-in numeric types for which there is no [implicit conversion](#implicit-numeric-conversions):</span></span>

|<span data-ttu-id="8af13-138">Исходный тип</span><span class="sxs-lookup"><span data-stu-id="8af13-138">From</span></span>|<span data-ttu-id="8af13-139">Кому</span><span class="sxs-lookup"><span data-stu-id="8af13-139">To</span></span>|
|----------|--------|
|[<span data-ttu-id="8af13-140">sbyte</span><span class="sxs-lookup"><span data-stu-id="8af13-140">sbyte</span></span>](integral-numeric-types.md)|<span data-ttu-id="8af13-141">`byte`, `ushort`, `uint` или `ulong`</span><span class="sxs-lookup"><span data-stu-id="8af13-141">`byte`, `ushort`, `uint`, or `ulong`</span></span>|
|[<span data-ttu-id="8af13-142">byte</span><span class="sxs-lookup"><span data-stu-id="8af13-142">byte</span></span>](integral-numeric-types.md)|`sbyte`|
|[<span data-ttu-id="8af13-143">short</span><span class="sxs-lookup"><span data-stu-id="8af13-143">short</span></span>](integral-numeric-types.md)|<span data-ttu-id="8af13-144">`sbyte`, `byte`, `ushort`, `uint` или `ulong`</span><span class="sxs-lookup"><span data-stu-id="8af13-144">`sbyte`, `byte`, `ushort`, `uint`, or `ulong`</span></span>|
|[<span data-ttu-id="8af13-145">ushort</span><span class="sxs-lookup"><span data-stu-id="8af13-145">ushort</span></span>](integral-numeric-types.md)|<span data-ttu-id="8af13-146">`sbyte`, `byte`или `short`</span><span class="sxs-lookup"><span data-stu-id="8af13-146">`sbyte`, `byte`, or `short`</span></span>|
|[<span data-ttu-id="8af13-147">int</span><span class="sxs-lookup"><span data-stu-id="8af13-147">int</span></span>](integral-numeric-types.md)|<span data-ttu-id="8af13-148">`sbyte`, `byte`, `short`, `ushort`, `uint` или `ulong`</span><span class="sxs-lookup"><span data-stu-id="8af13-148">`sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`</span></span>|
|[<span data-ttu-id="8af13-149">uint</span><span class="sxs-lookup"><span data-stu-id="8af13-149">uint</span></span>](integral-numeric-types.md)|<span data-ttu-id="8af13-150">`sbyte`, `byte`, `short`, `ushort` или `int`</span><span class="sxs-lookup"><span data-stu-id="8af13-150">`sbyte`, `byte`, `short`, `ushort`, or `int`</span></span>|
|[<span data-ttu-id="8af13-151">long</span><span class="sxs-lookup"><span data-stu-id="8af13-151">long</span></span>](integral-numeric-types.md)|<span data-ttu-id="8af13-152">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint` или `ulong`</span><span class="sxs-lookup"><span data-stu-id="8af13-152">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, or `ulong`</span></span>|
|[<span data-ttu-id="8af13-153">ulong</span><span class="sxs-lookup"><span data-stu-id="8af13-153">ulong</span></span>](integral-numeric-types.md)|<span data-ttu-id="8af13-154">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint` или `long`</span><span class="sxs-lookup"><span data-stu-id="8af13-154">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, or `long`</span></span>|
|[<span data-ttu-id="8af13-155">float</span><span class="sxs-lookup"><span data-stu-id="8af13-155">float</span></span>](floating-point-numeric-types.md)|<span data-ttu-id="8af13-156">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong` или `decimal`</span><span class="sxs-lookup"><span data-stu-id="8af13-156">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, or `decimal`</span></span>|
|[<span data-ttu-id="8af13-157">double</span><span class="sxs-lookup"><span data-stu-id="8af13-157">double</span></span>](floating-point-numeric-types.md)|<span data-ttu-id="8af13-158">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float` или `decimal`</span><span class="sxs-lookup"><span data-stu-id="8af13-158">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, or `decimal`</span></span>|
|[<span data-ttu-id="8af13-159">decimal</span><span class="sxs-lookup"><span data-stu-id="8af13-159">decimal</span></span>](floating-point-numeric-types.md)|<span data-ttu-id="8af13-160">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float` или `double`</span><span class="sxs-lookup"><span data-stu-id="8af13-160">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, or `double`</span></span>|

> [!NOTE]
> <span data-ttu-id="8af13-161">Явное числовое преобразование может привести к утрате данных или созданию исключения, обычно <xref:System.OverflowException>.</span><span class="sxs-lookup"><span data-stu-id="8af13-161">An explicit numeric conversion might result in data loss or throw an exception, typically an <xref:System.OverflowException>.</span></span>

<span data-ttu-id="8af13-162">Также обратите внимание на следующее.</span><span class="sxs-lookup"><span data-stu-id="8af13-162">Also note that</span></span>

- <span data-ttu-id="8af13-163">При преобразовании значения целочисленного типа в другой целочисленный тип результат зависит от переполнения [контекста проверки](../keywords/checked-and-unchecked.md).</span><span class="sxs-lookup"><span data-stu-id="8af13-163">When you convert a value of an integral type to another integral type, the result depends on the overflow [checking context](../keywords/checked-and-unchecked.md).</span></span> <span data-ttu-id="8af13-164">В проверенном контексте преобразование выполняется успешно, если исходное значение находится в диапазоне конечного типа.</span><span class="sxs-lookup"><span data-stu-id="8af13-164">In a checked context, the conversion succeeds if the source value is within the range of the destination type.</span></span> <span data-ttu-id="8af13-165">В противном случае возникает исключение <xref:System.OverflowException>.</span><span class="sxs-lookup"><span data-stu-id="8af13-165">Otherwise, an <xref:System.OverflowException> is thrown.</span></span> <span data-ttu-id="8af13-166">В непроверяемом контексте преобразование всегда завершается успешно и выполняется следующим образом.</span><span class="sxs-lookup"><span data-stu-id="8af13-166">In an unchecked context, the conversion always succeeds, and proceeds as follows:</span></span>

  - <span data-ttu-id="8af13-167">Если исходный тип больше целевого, исходное значение усекается путем отбрасывания его "лишних" самых значимых битов.</span><span class="sxs-lookup"><span data-stu-id="8af13-167">If the source type is larger than the destination type, then the source value is truncated by discarding its "extra" most significant bits.</span></span> <span data-ttu-id="8af13-168">Результат затем обрабатывается как значение целевого типа.</span><span class="sxs-lookup"><span data-stu-id="8af13-168">The result is then treated as a value of the destination type.</span></span>

  - <span data-ttu-id="8af13-169">Если исходный тип меньше целевого, исходное значение дополняется знаками или нулями, чтобы иметь тот же размер, что и целевой тип.</span><span class="sxs-lookup"><span data-stu-id="8af13-169">If the source type is smaller than the destination type, then the source value is either sign-extended or zero-extended so that it's of the same size as the destination type.</span></span> <span data-ttu-id="8af13-170">Знаки добавляются, если исходный тип имеет знак. Если у исходного типа нет знака, добавляются нули.</span><span class="sxs-lookup"><span data-stu-id="8af13-170">Sign-extension is used if the source type is signed; zero-extension is used if the source type is unsigned.</span></span> <span data-ttu-id="8af13-171">Результат затем обрабатывается как значение целевого типа.</span><span class="sxs-lookup"><span data-stu-id="8af13-171">The result is then treated as a value of the destination type.</span></span>

  - <span data-ttu-id="8af13-172">Если исходный тип совпадает по размеру с целевым, исходное значение обрабатывается как значение целевого типа.</span><span class="sxs-lookup"><span data-stu-id="8af13-172">If the source type is the same size as the destination type, then the source value is treated as a value of the destination type.</span></span>

- <span data-ttu-id="8af13-173">При преобразовании значения `decimal` в целочисленный тип оно округляется в сторону нуля до ближайшего целого значения.</span><span class="sxs-lookup"><span data-stu-id="8af13-173">When you convert a `decimal` value to an integral type, this value is rounded towards zero to the nearest integral value.</span></span> <span data-ttu-id="8af13-174">Если итоговое целое значение находится вне диапазона целевого типа, возникает исключение <xref:System.OverflowException>.</span><span class="sxs-lookup"><span data-stu-id="8af13-174">If the resulting integral value is outside the range of the destination type, an <xref:System.OverflowException> is thrown.</span></span>

- <span data-ttu-id="8af13-175">При преобразовании значения `double` или `float` в целочисленный тип оно округляется в сторону нуля до ближайшего целого значения.</span><span class="sxs-lookup"><span data-stu-id="8af13-175">When you convert a `double` or `float` value to an integral type, this value is rounded towards zero to the nearest integral value.</span></span> <span data-ttu-id="8af13-176">Если полученное целое значение выходит за пределы диапазона целевого типа, результат будет зависеть от [контекста проверки](../keywords/checked-and-unchecked.md) переполнения.</span><span class="sxs-lookup"><span data-stu-id="8af13-176">If the resulting integral value is outside the range of the destination type, the result depends on the overflow [checking context](../keywords/checked-and-unchecked.md).</span></span> <span data-ttu-id="8af13-177">В проверенном контексте возникает исключение <xref:System.OverflowException>, а в непроверенном контексте результатом будет неопределенное значение целевого типа.</span><span class="sxs-lookup"><span data-stu-id="8af13-177">In a checked context, an <xref:System.OverflowException> is thrown, while in an unchecked context, the result is an unspecified value of the destination type.</span></span>

- <span data-ttu-id="8af13-178">При преобразовании из `double` в `float` значение `double` округляется до ближайшего значения `float`.</span><span class="sxs-lookup"><span data-stu-id="8af13-178">When you convert `double` to `float`, the `double` value is rounded to the nearest `float` value.</span></span> <span data-ttu-id="8af13-179">Если значение `double` слишком мало или слишком велико для типа `float`, результатом будет ноль или бесконечность соответственно.</span><span class="sxs-lookup"><span data-stu-id="8af13-179">If the `double` value is too small or too large to fit into the `float` type, the result is zero or infinity.</span></span>

- <span data-ttu-id="8af13-180">При преобразовании из `float` или `double` в `decimal` исходное значение преобразуется в представление `decimal` и при необходимости округляется до ближайшего числа после 28-го десятичного разряда.</span><span class="sxs-lookup"><span data-stu-id="8af13-180">When you convert `float` or `double` to `decimal`, the source value is converted to `decimal` representation and rounded to the nearest number after the 28th decimal place if required.</span></span> <span data-ttu-id="8af13-181">В зависимости от исходного значения возможны следующие результаты:</span><span class="sxs-lookup"><span data-stu-id="8af13-181">Depending on the value of the source value, one of the following results may occur:</span></span>

  - <span data-ttu-id="8af13-182">Если исходное значение слишком мало для представления в виде `decimal`, результатом будет ноль.</span><span class="sxs-lookup"><span data-stu-id="8af13-182">If the source value is too small to be represented as a `decimal`, the result becomes zero.</span></span>

  - <span data-ttu-id="8af13-183">Если исходное значение не является числом (NaN), равно бесконечности или слишком велико для представления в виде `decimal`, возникает исключение <xref:System.OverflowException>.</span><span class="sxs-lookup"><span data-stu-id="8af13-183">If the source value is NaN (not a number), infinity, or too large to be represented as a `decimal`, an <xref:System.OverflowException> is thrown.</span></span>

- <span data-ttu-id="8af13-184">При преобразовании из `decimal` в `float` или `double` исходное значение округляется до ближайшего значения `float` или `double` соответственно.</span><span class="sxs-lookup"><span data-stu-id="8af13-184">When you convert `decimal` to `float` or `double`, the source value is rounded to the nearest `float` or `double` value, respectively.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8af13-185">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="8af13-185">C# language specification</span></span>

<span data-ttu-id="8af13-186">Дополнительные сведения см. в следующих разделах статьи [Спецификация языка C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="8af13-186">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="8af13-187">Неявные числовые преобразования</span><span class="sxs-lookup"><span data-stu-id="8af13-187">Implicit numeric conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-numeric-conversions)
- [<span data-ttu-id="8af13-188">Явные числовые преобразования</span><span class="sxs-lookup"><span data-stu-id="8af13-188">Explicit numeric conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-numeric-conversions)

## <a name="see-also"></a><span data-ttu-id="8af13-189">См. также</span><span class="sxs-lookup"><span data-stu-id="8af13-189">See also</span></span>

- [<span data-ttu-id="8af13-190">справочник по C#</span><span class="sxs-lookup"><span data-stu-id="8af13-190">C# reference</span></span>](../index.md)
- [<span data-ttu-id="8af13-191">Приведение и преобразование типов</span><span class="sxs-lookup"><span data-stu-id="8af13-191">Casting and type conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)