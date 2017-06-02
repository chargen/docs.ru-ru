---
title: "Операции службы (службы WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "HTML"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "операции службы [службы WCF Data Services]"
  - "Службы WCF Data Services, операции службы"
ms.assetid: 583a690a-e60f-4990-8991-d6efce069d76
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# Операции службы (службы WCF Data Services)
Службы [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] позволяют определять операции службы над службой данных для предоставления методов сервера.  Как и остальные ресурсы службы данных, операции службы адресуются с помощью URI.  Операции службы позволяют предоставлять бизнес\-логику службы данных, например реализовывать логику проверки, применять правила безопасности на основе ролей и предоставлять специализированные возможности запросов.  Операции службы — это методы, добавленные в класс службы данных, производный от <xref:System.Data.Services.DataService%601>. Методу операции службы вы можете передать параметры, как и любые другие ресурсы службы данных. Например, следующий URI операции службы \(основанный на службе данных [quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)\) передает значение `London` для параметра `city`:  
  
```  
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'  
```  
  
 Определение этой операции службы выглядит следующим образом:  
  
 [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationdef)]
 [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationdef)]  
  
 Свойство <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> класса <xref:System.Data.Services.DataService%601> можно использовать для непосредственного обращения к источнику данных при работе со службой данных.  Для получения дополнительной информации см. [Как определить операцию службы](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md).  
  
 Сведения о том, как вызвать операцию службы из клиентского приложения .NET Framework, см. в разделе [Вызов операций служб](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md).  
  
## Требования к операциям службы  
 Следующие требования применяются при определении операций службы в службе данных.  Если метод не соответствует этим требованиям, то не предоставляется в качестве операции службы для службы данных.  
  
-   Операция должна быть методом публичного экземпляра, являющимся элементом класса службы данных.  
  
-   Метод операции может принимать только входные параметры.  Данные, отправленные в тексте сообщения, недоступны для службы данных.  
  
-   Если параметры определены, каждый параметр должен иметь примитивный тип.  Любые данные, не являющееся типом\-примитивом, должны быть сериализованы и переданы в строковый параметр.  
  
-   Метод должен возвращать одно из следующих значений:  
  
    -   `void` \(`Nothing` в Visual Basic\).  
  
    -   <xref:System.Collections.Generic.IEnumerable%601>  
  
    -   <xref:System.Linq.IQueryable%601>  
  
    -   Тип сущности в модели данных, которую предоставляет служба данных.                  ``  
  
    -   Примитивный класс, такой как целое число или строка.  
  
-   Для поддержки параметров запросов, таких как сортировка, разбиение по страницам и фильтрация, методы операций службы должны возвращать класс <xref:System.Linq.IQueryable%601>.  Запросы к операциям службы, включающие параметры запросов, не допускаются для операций, которые возвращают только интерфейс <xref:System.Collections.Generic.IEnumerable%601>.  
  
-   Для поддержки доступа к связанным сущностям с помощью навигационных свойств операция службы должна возвращать интерфейс <xref:System.Linq.IQueryable%601>.  
  
-   Метод должен сопровождаться атрибутом `[WebGet]` или `[WebInvoke]`.  
  
    -   `[WebGet]` позволяет вызывать метод с помощью запроса GET.  
  
    -   `[WebInvoke(Method = "POST")]` позволяет вызывать метод с помощью запроса POST.  Другие методы <xref:System.ServiceModel.Web.WebInvokeAttribute> не поддерживаются.  
  
-   Операция службы может сопровождаться атрибутом <xref:System.Data.Services.SingleResultAttribute>, который указывает, что возвращаемое из метода значение является отдельной сущностью, а не коллекцией сущностей.  Это различие определяет результирующую сериализацию ответа и способ представления обхода дополнительных навигационных свойств в URI.  Например, при использовании сериализации AtomPub отдельный экземпляр типа ресурса представлен в качестве элемента entry, а набор экземпляров — в качестве элемента feed.  
  
