---
title: Regsvcs.exe (программа установки служб .NET)
description: Сведения об использовании программы установки служб .NET (Regsvcs.exe), позволяющей загрузить и зарегистрировать сборку, настроить службы, программно добавленные в класс, и выполнять другие действия.
ms.date: 03/30/2017
helpviewer_keywords:
- Regsvcs.exe
- .NET Services Installation tool
- loading assemblies
- assemblies [.NET Framework], registering
- type libraries
- registering assemblies
ms.assetid: 5220fe58-5aaf-4e8e-8bc3-b78c63025804
ms.openlocfilehash: 6d0090eda764113407e35a3bcec139f1c7cfb050
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517247"
---
# <a name="regsvcsexe-net-services-installation-tool"></a>Regsvcs.exe (программа установки служб .NET)
Программа установки служб .NET выполняет следующие действия.  
  
- Загружает и регистрирует сборку.  
  
- Создает, регистрирует и устанавливает библиотеку типов в указанное приложение COM+.  
  
- Настраивает службы, которые были программно добавлены в создаваемый класс.  
  
 Чтобы применить этот инструмент, воспользуйтесь командной строкой разработчика для Visual Studio (или командной строкой Visual Studio в Windows 7). Дополнительные сведения см. в разделе [Командные строки](developer-command-prompt-for-vs.md).  
  
 В командной строке введите следующее.  
  
## <a name="syntax"></a>Синтаксис  
  
```console  
      regsvcs [/c | /fc | /u] [/tlb:typeLibraryFile] [/extlb]  
[/reconfig] [/componly] [/appname:applicationName]  
[/nologo] [/quiet]assemblyFile.dll
```  
  
## <a name="parameters"></a>Параметры  
  
|Аргумент|Описание|  
|--------------|-----------------|  
|*assemblyFile.dll*|Исходный файл сборки. Сборка должна быть подписана с использованием строгого имени. Дополнительные сведения см. в разделе [Подпись сборки строгим именем](../../standard/assembly/sign-strong-name.md).|  
  
|Параметр|Описание:|  
|------------|-----------------|  
|**/appdir:** *path*|Определяет корневой каталог приложения.|  
|**/appname:** *applicationName*|Задает имя приложения COM+, которое следует найти или создать.|  
|**/c**|Создает конечное приложение.|  
|**/componly**|Выполняет только конфигурирование компонентов, методы и интерфейсы игнорируются.|  
|**/exapp**|Указывает, что программа будет работать с существующим приложением.|  
|**/extlb**|Использует существующую библиотеку типов.|  
|**/fc**|Находит или создает конечное приложение.|  
|**/help**|Отображает синтаксис команд и параметров программы.|  
|**/noreconfig**|Запрещает изменять конфигурации существующего конечного приложения.|  
|**/nologo**|Отключает отображение эмблемы Майкрософт при запуске.|  
|**/parname:** *name*|Задает имя или идентификатор приложения COM+, которое следует найти или создать.|  
|**/reconfig**|Изменяет конфигурацию существующего конечного приложения. Это значение по умолчанию.|  
|**/tlb:** *typelibraryfile*|Задает устанавливаемый файл библиотеки типов.|  
|**/u**|Удаляет конечное приложение.|  
|**/quiet**|Задает тихий режим, логотип и сообщения об успешном завершении операций не отображаются.|  
|**/?**|Отображает синтаксис команд и параметров программы.|  
  
## <a name="remarks"></a>Примечания  
 Программе Regsvcs.exe требуется исходный файл сборки, заданный библиотекой *assemblyFile.dll*. Эта сборка должна быть подписана с использованием строгого имени. Дополнительные сведения о подписи с использованием строгого имени см. в разделе [Подпись сборки строгим именем](../../standard/assembly/sign-strong-name.md). Имена конечного приложения и файла библиотеки типов не являются обязательными. Аргумент *applicationName* может быть создан из исходного файла сборки, и в случае его отсутствия он будет создан программой Regsvcs.exe. Аргумент *typelibraryfile* может задавать имя библиотеки типов. Если имя библиотеки типов не указано, программа Regsvcs.exe по умолчанию использует имя сборки.  
  
 Когда программа Regsvcs.exe регистрирует методы компонента, к ней применяются [требования](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) и [требования ссылки](../misc/link-demands.md) для этих методов. Поскольку эта программа выполняется в полностью доверенной среде, большинство требований на получение разрешения удовлетворяется. Однако программа Regsvcs.exe не может регистрировать компоненты с помощью методов, защищенных требованием или требованием связи для <xref:System.Security.Permissions.StrongNameIdentityPermission> или <xref:System.Security.Permissions.PublisherIdentityPermission>.  
  
 Для работы с программой Regsvcs.exe требуются права администратора на локальном компьютере.  
  
 Если программа Regsvcs.exe не может выполнить какие-либо из этих действий, на экран выводится соответствующее сообщение об ошибке.  
  
## <a name="examples"></a>Примеры  
 Следующая команда добавляет все открытые классы, содержащиеся в `myTest.dll`, в `myTargetApp` (существующее приложение COM+) и создает библиотеку типов `myTest.tlb`.  
  
```console  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 Следующая команда добавляет все открытые классы, содержащиеся в `myTest.dll`, в `myTargetApp` (существующее приложение COM+) и создает библиотеку типов `newTest.tlb`.  
  
```console  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a>См. также

- [Инструменты](index.md)
- [Практическое руководство. Подписание сборки строгим именем](../../standard/assembly/sign-strong-name.md)
- [Командные строки](developer-command-prompt-for-vs.md)
