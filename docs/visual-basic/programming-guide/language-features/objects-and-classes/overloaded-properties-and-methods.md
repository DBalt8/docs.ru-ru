---
title: Перегруженные свойства и методы
ms.date: 07/20/2015
helpviewer_keywords:
- properties [Visual Basic], overloading
- methods [Visual Basic], overloading
- shadowing
- names [Visual Basic], multiple procedures with same
- procedures [Visual Basic], multiples with same name
- classes [Visual Basic], properties
- classes [Visual Basic], methods
- method overloading
- Overloads keyword [Visual Basic], overloaded members
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
ms.openlocfilehash: 1672f12773ece012c580253b6dafbf9d0ac8f07c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84389156"
---
# <a name="overloaded-properties-and-methods-visual-basic"></a>Перегруженные свойства и методы (Visual Basic)

Перегрузка — это создание более чем одной процедуры, конструктора экземпляра или свойства в классе с тем же именем, но разными типами аргументов.

## <a name="overloading-usage"></a>Перегрузка использования

Перегрузка особенно полезна, когда объектная модель определяет, что для процедур, которые работают с различными типами данных, используются одинаковые имена. Например, класс, который может отображать несколько различных типов данных, может иметь `Display` процедуры, которые выглядят следующим образом:

[!code-vb[VbVbalrOOP#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#64)]

Без перегрузки необходимо создать разные имена для каждой процедуры, даже если они выполняют одно и то же действие, как показано далее:

[!code-vb[VbVbalrOOP#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#65)]

Перегрузка упрощает использование свойств или методов, поскольку она предоставляет возможность выбора типов данных, которые можно использовать. Например, перегруженный `Display` метод, описанный ранее, можно вызвать с помощью любой из следующих строк кода:

[!code-vb[VbVbalrOOP#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#66)]

Во время выполнения Visual Basic вызывает правильную процедуру на основе типов данных указанных параметров.

## <a name="overloading-rules"></a>Перегрузка правил

 Перегруженный член класса создается путем добавления двух или более свойств или методов с одинаковым именем. За исключением перегруженных производных членов, каждый перегруженный член должен иметь разные списки параметров, и следующие элементы нельзя использовать в качестве отличительной функции при перегрузке свойства или процедуры:

- Модификаторы, такие как `ByVal` или `ByRef` , которые применяются к элементу или параметрам элемента.

- Имена параметров

- Типы возвращаемых процедур

`Overloads`Ключевое слово является необязательным при перегрузке, но если какой-либо перегруженный член использует `Overloads` ключевое слово, то все другие перегруженные члены с тем же именем также должны указывать это ключевое слово.

Производные классы могут перегружать унаследованные члены с элементами, которые имеют одинаковые параметры и типы параметров, процесс, называемый *теневым именем и сигнатурой*. Если `Overloads` ключевое слово используется при затенении по имени и сигнатуре, реализация члена в производном классе будет использоваться вместо реализации в базовом классе, а все другие перегрузки для этого члена будут доступны экземплярам производного класса.

Если `Overloads` ключевое слово пропущено при перегрузке унаследованного члена с членом, имеющим идентичные параметры и типы параметров, перегрузка называется *тенью по имени*. Затенение по имени заменяет унаследованную реализацию члена и делает все другие перегрузки недоступными для экземпляров производного класса и его децедентс.

`Overloads` `Shadows` Модификаторы и не могут использоваться одновременно с одним свойством или методом.

### <a name="example"></a>Пример

В следующем примере создаются перегруженные методы, которые принимают `String` или `Decimal` представление суммы в долларе и возвращают строку, содержащую налог на продажу.

#### <a name="to-use-this-example-to-create-an-overloaded-method"></a>Использование этого примера для создания перегруженного метода

1. Откройте новый проект и добавьте класс с именем `TaxClass` .

2. Добавьте в класс `TaxClass` приведенный далее код.

    [!code-vb[VbVbalrOOP#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#67)]

3. Добавьте следующую процедуру в форму.

    [!code-vb[VbVbalrOOP#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#68)]

4. Добавьте в форму кнопку и вызовите `ShowTax` процедуру из `Button1_Click` события кнопки.

5. Запустите проект и нажмите кнопку в форме, чтобы проверить перегруженную `ShowTax` процедуру.

Во время выполнения компилятор выбирает подходящую перегруженную функцию, которая соответствует используемым параметрам. При нажатии кнопки перегруженный метод вызывается первым с `Price` параметром, который является строкой, и сообщением «Price — это строка. Налог — $5,12 ". `TaxAmount`вызывается со `Decimal` значением второй раз и сообщением "Price является десятичным числом. Налог — $5,12 ".

## <a name="see-also"></a>См. также раздел

- [Объекты и классы](index.md)
- [Сокрытие в Visual Basic](../declared-elements/shadowing.md)
- [Оператор Sub](../../../language-reference/statements/sub-statement.md)
- [Основы наследования](inheritance-basics.md)
- [Shadows](../../../language-reference/modifiers/shadows.md)
- [ByVal](../../../language-reference/modifiers/byval.md)
- [ByRef](../../../language-reference/modifiers/byref.md)
- [Перегрузки](../../../language-reference/modifiers/overloads.md)
- [Shadows](../../../language-reference/modifiers/shadows.md)
