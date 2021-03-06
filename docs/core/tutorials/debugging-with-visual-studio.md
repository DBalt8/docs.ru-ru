---
title: Отладка консольного приложения .NET Core с помощью Visual Studio
description: Узнайте, как выполнить отладку консольного приложения .NET Core с помощью Visual Studio.
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 4e408d5bd0976d88f368615860ac373142d0fe1e
ms.sourcegitcommit: 60dc0a11ebdd77f969f41891d5cca06335cda6a7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88957229"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio"></a>Учебник. Отладка консольного приложения .NET Core с помощью Visual Studio

В этом руководстве представлены средства отладки, доступные в Visual Studio.

## <a name="prerequisites"></a>Предварительные требования

- В этом руководстве используется консольное приложение, созданное в руководстве [Создание консольного приложения .NET Core в Visual Studio](with-visual-studio.md).

## <a name="use-debug-build-configuration"></a>Использование конфигурации отладочной сборки

В Visual Studio используются две встроенные конфигурации сборки — *Отладка* и *Выпуск*. Вы воспользуетесь отладочной конфигурацией сборки для отладки и конфигурацией для выпуска для окончательного выпуска программы.

В отладочной конфигурации программы компилируется с полной символической отладочной информацией и без оптимизации. Оптимизация усложняет отладку, поскольку усложняется связь между исходным кодом и сгенерированными инструкциями. Конфигурация для выпуска полностью оптимизирована и не содержит символической отладочной информации.

 По умолчанию Visual Studio использует отладочную конфигурацию сборки, поэтому ее не нужно изменять перед отладкой.

1. Запустите Visual Studio.

