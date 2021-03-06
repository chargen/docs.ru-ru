---
title: Практическое руководство. Использование системных цветов в градиенте
ms.date: 03/30/2017
helpviewer_keywords:
- gradients [WPF], system colors in
- system colors in gradients [WPF]
ms.assetid: 11942e7e-6300-4b50-8ed1-f50e8d20e7d2
ms.openlocfilehash: 4c3fca1db031b0dc397e9db58195b9714ff8aa9a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-system-colors-in-a-gradient"></a>Практическое руководство. Использование системных цветов в градиенте
Чтобы использовать системный цвет в градиенте, используйте  *\<SystemColor >* цвета и  *\<SystemColor >* ColorKey статических свойств <xref:System.Windows.SystemColors> для получения ссылки на цвет, где  *\<SystemColor >* имя необходимого системного цвета. Используйте  *\<SystemColor >* ColorKey свойства, если вы хотите создать динамическую ссылку, которая обновляется автоматически по мере изменения темы системы. В противном случае используйте  *\<SystemColor >* свойства цветов.  
  
## <a name="example"></a>Пример  
 В следующем примере для создания градиента используются динамические ресурсы системных цветов.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemColorExample.xaml#graphicsmmdynamicsystemcolorgradientexamplewholepage)]  
  
 В следующем примере для создания градиента используются статические ресурсы системных цветов.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemColorExample.xaml#graphicsmmstaticsystemcolorgradientexamplewholepage)]  
  
## <a name="see-also"></a>См. также  
 <xref:System.Windows.SystemColors>  
 [Заливка области с помощью системной кисти](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [Общие сведения о закраске сплошным цветом и градиентом](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
