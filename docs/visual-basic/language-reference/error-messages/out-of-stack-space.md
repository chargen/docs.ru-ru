---
title: Отсутствует место в стеке (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: e39be5913fe877cf7b3396e4f13f4440288cb8f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="out-of-stack-space-visual-basic"></a>Отсутствует место в стеке (Visual Basic)
Стек — это рабочая область памяти, который увеличивается и уменьшается динамически с запросами большого количества выполняемой программы. Предел был превышен.  
  
## <a name="to-correct-this-error"></a>Исправление ошибки  
  
1.  Проверьте, что процедуры не вложены слишком глубоко.  
  
2.  Убедитесь, что рекурсивные процедуры завершаются должным образом.  
  
3.  Если для локальных переменных недостаточно места, чем доступно, объявите некоторые переменные на уровне модуля. Можно также объявить все переменные в процедуре статические, поставив в начале `Property`, `Sub`, или `Function` ключевого слова with `Static`. Или можно использовать `Static` инструкции для объявления в процедурах отдельных статических переменных.  
  
4.  Переопределите некоторые строки фиксированной длины как строки переменной длины, как строки фиксированной длины используют большее пространство стека, чем строки переменной длины. Можно также определить строку на уровне модуля, где требуется пространство стека.  
  
5.  Проверьте число вложенных `DoEvents` вызовы функций, с помощью `Calls` диалоговым окном просмотра процедур, активных в стеке.  
  
6.  Убедитесь, что не был запущен «Каскад событий» путем активации события, вызывающего процедуру уже в стеке. Каскад событий аналогичен незавершенный рекурсивный вызов процедуры, но он не заметен, поскольку вызов Visual Basic, а не явным вызовом в коде. Используйте `Calls` диалоговым окном просмотра процедур, активных в стеке.  
  
## <a name="see-also"></a>См. также  
 [Окно памяти](/visualstudio/debugger/memory-windows)
