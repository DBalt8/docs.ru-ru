---
title: Документирование кода с помощью XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
ms.openlocfilehash: f391fb909cfe4de8f27afb24d6db389e2c8cdfae
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590933"
---
# <a name="document-your-code-with-xml-visual-basic"></a>Документирование кода с помощью XML (Visual Basic)

В Visual Basic можно документировать код с помощью XML.

## <a name="xml-documentation-comments"></a>Комментарии XML-документации

Visual Basic предоставляет простой способ автоматического создания XML-документации для проектов. Можно автоматически создать XML-схему для типов и членов, а затем предоставить сводные данные, описательную документацию для каждого параметра и другие замечания. При соответствующей настройке XML-документация автоматически создается в XML-файл с тем же корневым именем файла, что и у проекта. Дополнительные сведения см. в разделе [-doc](../../reference/command-line-compiler/doc.md).

XML-файл можно использовать или иным образом манипулировать как XML. Этот файл находится в том же каталоге, что и файл Output. exe или. DLL проекта.

Документация по XML начинается с `'''` . Обработка этих комментариев имеет некоторые ограничения.

- Документация должна представлять собой XML с правильным форматом. Если XML сформирован неправильно, создается предупреждение, а файл документации содержит комментарий, в котором говорится, что обнаружена ошибка.

- Разработчики могут создавать собственные наборы тегов. Существует рекомендуемый набор тегов (см. раздел [теги комментариев XML](../../language-reference/xmldoc/index.md)). Некоторые рекомендуемые теги имеют особые значения.

  - \<param>Тег используется для описания параметров. При использовании этого тега компилятор проверяет, что параметр существует и все параметры описаны в документации. Если проверка завершается неудачно, компилятор выдает предупреждение.

  - Атрибут `cref` может быть присоединен к любому тегу для предоставления ссылки на элемент кода. Компилятор проверяет наличие этого элемента кода. Если проверка завершается неудачно, компилятор выдает предупреждение. Компилятор также учитывает любые `Imports` инструкции при поиске типа, описанного в `cref` атрибуте.

  - Этот \<summary> тег используется технологией IntelliSense в Visual Studio для отображения дополнительных сведений о типе или члене.

## <a name="related-sections"></a>Связанные разделы

Дополнительные сведения о создании XML-файла с комментариями к документации см. в следующих разделах:

- [-doc](../../reference/command-line-compiler/doc.md)

- [XML-теги для комментариев](../../language-reference/xmldoc/index.md)

- [Обработка XML-файла](processing-the-xml-file.md)

- [Практическое руководство. Создание XML-документации](how-to-create-xml-documentation.md)

- [Средства XML в Visual Studio](/visualstudio/xml-tools/xml-tools-in-visual-studio)

## <a name="see-also"></a>См. также раздел

- [Разработка приложений в Visual Basic](../../developing-apps/index.md)
- [Руководство по программированию на Visual Basic](../index.md)
