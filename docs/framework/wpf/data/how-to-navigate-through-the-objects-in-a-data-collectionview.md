---
title: Практическое руководство. Перемещение по объектам в Data CollectionView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CollectionView [WPF], navigating through objects
- data binding [WPF], navigating through objects in data CollectionView
- navigating through objects in data CollectionView [WPF]
ms.assetid: fcd37590-bce1-4ac9-8b74-3b96c7458b8a
ms.openlocfilehash: ec78b7350d23364cfb0eaa9a0611be8449073cd7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-navigate-through-the-objects-in-a-data-collectionview"></a>Практическое руководство. Перемещение по объектам в Data CollectionView
Представления позволяют просматривать различными способами, в зависимости от сортировки, фильтрации и группирования же коллекцию данных. Представления также предоставляют понятием текущего указателя записи и включают перемещение указателя. В этом примере показано, как получить текущий объект, а также перемещение по объектам в коллекции данных, используя функциональные возможности, предоставляемые <xref:System.Windows.Data.CollectionView> класса.  
  
## <a name="example"></a>Пример  
 В этом примере `myCollectionView` — <xref:System.Windows.Data.CollectionView> объект, который является представлением присоединенной коллекции.  
  
 В следующем примере `OnButton` является обработчиком событий для `Previous` и `Next` кнопки в приложении, которые находятся кнопки, позволяющие пользователю перемещаться по коллекции данных. Обратите внимание, что <xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> и <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> свойства отчета, является ли указатель текущей записи поступило в начало и конец списка соответственно таким образом, <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> и <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> могут быть вызваны соответствующим образом.  
  
 <xref:System.Windows.Data.CollectionView.CurrentItem%2A> Свойства представления приводится к `Order` для возврата текущего элемента в коллекции.  
  
 [!code-csharp[CollectionView#OnButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#onbutton)]
 [!code-vb[CollectionView#OnButton](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#onbutton)]  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о привязке данных](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Сортировка данных в представлении](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)  
 [Фильтрация данных в представлении](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)  
 [Сортировка и группировка данных с помощью представления в XAML](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)  
 [Разделы практического руководства](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
