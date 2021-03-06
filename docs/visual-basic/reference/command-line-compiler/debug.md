---
title: /debug (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- debug compiler switches
- /debug compiler option [Visual Basic]
- -debug compiler option [Visual Basic]
- debug compiler option [Visual Basic]
ms.assetid: c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18d74b8f0a7b319e08780a8db9175c7be16d932e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="-debug-visual-basic"></a>-debug (Visual Basic)
Указывает компилятору создавать отладочную информацию и поместить ее в выходных файлах.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-debug[+ | -]  
' -or-  
-debug:[full | pdbonly]  
```  
  
## <a name="arguments"></a>Аргументы  
  
|Термин|Определение|  
|---|---|  
|`+` &#124; `-`|Необязательный. Указание `+` или `/debug` указывает компилятору создавать отладочную информацию и поместить ее в PDB-файл. Указание `-` имеет тот же эффект, что и при указании не `/debug`.|  
|`full` &#124; `pdbonly`|Необязательный. Определяет тип отладочной информации, создаваемой компилятором. Если вы не укажете `/debug:pdbonly`, значение по умолчанию — `full`, что позволяет присоединить отладчик к выполняющейся программе. `pdbonly` Аргумент позволяет выполнить отладку исходного кода при запуске программы в отладчике, но только в том случае, когда исполняемой программы в отладчике отображается кода на языке ассемблера.|  
  
## <a name="remarks"></a>Примечания  
 Используйте этот параметр для создания отладочных сборок. Если вы не укажете `/debug`, `/debug+`, или `/debug:full`, нельзя отладить выходной файл программы.  
  
 По умолчанию отладочная информация не создается (`/debug-`). Для получения отладочной информации, укажите `/debug` или `/debug+`.  
  
 Сведения о настройке производительности отладки для приложения см. в разделе [Упрощение отладки образов](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md).  
  
|Чтобы задать — отладку в среде разработки Visual Studio|  
|---|  
|1.  Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**. <br />2.  Откройте вкладку **Компиляция**.<br />3.  Щелкните **Дополнительные параметры компиляции**.<br />4.  Измените значение в **создать отладочную информацию** поле.|  
  
## <a name="example"></a>Пример  
 Следующий пример демонстрирует размещение отладочной информации в выходной файл `App.exe`.  
  
```  
vbc -debug -out:app.exe test.vb  
```  
  
## <a name="see-also"></a>См. также  
 [Компилятор Visual Basic с интерфейсом командной строки](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)  
 [Примеры командных строк компиляции](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
