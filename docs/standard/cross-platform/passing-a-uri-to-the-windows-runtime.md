---
title: Передача URI в среду выполнения Windows
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Runtime, .NET Framework support for
- Windows Runtime, passing a URI to
ms.assetid: 3eb5ce6f-f304-4f87-8e81-0f25092f5ad4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7a31a1246fe311c36e7457327c79aeeef30e7813
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="passing-a-uri-to-the-windows-runtime"></a>Передача URI в среду выполнения Windows
Методы среды выполнения Windows принимают только абсолютные URI. Если передать относительный URI методу [!INCLUDE[wrt](../../../includes/wrt-md.md)], вызывается исключение <xref:System.ArgumentException>. Вот почему: при использовании [!INCLUDE[wrt](../../../includes/wrt-md.md)] в коде .NET Framework <xref:Windows.Foundation.Uri?displayProperty=nameWithType> класс отображается как <xref:System.Uri?displayProperty=nameWithType> в Intellisense. <xref:System.Uri?displayProperty=nameWithType> Класс допускает относительные URI, но <xref:Windows.Foundation.Uri?displayProperty=nameWithType> класса — нет. Это также справедливо для методов, доступных в компонентах [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Если компонент предоставляет метод, принимающий URI, сигнатура в коде содержит <xref:System.Uri?displayProperty=nameWithType>. Однако для пользователей вашего компонента сигнатура содержит <xref:Windows.Foundation.Uri?displayProperty=nameWithType>. URI, переданный вашему компоненту, должен быть абсолютным.  
  
 В этом разделе показано, как определить абсолютный URI и как создать его при указании ссылки на ресурс в пакете приложения.  
  
## <a name="detecting-and-using-an-absolute-uri"></a>Определение и использование абсолютного URI  
 Используйте свойство <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType>, чтобы убедиться, что URI является абсолютным, перед его передачей классу [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Такой подход более эффективен, чем перехват и обработка исключения <xref:System.ArgumentException>.  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a>Использование абсолютного URI для ресурса в пакете приложения  
 Чтобы указать URI для ресурса в пакете приложения, можно использовать схему `ms-appx` или `ms-appx-web` для создания абсолютного URI.  
  
 Следующий пример показывает, как задать [источника](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.source.aspx) свойство для [WebView](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.aspx) управления и [источника](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.image.source.aspx) свойство [изображения](http://msdn.microsoft.com/library/windows/apps/br242752.aspx) управления для ресурсов, содержащихся в папке страниц с использованием XAML и кода.  
  
 [!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
 Дополнительные сведения об этих схемах см. в разделе [схемы URI](http://msdn.microsoft.com/library/windows/apps/jj655406.aspx) в центре разработчиков Windows.  
  
## <a name="see-also"></a>См. также  
 [Поддержка платформы .NET Framework для приложений магазина Windows и среды выполнения Windows](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
