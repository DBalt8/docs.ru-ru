---
title: Анализ строк в .NET
description: Общие сведения об анализе строк в .NET. Операция анализа преобразует строку, представляющую базовый тип .NET, в этот базовый тип. Анализ является операцией, обратной форматированию.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
ms.openlocfilehash: 5e297c8f689fdabc268ee6e269a7969155befe7b
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769292"
---
# <a name="parsing-strings-in-net"></a>Анализ строк в .NET
Операция синтаксического анализа преобразует строку, представляющую базовый тип .NET, в этот базовый тип. Например, операция синтаксического анализа используется для преобразования строки в число с плавающей запятой или в значение даты и времени. Чаще всего для выполнения операции синтаксического разбора используется метод `Parse`. Поскольку разбор — это операция, обратная форматированию (которое подразумевает преобразование базового типа в строковое представление), то применимы многие схожие правила и условия. Подобно тому, как при форматировании используется объект, реализующий интерфейс <xref:System.IFormatProvider> для предоставления зависящей от языка и региональных параметров информации форматирования, точно так же и при синтаксическом разборе используется объект, реализующий интерфейс <xref:System.IFormatProvider>, чтобы определить, как интерпретировать строковое представление. Дополнительные сведения см. в статье [Типы форматирования в .NET](formatting-types.md).  
  
## <a name="in-this-section"></a>В этом разделе  
 [Анализ числовых строк](parsing-numeric.md)  
 Описание преобразования строк в числовые типы .NET.  
  
 [Анализ строк даты и времени](parsing-datetime.md)  
 Описание преобразования строк в типы **даты и времени** .NET.  
  
 [Анализ других строк](parsing-other.md)  
 Описание преобразования строк в типы **Char**, **Boolean** и **Enum**.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Типы форматирования](formatting-types.md)  
 Описание базовых концепций форматирования, таких как описатели формата и поставщики формата.  
  
 [Преобразование типов в .NET](type-conversion.md)  
 Описание процесса преобразования типов.