1. Откройте проект, созданный по инструкциям из статьи [Создание консольного приложения .NET Core в Visual Studio](with-visual-studio.md).

   Используемая конфигурация сборки отображается на панели инструментов. На следующем изображении панели инструментов показано, что служба Visual Studio настроена для компиляции отладочной версии приложения:

   ![Панель инструментов Visual Studio с выделенным режимом отладки](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

## <a name="set-a-breakpoint"></a>Установка точки останова

*Точка останова* приостанавливает выполнение приложения на инструкции, предшествующей той строке, в которой установлена точка останова.

1. Установите *точку останова* в строке, где отображается имя, дата и время, щелкнув в левом поле окна изменения кода в этой строке. Левое поле находится слева от номеров строк.  Кроме того, установить точку останова можно, поместив курсор в строку кода и нажав клавишу <kbd>F9</kbd> или выбрав **Отладка** > **Переключить точку останова** в строке меню.

   Как видно на следующем рисунке, строку с точкой останова Visual Studio обозначает подсветкой текста и красной точкой в левом поле.

   ![Окно приложения Visual Studio с установленной точкой останова](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. Нажмите клавишу <kbd>F5</kbd>, чтобы запустить программу в режиме отладки. Еще один способ запуска отладки — выбрать в меню параметры **Отладка** > **Начать отладку**.

1. Когда программа запросит имя, введите любую строку в окне консоли и нажмите клавишу <kbd>ВВОД</kbd>.

1. Выполнение программы остановится, когда будет достигнута точка останова, то есть перед выполнением метода `Console.WriteLine`. В окне **Локальные** отображаются значения переменных, которые определены в текущем выполняемом методе.

   ![Снимок экрана с точкой останова в Visual Studio](./media/debugging-with-visual-studio/breakpoint-hit.png)

## <a name="use-the-immediate-window"></a>Использование окна "Интерпретация"

Окно **Интерпретация** позволяет взаимодействовать с приложением, которое вы отлаживаете. Вы можете интерактивно изменить значения переменных и посмотреть, как это повлияет на работу программы.

1. Если окно **Интерпретация** не отображается, откройте его, выбрав **Отладка** > **Окна** > **Интерпретация**.

1. Введите `name = "Gracie"` в окне **Интерпретация** и нажмите клавишу <kbd>ВВОД</kbd>.

1. Введите `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` в окне **Интерпретация** и нажмите клавишу <kbd>ВВОД</kbd>.

   В окне **Интерпретация** отображается значение переменной строки и свойства значения <xref:System.DateTime>. Кроме того, значения переменных обновляются в окне **Локальные**.

   ![Окна "Локальные" и "Интерпретация" в Visual Studio 2019](./media/debugging-with-visual-studio/locals-immediate-window.png)

1. Нажмите клавишу <kbd>F5</kbd>, чтобы продолжить выполнение программы. Или выберите **Отладка** > **Продолжить** в меню.

   Значения, отображаемые в окне консоли, соответствуют изменениям, произведенным в окне **Интерпретация**.

   ![Окно консоли с указанными значениями](./media/debugging-with-visual-studio/console-window.png)

1. Нажмите любую клавишу, чтобы выйти из приложения и остановить отладку.

## <a name="set-a-conditional-breakpoint"></a>Установка условной точки останова

Программа отображает строку, которую вводит пользователь. Что произойдет, если пользователь ничего не введет? Это можно проверить с помощью полезной функции отладки, которая называется *условной точкой останова*.

1. Щелкните правой кнопкой мыши красную точку, обозначающую точку останова. В контекстном меню выберите **Условия**. Откроется диалоговое окно **Параметры точки останова**. Установите флажок **Условия**, если он еще не установлен.

   ![Редактор с панелью параметров точки останова (C#)](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. Для **условного выражения** введите следующий код в поле, где приведен пример кода, который проверяет, имеет ли `x` значение 5. Если нужный язык не отображается, измените выбор языка в верхней части страницы.

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   ```vb
   String.IsNullOrEmpty(name)
   ```

   При каждом достижении точки останова отладчик вызывает метод `String.IsNullOrEmpty(name)` и останавливается на этой строке только в том случае, если вызов метода возвращает `true`.

   Вместо условного выражения можно указать *количество обращений* (выполнение программы будет прервано, пока инструкция не будет выполнена указанное количество раз) или *условие фильтра* (выполнение программы будет прервано на основе таких атрибутов, как идентификатор потока, имя процесса или имя потока).

1. Выберите **Закрыть**, чтобы закрыть диалоговое окно.

1. Запустите отладку программы, нажав клавишу <kbd>F5</kbd>.

1. Когда в окне консоли появится предложение ввести имя, просто нажмите клавишу <kbd>ВВОД</kbd>.

1. Так как указанное вами условие соблюдается (`name` имеет значение `null` или <xref:System.String.Empty?displayProperty=nameWithType>), выполнение программы будет остановлено при достижении точки останова, то есть перед выполнением метода `Console.WriteLine`.

1. Выберите окно **Локальные**, в котором отображаются значения локальных переменных для текущего выполняемого метода. В нашем примере этим методом является `Main`. Обратите внимание, что переменная `name` имеет значение `""` или <xref:System.String.Empty?displayProperty=nameWithType>.

1. Убедитесь в том, что переменная содержит пустую строку, введя следующую инструкцию в окне **Интерпретация** и нажав клавишу <kbd>ВВОД</kbd>. Результат равен `true`.

   ```csharp
   ? name == String.Empty
   ```

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

   Вопросительный знак указывает окну интерпретации на необходимость [вычислить выражение](/visualstudio/ide/reference/immediate-window#enter-commands).

   ![Значение true в окне интерпретации после выполнения инструкции (C#)](./media/debugging-with-visual-studio/immediate-window-output.png)

1. Нажмите клавишу <kbd>F5</kbd>, чтобы продолжить выполнение программы.

1. Нажмите любую клавишу, чтобы закрыть окно консоли и остановить отладку.

1. Очистите точку останова. Для этого щелкните красную точку в левом поле окна с кодом. Или нажмите клавишу <kbd>F9</kbd> либо выберите в меню пункт **Отладка > Перейти к следующей точке останова** при выбранной строке кода.

## <a name="step-through-a-program"></a>Пошаговое выполнение программы

Visual Studio позволяет выполнять программу пошагово, отслеживая результат ее выполнения. Для этого обычно задают точку останова и запускают программу в небольшой части ее кода. Поскольку наша программа невелика, давайте выполним ее пошагово.

1. Выберите **Отладка** > **Шаг с заходом**. Или выполните отладку по одному оператору, нажимая клавишу <kbd>F11</kbd>.

   Следующая выполняемая строка будет выделена, и рядом с ней появится стрелка.

   C#

   ![Метод выполнения по шагам в Visual Studio (C#)](./media/debugging-with-visual-studio/step-into-method.png)

   Visual Basic

   ![Метод выполнения по шагам в Visual Studio (Visual Basic)](./media/debugging-with-visual-studio/vb-step-into-method.png)

   На этом этапе в окне **Локальные** показано, что массив `args` пуст, а `name` и `date` имеют значения по умолчанию. Кроме того, Visual Studio открыла пустое окно консоли.

1. Нажмите клавишу <kbd>F11</kbd>. Будет выделена следующая выполняемая строка. Окно **Локальные** не изменяется, и окно консоли остается пустым.

   C#

   ![Источник метода выполнения по шагам в Visual Studio (C#)](./media/debugging-with-visual-studio/step-into-source-method.png)

   Visual Basic

   ![Источник метода выполнения по шагам в Visual Studio (Visual Basic)](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. Нажмите клавишу <kbd>F11</kbd>. Visual Studio подсвечивает инструкцию, которая содержит присваивание значения переменной `name`. В окне **Локальные** отображается, что `name` имеет значение `null`, а в окне консоли появилась строка What is your name? (Введите имя:).

1. Ответьте на этот запрос, введя строку в окно консоли и нажав клавишу <kbd>ВВОД</kbd>. Консоль никак не отреагирует на это, и введенная строка не будет отображаться в окне консоли, но метод <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> получит введенные входные данные.

1. Нажмите клавишу <kbd>F11</kbd>. Visual Studio подсвечивает оператор, который содержит присваивание значения переменной `date` (`currentDate` в Visual Basic). В окне **Локальные** отображается значение, полученное в результате вызова метода <xref:System.Console.ReadLine%2A?displayProperty=nameWithType>. В окне консоли также отображается строка, указанная в командной строке.

1. Нажмите клавишу <kbd>F11</kbd>. В окне **Локальные** отображается значение переменной `date`, которому было присвоено свойство <xref:System.DateTime.Now?displayProperty=nameWithType>. В окне консоли изменений не произошло.

1. Нажмите клавишу <kbd>F11</kbd>. Visual Studio вызывает метод <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType>. В окне консоли отображается форматированная строка.

1. Выберите **Отладка** > **Шаг с выходом**. Или отмените пошаговое выполнение, нажав сочетание клавиш <kbd>SHIFT</kbd>+<kbd>F11</kbd>.

   В окне консоли отображается сообщение с предложением нажать любую клавишу для выхода.

1. Нажмите любую клавишу, чтобы закрыть окно консоли и остановить отладку.

## <a name="use-release-build-configuration"></a>Использование конфигурации сборки для выпуска

После тестирования отладочной версии приложения следует скомпилировать и протестировать версию в режиме выпуска. При сборке в режиме выпуска компилятор использует методы оптимизации, которые иногда могут негативно повлиять на поведение приложения. Например, оптимизации компилятора для повышения производительности могут привести к состоянию конкуренции в многопоточных приложениях.

Чтобы собрать и протестировать консольное приложение в режиме выпуска, переключите конфигурацию сборки из режима **Отладка** в режим **Выпуск** на панели инструментов.

![Панель инструментов Visual Studio по умолчанию с выделенным режимом отладки](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

Если нажать клавишу <kbd>F5</kbd> или выбрать пункт **Собрать решение** в меню **Сборка**, Visual Studio скомпилирует версию приложения в режиме выпуска. Эту версию можно протестировать точно так же, как и отладочную.

## <a name="next-steps"></a>Следующие шаги

В этом руководстве вы использовали средства отладки Visual Studio. В следующем руководстве вы опубликуете развертываемую версию приложения.

> [!div class="nextstepaction"]
> [Публикация консольного приложения .NET Core с помощью Visual Studio](publishing-with-visual-studio.md)
