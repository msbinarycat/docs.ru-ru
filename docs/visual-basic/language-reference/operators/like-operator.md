---
title: Оператор Like
ms.date: 07/20/2015
f1_keywords:
- Like
- vb.Like
helpviewer_keywords:
- similar to
- pattern matching
- Like operator [Visual Basic]
- '? symbol, wildcard character'
- string comparison [Visual Basic], Like operator
- strings [Visual Basic], comparing
- comparison operators [Visual Basic]
- symbols, wildcard
- wildcards, Like operator
- strings [Visual Basic], matching
- string comparison [Visual Basic], sorting data
- data [Visual Basic], sorting
- text [Visual Basic], comparing
- operators [Visual Basic], pattern-matching
- data [Visual Basic], string comparisons
- string comparison [Visual Basic], Like operators
ms.assetid: 966283ec-80e2-4294-baa8-c75baff804f9
ms.openlocfilehash: 5db9488bbec716156a3ab464042c0853241a82b1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350937"
---
# <a name="like-operator-visual-basic"></a>Оператор Like (Visual Basic)
Сравнивает строку с шаблоном.  

> [!IMPORTANT]
> В настоящее время оператор `Like` не поддерживается в проектах .NET Core и .NET Standard.

## <a name="syntax"></a>Синтаксис  
  
```vb  
result = string Like pattern  
```  
  
## <a name="parts"></a>Части  
 `result`  
 Обязательно. Любая переменная `Boolean`. Результатом является `Boolean` значение, указывающее, удовлетворяет ли `string` `pattern`.  
  
 `string`  
 Обязательно. Произвольное выражение `String` .  
  
 `pattern`  
 Обязательно. Любое `String` выражение, удовлетворяющее соглашениям о соответствии шаблону, описанным в разделе «Примечания».  
  
## <a name="remarks"></a>Примечания  
 Если значение в `string` соответствует шаблону, содержащемуся в `pattern`, `result` `True`. Если строка не соответствует шаблону, `result` `False`. Если оба `string` и `pattern` являются пустыми строками, результат будет `True`.  
  
## <a name="comparison-method"></a>Метод сравнения  
 Поведение оператора `Like` зависит от [оператора Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md). Для каждого исходного файла используется метод сравнения строк по умолчанию `Option Compare Binary`.  
  
## <a name="pattern-options"></a>Параметры шаблона  
 Встроенное сопоставление шаблонов предоставляет универсальное средство для сравнения строк. Функции сопоставления шаблонов позволяют сопоставить каждый символ в `string` с конкретным символом, символом-шаблоном, списком символов или диапазоном символов. В следующей таблице приведены символы, разрешенные в `pattern` и их соответствие.  
  
|Символы в `pattern`|Соответствия в `string`|  
|-----------------------------|-------------------------|  
|`?`|Любой отдельный знак|  
|`*`|Ноль или более символов|  
|`#`|Любая отдельная цифра (0 – 9)|  
|`[charlist]`|Любой отдельный символ в `charlist`|  
|`[!charlist]`|Любой отдельный символ, не являющийся `charlist`|  
  
## <a name="character-lists"></a>Списки символов  
 Группа из одного или нескольких символов (`charlist`), заключенных в квадратные скобки (`[ ]`), может использоваться для сопоставления любого отдельного символа в `string` и может включать практически любой код символа, включая цифры.  
  
 Восклицательный знак (`!`) в начале `charlist` означает, что сопоставление выполняется, если в `string`найден любой символ, кроме символов в `charlist`. При использовании вне квадратных скобок восклицательный знак соответствует самому себе.  
  
