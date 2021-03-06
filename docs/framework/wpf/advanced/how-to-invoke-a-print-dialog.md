---
title: Практическое руководство. Вызов диалогового окна печати
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking print dialogs [WPF]
- print dialogs [WPF], invoking
ms.assetid: e3a2c84c-74fe-45a4-8501-5813f9dbfed2
ms.openlocfilehash: f94a965f724e85fb63ed9c98ebddba40938eb9b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-invoke-a-print-dialog"></a>Практическое руководство. Вызов диалогового окна печати
Чтобы обеспечить возможность печати из приложения, можно просто создать и открыть <xref:System.Windows.Controls.PrintDialog> объекта.  
  
## <a name="example"></a>Пример  
 Элемент управления <xref:System.Windows.Controls.PrintDialog> предоставляет единую точку входа для [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], конфигурации и отправки задания [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)]. Элемент управления является простота использования и может быть создан с помощью [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] разметки или кода. В следующем примере показано, как создать и открыть элемент управления в коде и печать из него. Также показано, как убедиться, что диалоговое окно предоставит пользователям возможность установки конкретного диапазона страниц. В примере кода предполагается, что имеется файл FixedDocumentSequence.xps в корне диска C:.  
  
 [!code-csharp[printdialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 После открытия диалогового окна пользователи смогут выбрать один из принтеров на компьютере. Они также будут иметь возможность выбрать [записи XPS-документов Microsoft](http://go.microsoft.com/fwlink/?LinkId=147319) для создания [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] файла вместо печати.  
  
> [!NOTE]
>  <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> Управления [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], который рассматривается в этом разделе, не следует путать с <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> компонент Windows Forms.  
  
 Строго говоря, можно использовать <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> метода, не открывая диалоговое окно. В этом смысле элемент управления может использоваться в качестве невидимого компонента печати. Однако для повышения производительности было бы лучше использовать <xref:System.Printing.PrintQueue.AddJob%2A> метода или один из многих <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> и <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> методы <xref:System.Windows.Xps.XpsDocumentWriter>. Дополнительные сведения об этом разделе [программно печати XPS-файлы](../../../../docs/framework/wpf/advanced/how-to-programmatically-print-xps-files.md) и.  
  
## <a name="see-also"></a>См. также  
 <xref:System.Windows.Controls.PrintDialog>  
 [Документы в WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Общие сведения о печати](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [Записи Microsoft XPS-документов](http://go.microsoft.com/fwlink/?LinkId=147319)
