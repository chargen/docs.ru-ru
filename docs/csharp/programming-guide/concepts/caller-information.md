---
title: Сведения о вызывающем объекте (C#)
ms.date: 07/20/2015
ms.assetid: ffad3d24-2fb7-4641-9124-53b5bc91d339
ms.openlocfilehash: 6f0cd4d9d8fc85cb15431ccb4c76eee14b3f67c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="caller-information-c"></a>Сведения о вызывающем объекте (C#)
С помощью информационных атрибутов вызывающего объекта можно получить сведения о вызывающем объекте метода. Можно получить путь к файлу исходного кода, номер строки в исходном коде и имя вызывающего объекта. Эти сведения полезны для трассировки, отладки и создания средств диагностики.  
  
 Для получения этих сведений используются атрибуты, которые применяются к необязательным параметрам, каждый из которых имеет значение по умолчанию. В следующей таблице перечислены информационные атрибуты вызывающего объекта, которые определены в пространстве имен <xref:System.Runtime.CompilerServices?displayProperty=nameWithType>:  
  
|Атрибут|Описание:|Тип|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Полный путь исходного файла, содержащего вызывающий объект. Это путь к файлу во время компиляции.|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Номер строки в исходном файле, в которой вызывается метод.|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Имя свойства или метода вызывающего объекта. См. подраздел [Имена членов](#MEMBERNAMES) ниже.|`String`|  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать информационные атрибуты вызывающего объекта. При каждом вызове метода `TraceMessage` сведения о вызывающем объекте подставляются в качестве аргументов необязательных параметров.  
  
```csharp  
public void DoProcessing()  
{  
    TraceMessage("Something happened.");  
}  
  
public void TraceMessage(string message,  
        [System.Runtime.CompilerServices.CallerMemberName] string memberName = "",  
        [System.Runtime.CompilerServices.CallerFilePath] string sourceFilePath = "",  
        [System.Runtime.CompilerServices.CallerLineNumber] int sourceLineNumber = 0)  
{  
    System.Diagnostics.Trace.WriteLine("message: " + message);  
    System.Diagnostics.Trace.WriteLine("member name: " + memberName);  
    System.Diagnostics.Trace.WriteLine("source file path: " + sourceFilePath);  
    System.Diagnostics.Trace.WriteLine("source line number: " + sourceLineNumber);  
}  
  
// Sample Output:  
//  message: Something happened.  
//  member name: DoProcessing  
//  source file path: c:\Users\username\Documents\Visual Studio 2012\Projects\CallerInfoCS\CallerInfoCS\Form1.cs  
//  source line number: 31  
```  
  
## <a name="remarks"></a>Примечания  
 Для каждого необязательного параметра необходимо указать явное значение по умолчанию. Нельзя применять информационные атрибуты вызывающего объекта к параметрам, которые не были указаны как необязательные.  
  
 Информационные атрибуты вызывающего объекта не делают параметр необязательным. Вместо этого они влияют на значение по умолчанию, которое передается, если аргумент был опущен.  
  
 Информационные значения вызывающего объекта передаются как литералы в IL во время компиляции. В отличие от результатов свойства <xref:System.Exception.StackTrace%2A> для исключений, результаты не затрагиваются запутыванием кода.  
  
 Можно явно передать необязательные аргументы, чтобы управлять сведениями о вызывающем объекте или скрывать сведения о вызывающем объекте.  
  
###  <a name="MEMBERNAMES"></a> Имена членов  
 Можно использовать атрибут `CallerMemberName`, чтобы не указывать имя члена в виде аргумента `String` вызываемому методу. Этот прием позволяет избежать проблемы, заключающейся в том, что **операция рефакторинга и переименования** не изменяет значений `String`. Это особенно полезно при выполнении следующих задач:  
  
-   Использование процедур трассировки и диагностики.  
  
-   Реализация интерфейса <xref:System.ComponentModel.INotifyPropertyChanged> при привязке данных. Этот интерфейс позволяет свойству объекта уведомлять связанный элемент управления об изменении свойства, чтобы элемент управления мог отображать обновленные сведения. Если атрибут `CallerMemberName` не используется, необходимо указать имя свойства как литерал.  
  
 В следующей таблице представлены имена членов, возвращаемых при использовании атрибута `CallerMemberName`.  
  
|Фрагмент кода, в пределах которого происходит вызов|Результат имени члена|  
|-------------------------|------------------------|  
|Метод, свойство или событие|Имя метода, свойства или события, из которого происходил вызов.|  
|Конструктор|Строка ".ctor"|  
|Статический конструктор|Строка ".cctor"|  
|Деструктор|Строка "Finalize"|  
|Определяемые пользователем операторы и преобразования|Созданное имя члена, например, "op_Addition".|  
|Конструктора атрибута|Имя члена, к которому применяется атрибут. Если атрибут — любой элемент внутри члена (например, параметр, возвращаемое значение или параметр универсального типа), то результат — имя члена, который связан с этим элементом.|  
|Нет содержащего члена (например, уровень сборки или атрибуты, примененные к типам)|Значение необязательного параметра по умолчанию.|  
  
## <a name="see-also"></a>См. также  
 [Атрибуты (C#)](../../../csharp/programming-guide/concepts/attributes/index.md)  
 [Общие атрибуты (C#)](../../../csharp/programming-guide/concepts/attributes/common-attributes.md)  
 [Именованные и необязательные аргументы](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)  
 [Основные понятия программирования (C#)](../../../csharp/programming-guide/concepts/index.md)
