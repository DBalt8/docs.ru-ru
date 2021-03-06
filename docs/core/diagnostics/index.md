---
title: Общие сведения о средствах диагностики в .NET Core
description: Общие сведения о средствах и методах диагностики приложений .NET Core.
ms.date: 07/16/2020
ms.topic: overview
ms.openlocfilehash: ae3b9a1961f331c9cdea786bd5fe06b7bfa10927
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558118"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a>Общие сведения о средствах диагностики в .NET Core

Программное обеспечение не всегда работает должным образом, но в .NET Core есть средства и API, которые помогут вам быстро и эффективно диагностировать проблемы.

Эта статья поможет вам выбрать нужные средства.

## <a name="managed-debuggers"></a>Управляемые отладчики

[Управляемые отладчики](managed-debuggers.md) позволяют взаимодействовать с программой. Такие операции, как приостановка, инкрементное выполнение, анализ и возобновление, предоставляют сведения о поведении кода. Отладчик — это самое подходящее средство для диагностики функциональных проблем, которые можно легко воспроизвести.

## <a name="logging-and-tracing"></a>Ведение журнала и трассировка

[Ведение журнала и трассировка](logging-tracing.md) — это связанные методы, предназначенные для инструментирования кода и создания файлов журнала. В файлах записываются сведения о том, что делает программа. Эти сведения можно использовать для диагностики самых сложных проблем. В сочетании с метками времени эти методы также используются для выявления проблем с производительностью.

## <a name="unit-testing"></a>Модульное тестирование

[Модульное тестирование](../testing/index.md) — это ключевой компонент непрерывной интеграции и развертывания высококачественного программного обеспечения. Модульные тесты позволяют сразу же узнать о возникшей проблеме.

## <a name="net-core-dotnet-diagnostic-global-tools"></a>Глобальные средства диагностики dotnet в .NET Core

### <a name="dotnet-counters"></a>dotnet-counters

[dotnet-counters](dotnet-counters.md) — это средство мониторинга производительности для первого уровня мониторинга работоспособности и анализа производительности. Оно отслеживает значения счетчиков производительности, опубликованные с помощью API <xref:System.Diagnostics.Tracing.EventCounter>. Например, можно быстро отслеживать использование ЦП или частоту возникновения исключений в приложении .NET Core.

### <a name="dotnet-dump"></a>dotnet-dump

[dotnet-dump](dotnet-dump.md) — это средство сбора и анализа дампов ядра Windows и Linux без собственного отладчика.

### <a name="dotnet-gcdump"></a>dotnet-gcdump

Средство [dotnet-gcdump](dotnet-gcdump.md) предоставляет способ сбора дампов сборщика мусора (GC) для активных процессов .NET.

### <a name="dotnet-trace"></a>dotnet-trace

.NET Core включает в себя `EventPipe`, с помощью которого предоставляются диагностические данные. Средство [dotnet-trace](dotnet-trace.md) позволяет использовать интересные данные профилирования из приложения, которые могут помочь в сценариях, когда вам нужно найти причину медленной работы приложений.

## <a name="net-core-diagnostics-tutorials"></a>Учебники по диагностике .NET Core

### <a name="debug-a-memory-leak"></a>Отладка утечек памяти

[Учебник. Отладка утечек памяти](debug-memory-leak.md) содержит пошаговые инструкции по поиску утечек памяти. Средство [dotnet-counters](dotnet-counters.md) позволяет подтвердить наличие утечки, а средство [dotnet-dump](dotnet-dump.md) используется для ее диагностики.

### <a name="debug-high-cpu-usage"></a>Отладка высокой загрузки ЦП

В [руководстве по отладке высокой загрузки ЦП](debug-highcpu.md) приводятся пошаговые инструкции по изучению высокой загрузки ЦП. Для подтверждения высокой загрузки ЦП используется средство [dotnet-counters](dotnet-counters.md). Затем вы узнаете, как использовать [служебную программу трассировки для анализа производительности (`dotnet-trace`)](dotnet-trace.md) или `perf` для Linux, чтобы получить и просмотреть профиль загрузки ЦП.

### <a name="debug-deadlock"></a>Отладка взаимоблокировки

В [руководстве по отладке взаимоблокировки](debug-deadlock.md) показано, как использовать средство [dotnet-dump](dotnet-dump.md) для изучения потоков и блокировок.