## <a name="special-characters"></a>Специальные символы  
 Чтобы сопоставить специальные символы с левой скобкой (`[`), вопросительный знак (`?`), знак решетки (`#`) и звездочка (`*`), заключите их в квадратные скобки. Правая квадратная скобка (`]`) не может использоваться в группе для сопоставления самой себе, но ее можно использовать за пределами группы в качестве отдельного символа.  
  
 `[]` последовательности символов считается строкой нулевой длины (`""`). Однако она не может входить в список символов, заключенный в квадратные скобки. Если вы хотите проверить, содержит ли расположение в `string` одну из групп символов или вообще не использовать ни одного символа, можно воспользоваться `Like` дважды. Пример см. в разделе [как сопоставить строку с шаблоном](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).  
  
## <a name="character-ranges"></a>Диапазоны символов  
 Используя дефис (`–`) для разделения нижней и верхней границ диапазона, `charlist` может указать диапазон символов. Например, `[A–Z]` приводит к совпадению, если соответствующая символьная позиции в `string` содержит любой символ в диапазоне `A`–`Z`, а `[!H–L]` приводит к совпадению, если соответствующая символьная позиции содержит любой символ за пределами диапазона `H`–`L`.  
  
 При указании диапазона символов они должны отображаться в порядке сортировки по возрастанию, то есть от самого низкого до самого высокого. Таким образом, `[A–Z]` является допустимым шаблоном, но `[Z–A]` не является.  
  
### <a name="multiple-character-ranges"></a>Несколько диапазонов символов  
 Чтобы указать несколько диапазонов для одной позиции символа, поместите их в одни и те же квадратные скобки без разделителей. Например, `[A–CX–Z]` приводит к совпадению, если соответствующая символьная позиции в `string` содержит любой символ в диапазоне `A`–`C` или диапазон `X`–`Z`.  
  
### <a name="usage-of-the-hyphen"></a>Использование дефиса  
 Дефис (`–`) может располагаться в начале (после восклицательного знака, если есть) или в конце `charlist` для сопоставления с самим собой. В любом другом расположении дефис определяет диапазон символов, разделенных символами с любой стороны дефиса.  
  
## <a name="collating-sequence"></a>Порядок сортировки  
 Значение указанного диапазона зависит от порядка символов во время выполнения, как определено `Option Compare` и параметром языкового стандарта системы, в которой выполняется код. При использовании `Option Compare Binary`диапазон `[A–E]` соответствует `A`, `B`, `C`, `D`и `E`. С помощью `Option Compare Text``[A–E]` соответствует `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`и `e`. Диапазон не соответствует `Ê` или `ê`, так как диакритические знаки сортируются после символов без диакритических знаков в порядке сортировки.  
  
## <a name="digraph-characters"></a>Символы раскрутки  
 В некоторых языках есть алфавитные символы, представляющие два отдельных символа. Например, несколько языков используют символ `æ` для представления символов `a` и `e`, когда они появляются вместе. Оператор `Like` распознает, что один символ раскрутки и два отдельных символа эквивалентны.  
  
 Если в параметрах национальной настройки системы указан язык, использующий символ относительных значений, то вхождение одного символа относительных значений в `pattern` или `string` совпадает с эквивалентной последовательностью двух символов в другой строке. Аналогично, символ-граф в `pattern`, заключенный в квадратные скобки (сам по себе, в списке или в диапазоне), совпадает с эквивалентной последовательностью двух символов в `string`.  
  
## <a name="overloading"></a>Перегрузка  
 Оператор `Like` может быть *перегружен*, что означает, что класс или структура может переопределить свое поведение, если операнд имеет тип этого класса или структуры. Если код использует этот оператор для такого класса или структуры, убедитесь, что вы понимаете его переопределенное поведение. Для получения дополнительной информации см. [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Пример  
 В этом примере оператор `Like` используется для сравнения строк с различными шаблонами. Результаты попадают в переменную `Boolean`, указывающую, соответствует ли каждая строка шаблону.  
  
 [!code-vb[VbVbalrOperators#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#30)]  
  
## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [Операторы сравнения](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Порядок применения операторов в Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Список операторов, сгруппированных по функциональному назначению](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Оператор Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Операторы и выражения](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Практическое руководство. Сравнение строки на соответствие с шаблоном](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
