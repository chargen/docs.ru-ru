---
title: Общие сведения об элементе управления StatusBar (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
ms.openlocfilehash: 6dd5b45b38ec4fb04d9a53a1648cfe6e5a5b9f20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="statusbar-control-overview-windows-forms"></a>Общие сведения об элементе управления StatusBar (Windows Forms)
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip> И <xref:System.Windows.Forms.ToolStripStatusLabel> заменить элементы управления и добавить функциональные возможности в <xref:System.Windows.Forms.StatusBar> и <xref:System.Windows.Forms.StatusBarPanel> управляет; Однако <xref:System.Windows.Forms.StatusBar> и <xref:System.Windows.Forms.StatusBarPanel> элементы управления можно сохранить для обратной совместимости и использования в будущем, если вы Выберите этот параметр.  
  
 Windows Forms [управления StatusBar](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) используется в формах в качестве области, обычно отображаемой в нижней части окна, в которой выводятся различные сведения о состоянии приложения. <xref:System.Windows.Forms.StatusBar> элементы управления могут включать панели строки состояния на них, отображающие текст или значки, показывающие состояние, или набор значков в анимации, указывающие, что процесс работает; например [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] означает, что при сохранении документа.  
  
## <a name="using-the-statusbar-control"></a>С помощью элемента управления StatusBar  
 Строка состояния Internet Explorer используется для указания URL-адрес страницы, при наведении указателя мыши на гиперссылку; [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] представлены сведения о расположении страницы, расположение раздела и режимах редактирования, такие как Visual Studio и замены текста и отслеживание изменений; строка состояния используется для предоставления контекстных сведений, таких как закрепляемыми окнами как закрепленного или с плавающей запятой.  
  
 Можно отобразить одно сообщение в строке состояния, задав <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> свойства `false` (по умолчанию) и параметр <xref:System.Windows.Forms.StatusBar.Text%2A> свойство строки состояния, применяемый к тексту, который будет отображаться в строке состояния. В строке состояния можно разделить на панелей для отображения более чем один тип данных, задав <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> свойства `true` и с помощью <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> метод <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.  
  
## <a name="see-also"></a>См. также  
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [Практическое руководство. Идентификация панели элемента управления StatusBar, которую щелкнул пользователь, в Windows Forms](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)
