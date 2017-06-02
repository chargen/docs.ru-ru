---
title: "x:FactoryMethod Directive | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "XAML. x:FactoryMethod directive [XAML Services]"
  - "FactoryMethod directive in XAML [XAML Services]"
  - "x:FactoryMethod directive [XAML Services]"
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
caps.latest.revision: 8
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 8
---
# x:FactoryMethod Directive
Указывает метод, отличный от конструктора, который процессор XAML должен использовать для инициализации объекта после разрешения его резервного типа.  
  
## Использование атрибутов XAML, не x:Arguments  
  
```  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## Использование атрибутов XAML, x:Arguments как элементы  
  
```  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## Значения XAML  
  
|||  
|-|-|  
|`methodname`|Имя метода строки, который вызывают процессоры XAML для инициализации экземпляра, заданного как `object`.  См. примечания.|  
|`oneOrMoreObjectElements`|Один или несколько объектных элементов для объектов, задающих параметры фабричных методов.  Порядок имеет значение, т. к. обозначает порядок, в котором аргументы должны быть переданы в фабричный метод.|  
  
## Заметки  
 Если `methodname` является методом экземпляра, его невозможно квалифицировать.  
  
 Поддерживаются статические методы как фабричные методы.  Если `methodname` является статическим методом, то `methodname` предоставляется как сочетание *Имя\_типа*.*Имя\_метода*, где *Имя\_типа* означает класс, который определяет статический фабричный метод.  *typeName* может иметь префикс, если ссылается на тип в сопоставленных xmlns.  *typeName* может быть типом, отличным от `typeof(``object``)`.  
  
 Заводской метод должен быть объявлен открытым методом типа, который возвращает соответствующий элемент объекта.  
  
 Фабричный метод должен возвращать экземпляр, который может быть назначен соответствующему объекту.  Фабричные методы никогда не должны возвращать значение NULL.  
  
 `x:Arguments` работает по принципу наилучшего соответствия для сигнатур методов фабрик.  При поиске соответствия сначала оценивается число параметров.  Если имеется несколько возможных соответствий для числа параметров, тогда следом оценивается тип параметра и определяется наилучшее соответствие.  Если после этого этапа оценки остается неоднозначность, поведение процессора языка XAML является неопределенным.  
  
 Использование элемента `x:FactoryMethod` не является использованием элемента свойства в обычном смысле, так как разметка директивы не ссылается на тип элемента содержащего его объекта.  Ожидается, что элементы используются реже, чем атрибуты.  `x:Arguments` \(использование атрибута или элемента\) может применяться вместе с использованием элемента `x:FactoryMethod`, но это не отображается в разделах использования.  
  
 Как элемент, `x:FactoryMethod` должен предварять другие элементы свойства и должен предшествовать любому `x:Arguments`, также представленному как элементы, и должен предшествовать содержимому, внутреннему тексту или тексту инициализации.  
  
## См. также  
 [x:Arguments Directive](../../../docs/framework/xaml-services/x-arguments-directive.md)