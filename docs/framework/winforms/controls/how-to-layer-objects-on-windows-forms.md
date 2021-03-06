---
title: Практическое руководство. Многоуровневое расположение объектов в формах Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, layering
- controls [Windows Forms], layering
- z order
- controls [Windows Forms], positioning
- z-order
ms.assetid: 1acc4281-2976-4715-86f4-bda68134baaf
ms.openlocfilehash: 1a2a25f2e7eaa6618c0bf535a34f7dc6a28d51fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-layer-objects-on-windows-forms"></a>Практическое руководство. Многоуровневое расположение объектов в формах Windows Forms
При создании сложного пользовательского интерфейса, или работы с формой многодокументного интерфейса (MDI), часто необходимо расположить элементы управления и дочерние формы для создания более сложных пользовательского интерфейса (UI). Чтобы переместить и хранить список элементов управления и окна в контексте группы, управлять z порядком. *Z-порядок* является видимое расположение элементов управления на форме вдоль оси z формы (глубина). Окно, в верхней части z порядка перекрывает все остальные окна. Все остальные окна перекрывают окно в нижней части z порядка.  
  
> [!NOTE]
>  Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в статье [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-layer-controls-at-design-time"></a>Чтобы расположить элементы управления во время разработки  
  
1.  Выберите элемент управления, который необходимо расположить.  
  
2.  На **формат** последовательно выберите пункты **порядок**, а затем нажмите кнопку **на передний** или **на задний**.  
  
### <a name="to-layer-controls-programmatically"></a>Чтобы расположить элементы управления программным способом  
  
-   Используйте <xref:System.Windows.Forms.Control.BringToFront%2A> и <xref:System.Windows.Forms.Control.SendToBack%2A> методы для управления порядком элементов управления.  
  
     Например если <xref:System.Windows.Forms.TextBox> управления `txtFirstName`, находится под другим элементом управления и необходимо переместить его вверх, используйте следующий код:  
  
    ```vb  
    txtFirstName.BringToFront()  
    ```  
  
    ```csharp  
    txtFirstName.BringToFront();  
    ```  
  
    ```cpp  
    txtFirstName->BringToFront();  
    ```  
  
> [!NOTE]
>  Windows Forms поддерживает *вложении элементов управления*. Включение элементов управления заключается в размещении нескольких элементов управления внутри элемента управления, такие как ряд <xref:System.Windows.Forms.RadioButton> управления внутри <xref:System.Windows.Forms.GroupBox> элемента управления. Можно размещать элементы управления внутри содержащего элемента управления. Перемещение группы перемещает элементы управления, так как они находятся внутри него.  
  
## <a name="see-also"></a>См. также  
 [Элементы управления Windows Forms](../../../../docs/framework/winforms/controls/index.md)  
 [Упорядочение элементов управления в формах Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Создание меток и назначение сочетаний клавиш для элементов управления Windows Forms](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Элементы управления для использования в Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Функциональная классификация элементов управления Windows Forms](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
