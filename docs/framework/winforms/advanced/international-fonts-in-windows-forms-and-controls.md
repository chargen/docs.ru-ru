---
title: Международные шрифты в Windows Forms и элементах управления Windows
ms.date: 03/30/2017
helpviewer_keywords:
- fonts [Windows Forms], international
- international applications [Windows Forms], character display
- fonts [Windows Forms], globalization considerations
- localization [Windows Forms], fonts
- Windows Forms controls, labels
- font fallback in Windows Forms
- globalization [Windows Forms], character sets
ms.assetid: 2c3066df-9bac-479a-82b2-79e484b346a3
ms.openlocfilehash: 38a6928dfb548c6b514b598dbebe5bbc62d2e3f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="international-fonts-in-windows-forms-and-controls"></a>Международные шрифты в Windows Forms и элементах управления Windows
В приложениях на разных языках выбора шрифтов рекомендуется использовать откат шрифта везде, где это возможно. Это означает система определяет, что скрипт символ принадлежит.  
  
## <a name="using-font-fallback"></a>Применение подмены шрифта  
 Чтобы воспользоваться этой функцией, не устанавливайте <xref:System.Drawing.Font> свойство формы или любого другого элемента. Приложение будет автоматически использовать системный шрифт по умолчанию, отличающийся от языка локализованной операционной системы в другую. При запуске приложения, система автоматически выбирает правильный шрифт для языка и региональных параметров, выбранных в операционной системе.  
  
 Существует исключение из правила не задавать шрифт, начертание шрифта изменением. Это может оказаться важным для приложения, в котором пользователь нажимает кнопку для отображения текста в текстовом поле был выделен полужирным шрифтом. Чтобы сделать это, вы пишете функции для изменения стиля шрифта текстовое поле, будут выводиться полужирным шрифтом, зависимости от того, независимо от шрифта формы. Очень важно, чтобы эта функция вызывается в двух местах: в кнопке <xref:System.Windows.Forms.Control.Click> обработчик событий и в <xref:System.Windows.Forms.Control.FontChanged> обработчика событий. Если функция вызывается только в <xref:System.Windows.Forms.Control.Click> обработчик событий и другие части кода изменяет семейства шрифтов для всей формы, текстовое поле не изменится с остальной частью формы.  
  
```  
' Visual Basic  
Private Sub MakeBold()  
   ' Change the TextBox to a bold version of the form font  
   TextBox1.Font = New Font(Me.Font, FontStyle.Bold)  
End Sub  
  
Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
   ' Clicking this button makes the TextBox bold  
   MakeBold()  
End Sub  
  
Private Sub Form1_FontChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles MyBase.FontChanged  
   ' If the TextBox is already bold and the form's font changes,  
   ' change the TextBox to a bold version of the new form font  
   If (TextBox1.Font.Style = FontStyle.Bold) Then  
      MakeBold()  
   End If  
End Sub  
  
// C#  
private void button1_Click(object sender, System.EventArgs e)  
{  
   // Clicking this button makes the TextBox bold  
   MakeBold();  
}  
  
private void MakeBold()   
{  
   // Change the TextBox to a bold version of the form's font  
   textBox1.Font = new Font(this.Font, FontStyle.Bold);  
}  
  
private void Form1_FontChanged(object sender, System.EventArgs e)  
{  
   // If the TextBox is already bold and the form's font changes,  
   // change the TextBox to a bold version of the new form font  
   if (textBox1.Font.Style == FontStyle.Bold)   
   {  
      MakeBold();  
   }  
}  
```  
  
 Тем не менее при локализации приложения полужирный шрифт могут отображаться неправильно для определенных языков. Если это критично, то локализаторам иметь возможность переключения шрифта с жирного шрифта на обычный текст. Поскольку локализаторам обычно не являются разработчиками и не имеют доступа к исходному коду, только с файлами ресурсов, этот параметр необходимо задать в файлах ресурсов. Чтобы сделать это, необходимо установить <xref:System.Drawing.Font.Bold%2A> свойства `true`. Это приводит к записывается в файлы ресурсов, где локализаторам можно изменить начертание шрифта. Затем написать код после `InitializeComponent` метод, который сбрасывает шрифт на основании шрифт независимо от формы, но использует начертание шрифта, указанное в файле ресурсов.  
  
```  
' Visual Basic  
TextBox1.Font = New System.Drawing.Font(Me.Font, TextBox1.Font.Style)  
  
// C#  
textBox1.Font = new System.Drawing.Font(this.Font, textBox1.Font.Style);  
```  
  
## <a name="see-also"></a>См. также  
 [Глобализация Windows Forms](../../../../docs/framework/winforms/advanced/globalizing-windows-forms.md)  
 [Работами со шрифтами и текстом](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