## Адресация операций службы  
 Адресовать операции службы можно, помещая имя метода в первый сегмент пути в URI.  Например, следующий URI обращается к операции `GetOrdersByState`, которая возвращает коллекцию <xref:System.Linq.IQueryable%601> объектов `Orders`.  
  
```  
http://localhost:12345/Northwind.svc/GetOrdersByState?state='CA'&includeItems=true  
```  
  
 При вызове операции службы параметры предоставляются в качестве параметров запроса.  Предыдущая операция службы принимает как строковый параметр `state`, так и логический параметр `includeItems`, который указывает, следует ли включить в ответ связанные объекты `Order_Detail`.  
  
 Ниже приведены допустимые типы возвращаемых значений для операции службы.  
  
|Допустимые типы возвращаемых значений|Правила URI|  
|-------------------------------------------|-----------------|  
|`void` \(`Nothing` в Visual Basic\).<br /><br /> \-или\-<br /><br /> Типы сущностей<br /><br /> \-или\-<br /><br /> Примитивные типы|URI должен содержать один сегмент пути, представляющий собой имя операции службы.  Параметры запросов не допускаются.|  
|<xref:System.Collections.Generic.IEnumerable%601>|URI должен содержать один сегмент пути, представляющий собой имя операции службы.  Поскольку результат имеет тип, отличный от <xref:System.Linq.IQueryable%601>, параметры запросов не допускаются.|  
|<xref:System.Linq.IQueryable%601>|Допускаются сегменты пути запроса в дополнение к имени операции службы.  Параметры запросов также допускаются.|  
  
 Дополнительные сегменты пути или параметры запросов добавляются в URI в зависимости от типа возвращаемого значения операции службы.  Например, следующий URI обращается к операции `GetOrdersByCity`, которая возвращает коллекцию <xref:System.Linq.IQueryable%601> объектов `Orders`, упорядоченных по значению `RequiredDate` в убывающем порядке, вместе со связанными объектами `Order_Details`:  
  
```  
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc  
  
```  
  
## Управление доступом к операциям службы  
 Управление общей видимостью операций службы осуществляется с помощью метода <xref:System.Data.Services.IDataServiceConfiguration.SetServiceOperationAccessRule%2A> класса <xref:System.Data.Services.IDataServiceConfiguration> в основном так же, как происходит управление видимостью набора сущностей с помощью метода <xref:System.Data.Services.IDataServiceConfiguration.SetEntitySetAccessRule%2A>.  Например, в следующей строке кода определения службы данных включается доступ к операции службы `CustomersByCity`.  
  
 [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationconfig)]
 [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationconfig)]  
  
> [!NOTE]
>  Если операция службы имеет возвращаемый тип, скрытый путем ограничения доступа к базовым наборам сущностей, операция службы не будет доступна клиентским приложениям.  
  
 Для получения дополнительной информации см. [Как определить операцию службы](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md).  
  
## Вызов исключений  
 Рекомендуется использовать класс <xref:System.Data.Services.DataServiceException> всякий раз, когда нужно вызывать исключение при выполнении службы данных.  Это необходимо потому, что среде выполнения службы данных известно, как правильно сопоставить свойства этого объекта исключения с ответным сообщением HTTP.  При вызове <xref:System.Data.Services.DataServiceException> в операции службы возвращаемое исключение упаковывается в <xref:System.Reflection.TargetInvocationException>.  Чтобы вернуть базовое <xref:System.Data.Services.DataServiceException> без включения <xref:System.Reflection.TargetInvocationException>, необходимо переопределить метод <xref:System.Data.Services.DataService%601.HandleException%2A> в <xref:System.Data.Services.DataService%601>, извлечь <xref:System.Data.Services.DataServiceException> из <xref:System.Reflection.TargetInvocationException> и возвратить его в качестве ошибки верхнего уровня, как показано в следующем примере:  
  
 [!code-csharp[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#handleexceptions)]
 [!code-vb[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#handleexceptions)]  
  
## См. также  
 [Перехватчики](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md)