---
title: Практическое руководство. Проверка строк, представляющих дату или время
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: 5d153ac29039375386b3cd5f03609b1e4bd1d5bf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410571"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a>Практическое руководство. Проверка строк, представляющих дату или время (Visual Basic)
В следующем примере кода задается `Boolean` значение, указывающее, представляет ли строка допустимую дату или время.  
  
## <a name="example"></a>Пример  
 [!code-vb[VbVbcnRegEx#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#2)]  
  
## <a name="compile-the-code"></a>Компиляция кода  
 Замените `("01/01/03")` и `"9:30 PM"` датой и временем, которые необходимо проверить. Строку можно заменить другой жестко запрограммированной строкой, `String` переменной или методом, возвращающим строку, например `InputBox` .  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 Используйте этот метод для проверки строки перед попыткой преобразования в `String` `DateTime` переменную. При проверке даты или времени сначала можно избежать создания исключения во время выполнения.  
  
## <a name="see-also"></a>См. также раздел

- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [Проверка строк в Visual Basic](validating-strings.md)
