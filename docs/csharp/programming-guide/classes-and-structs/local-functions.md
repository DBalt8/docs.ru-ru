---
title: Руководство по программированию на C#. Локальные функции
description: Локальные функции в C# — это частные методы, которые вложены в другой член и могут быть вызваны из их содержащего члена.
ms.date: 06/14/2017
helpviewer_keywords:
- local functions [C#]
ms.openlocfilehash: 854ec7ab4a4cc637c0a5ad03e0344d2f1f7679d2
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063306"
---
# <a name="local-functions-c-programming-guide"></a>Локальные функции (руководство по программированию на C#)

Начиная с версии 7.0 в языке C# поддерживаются *локальные функции*. Локальные функции представляют собой частные методы типа, вложенные в другой элемент. Они могут вызываться только из того элемента, в который вложены. Ниже перечислены элементы, в которых можно объявлять и из которых можно вызывать локальные функции:

- Методы, в частности методы итератора и асинхронные методы
- Конструкторы
- Методы доступа свойств
- Методы доступа событий
- Анонимные методы
- Лямбда-выражения
- Методы завершения
- Другие локальные функции

Тем не менее локальные функции нельзя объявлять внутри элемента, воплощающего выражение.

> [!NOTE]
> В некоторых случаях для реализации возможностей, поддерживаемых локальными функциями, также можно использовать лямбда-выражения. Дополнительные сведения см. в разделе [Локальные функции или лямбда-выражения](#local-functions-vs-lambda-expressions).

Применение локальных функций позволяет сделать предназначение кода более понятным. Другие пользователи, читающие ваш код, смогут видеть, что соответствующий метод вызывается только внутри того метода, в который он вложен. В случае с командными проектами это также гарантирует, что другой разработчик не сможет ошибочно вызвать метод напрямую из любого другого места в классе или структуре.

## <a name="local-function-syntax"></a>Синтаксис локальной функции

Локальная функция определяется как вложенный метод внутри содержащего ее элемента. Ниже приведен синтаксис определения локальной функции:

```csharp
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

Локальные функции могут использовать модификаторы [async](../../language-reference/keywords/async.md) и [unsafe](../../language-reference/keywords/unsafe.md).

Обратите внимание, что все локальные переменные, определенные в содержащем функцию элементе (включая параметры метода), доступны в локальной функции.

В отличие от определения метода, определение локальной функции не может содержать модификатор доступа к элементу. Поскольку все локальные функции являются частными, при использовании модификатора доступа (например, ключевого слова `private`) возникает ошибка компилятора CS0106, "Модификатор "private" недопустим для этого элемента".

> [!NOTE]
> В версиях C# ниже 8.0 локальные функции не могут содержать модификатор `static`. При использовании ключевого слова `static` возникает ошибка компилятора CS0106, "Модификатор "static" недопустим для этого элемента".

Кроме того, к локальной функции, а также ее параметрам и параметрам типа, нельзя применять атрибуты.

В следующем примере определяется локальная функция `AppendPathSeparator`, которая является частной для метода `GetText`:

[!code-csharp[LocalFunctionExample](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  

## <a name="local-functions-and-exceptions"></a>Локальные функции и исключения

Полезной особенностью локальных функций является то, что они допускают немедленную обработку исключений. В случае с итераторами метода исключения обрабатываются только после перечисления возвращаемой последовательности, а не в момент извлечения итератора. В случае с асинхронными методами любые исключения, возникшие в таком методе, наблюдаются в тот момент, когда возвращаемая задача находится в состоянии ожидания.

В следующем примере определяется метод `OddSequence`, который перечисляет нечетные числа в заданном диапазоне. Поскольку он передает в метод перечислителя `OddSequence` число больше 100, этот метод вызывает исключение <xref:System.ArgumentOutOfRangeException>. Как видно из выходных данных этого примера, исключение обрабатывается только в момент перебора чисел, а не при извлечении перечислителя.

[!code-csharp[LocalFunctionIterator1](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)]

Вместо этого исключение может быть вызвано при выполнении проверки до того, как будет извлечен итератор, путем возврата итератора из локальной функции, как показано в следующем примере.

[!code-csharp[LocalFunctionIterator2](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

Локальные функции можно использовать аналогичным образом для обработки исключений вне асинхронной операции. Как правило, при возникновении исключения в асинхронном методе требуется проверить внутренние исключения в <xref:System.AggregateException>. Локальная функция реализует моментальный сбой кода, синхронно обеспечивая вызов исключения и наблюдение за ним.

В следующем примере асинхронный метод `GetMultipleAsync` выполняет приостановку на указанное число секунд, возвращая значение, представляющее собой произведение случайного множителя на это число секунд. Максимальная задержка составляет 5 с. Результат <xref:System.ArgumentOutOfRangeException> возвращается в том случае, если значение больше 5. Как видно из следующего примера, исключение, которое возникает при передаче в метод `GetMultipleAsync` значения 6, инкапсулируется в <xref:System.AggregateException> после того, как начинается выполнение метода `GetMultipleAsync`.

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)]

Как и в случае с итератором метода, можно выполнить рефакторинг кода из этого примера таким образом, чтобы реализовать проверку перед вызовом асинхронного метода. Как видно из результатов следующего примера, <xref:System.ArgumentOutOfRangeException> не инкапсулируется в <xref:System.AggregateException>.

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)]

## <a name="local-functions-vs-lambda-expressions"></a>Локальные функции или лямбда-выражения

На первый взгляд, локальные функции и [лямбда-выражения](../../language-reference/operators/lambda-expressions.md) во многом похожи. Во многих случаях выбор между использованием лямбда-выражений и локальных функций определяется стилем и личными предпочтениями. Однако существуют реальные различия в использовании этих сущностей, о которых нужно знать.

Рассмотрим различия в реализации алгоритма вычисления факториала с использованием локальной функции и лямбда-выражения. В первой версии используется локальная функция:

[!code-csharp[LocalFunctionFactorial](../../../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Recursive factorial using local function")]

Сравните эту реализацию с версией, в которой используются лямбда-выражения:

[!code-csharp[26_LambdaFactorial](../../../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Recursive factorial using lambda expressions")]

Локальные функции имеют имена. Лямбда-выражения — это анонимные методы, назначаемые переменным типов `Func` или `Action`. При объявлении локальной функции типы аргументов и тип возвращаемого значения являются частью объявления функции. Типы аргументов и тип возвращаемого значения не являются частью основной части лямбда-выражения — это часть объявления типа переменной лямбда-выражения. Знание этих двух различий поможет в создании более понятного кода.

Правила определенного назначения у локальных функций и лямбда-выражений различаются. На объявление локальной функции можно сослаться из любого расположения кода, находящегося в области охвата. Прежде чем к лямбда-выражению можно будет осуществлять доступ, необходимо присвоить его переменной-делегату (или вызвать через делегат, ссылающийся на лямбда-выражение). Обратите внимание на то, что версия с использованием лямбда-выражения должна объявить и инициализировать лямбда-выражение `nthFactorial`, прежде чем его определить. В противном случае возникает ошибка компилятора, связанная со ссылкой на объект `nthFactorial`, который еще не был назначен. Эти различия означают, что рекурсивные алгоритмы легче создавать, используя локальные функции. Можно объявить и определить локальную функцию, которая вызывает саму себя. Необходимо объявить лямбда-выражения и назначить им значение по умолчанию, прежде чем их можно будет переназначить телу, которое ссылается на то же лямбда-выражение.

Правила определенного назначения также влияют на любые переменные, собранные локальной функцией или лямбда-выражением. Локальные функции и правила лямбда-выражений требуют, чтобы любые захваченные переменные были определенно назначены в точке, где локальная функция или лямбда-выражение преобразуется в делегат. Разница в том, что лямбда-выражения преобразуются в делегаты при объявлении. Локальные функции преобразуются в делегаты только при использовании в качестве делегата. Если объявить локальную функцию и сослаться на нее только путем вызова этой функции в качестве метода, она не будет преобразована в делегат. Это правило позволяет объявлять локальную функцию в любом удобном расположении во включающей его области. Обычно локальные функции объявляют в конце родительского метода, после всех операторов return.

В-третьих, компилятор может выполнять статический анализ, что позволяет локальным функциям определенно назначать захваченные переменные во включающей области. Рассмотрим следующий пример.

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

Компилятор может определить, что `LocalFunction` определенно назначает `y` при вызове. Поскольку `LocalFunction` вызывается перед оператором `return`, `y` определенно назначается в операторе `return`.

Анализ, позволяющий выполнить анализ примера, также иллюстрирует четвертое различие. В зависимости от использования при работе с локальными функциями можно избежать распределения куч, которое всегда необходимо выполнять при работе с лямбда-выражениями. Если локальная функция никогда не преобразуется в делегат и ни одна из переменных, захваченных локальной функцией, не захвачена другими лямбда-выражениями или локальными функциями, которые преобразуются в делегаты, компилятор может избежать распределения куч.

Рассмотрим следующий асинхронный пример:

[!code-csharp[TaskLambdaExample](../../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Task returning method with lambda expression")]

Замыкание для этого лямбда-выражения содержит переменные `address`, `index` и `name`. При использовании локальных функций объект, который реализует замыкание, может иметь тип `struct`. Этот тип структуры будет передан в локальную функцию посредством ссылки. Эта разница в реализации позволяет избежать распределения.

Создание экземпляра, необходимое для лямбда-выражений, означает выделение дополнительной памяти, что в критически важном коде может ухудшить производительность. Локальные функции не создают этой перегрузки. В приведенном выше примере в версии с локальной функцией используется на 2 меньше операции выделения памяти по сравнению с версией на основе лямбда-выражения.

> [!NOTE]
> В эквивалентном этому методе на основе локальной функции также используется класс для замыкания. Реализация замыкания для локальной функции в формате `class` или `struct` зависит от особенностей реализации. Локальная функция может использовать `struct`, тогда как в лямбда-выражениях всегда используется `class`.

[!code-csharp[TaskLocalFunctionExample](../../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

Еще одно преимущество локальных функций, которое не показано в этом примере, заключается в том, что они могут быть реализованы в качестве итераторов с использованием синтаксиса `yield return` для создания последовательности значений. В лямбда-выражениях не допускается использование оператора `yield return`.

Локальные функции могут показаться избыточными для лямбда-выражений, поскольку обычно применяются иначе и в других целях. Локальные функции более эффективны в случаях, когда вам нужно написать функцию, которая будет вызываться только из контекста другого метода.

## <a name="see-also"></a>См. также

- [Методы](methods.md)
