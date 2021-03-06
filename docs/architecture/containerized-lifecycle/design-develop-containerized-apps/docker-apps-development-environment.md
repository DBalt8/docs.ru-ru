---
title: Среда разработки приложений Docker
description: Ознакомьтесь с наиболее важными средствами разработки, поддерживающими жизненный цикл разработки Docker.
ms.date: 08/06/2020
ms.openlocfilehash: 07b42b2bd05ab16ba0fbf61863b050ee2c9e242b
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916036"
---
# <a name="development-environment-for-docker-apps"></a>Среда разработки приложений Docker

## <a name="development-tools-choices-ide-or-editor"></a>Выбор средств разработки: интегрированная среда разработки или редактор

Предпочитаете ли вы использовать полнофункциональную среду IDE или упрощенный редактор, корпорация Майкрософт предлагает вам удобное решение для разработки приложений Docker.

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a>Visual Studio Code и CLI Docker (кроссплатформенные средства для Mac, Linux и Windows)

Если вам нужен упрощенный кроссплатформенный редактор, поддерживающий любой язык программирования, вы можете использовать Visual Studio Code и CLI Docker. Эти решения обеспечивают простой, но в то же время эффективный рабочий процесс разработки. Установив Docker для Mac или Docker для Windows (среду разработки), разработчики приложений Docker могут использовать единый интерфейс CLI Docker (среду выполнения), чтобы создавать приложения как для Windows, так и для Linux. Кроме того, Visual Studio Code поддерживает расширения для Docker с IntelliSense для файлов Dockerfile и ярлыками для выполнения команд Docker из редактора.

> [!NOTE]
> Чтобы скачать Visual Studio Code, перейдите на страницу <https://code.visualstudio.com/download>.
>
> Чтобы скачать Docker для Mac и Windows, перейдите на страницу <https://www.docker.com/products/docker>.

### <a name="visual-studio-with-docker-tools-windows-development-machine"></a>Visual Studio со средствами Docker (компьютер Windows для разработки)

Рекомендуется использовать Visual Studio 2019 с включенными встроенными средствами Docker. С помощью Visual Studio вы можете разрабатывать, запускать и проверять приложения непосредственно в выбранной среде Docker. Нажмите клавишу F5 для отладки приложения (на основе одного контейнера или нескольких) непосредственно в узле Docker или клавиши CTRL+F5 для редактирования и обновления приложения без повторной сборки контейнера. Это самый простой и эффективный способ разработки в Windows контейнеров Docker для Linux или Windows.

### <a name="visual-studio-for-mac-mac-development-machine"></a>Visual Studio для Mac (компьютер Mac для разработки)

При разработке приложений на основе Docker можно использовать [Visual Studio для Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link). Visual Studio для Mac — это интегрированная среда разработки с более широкими возможностями по сравнению с Visual Studio Code для Mac.

## <a name="language-and-framework-choices"></a>Языки и платформы

С помощью средств Майкрософт вы можете разрабатывать приложения Docker на самых современных языках. Вот лишь часть их списка:

- .NET Core и ASP.NET Core
- Node.js
- Go
- Java
- Ruby
- Python

По сути, можно использовать любой современный язык, поддерживаемый Docker в Linux или Windows.

>[!div class="step-by-step"]
>[Назад](deploy-azure-kubernetes-service.md)
>[Вперед](docker-apps-inner-loop-workflow.md)
