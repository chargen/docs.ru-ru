---
title: Создание служб WCF для ASP.NET AJAX
ms.date: 03/30/2017
ms.assetid: 04c0402c-e617-4ba5-aedf-d17692234776
ms.openlocfilehash: c2d56380b626cd0eafc178b4db3584883b00a6bf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="creating-wcf-services-for-aspnet-ajax"></a>Создание служб WCF для ASP.NET AJAX
Технология ASP.NET AJAX корпорации Майкрософт позволяет быстро создавать веб-страницы, содержащие широкий набор средств взаимодействия с пользователем с известными элементами пользовательского интерфейса. Эта технология предоставляет библиотеки клиентских сценариев, включающие не зависящие от веб-обозревателя технологии ECMAScript (JavaScript) и динамического HTML (DHTML), и интегрирует их с платформой разработки на базе сервера ASP.NET 2.0. Используя ASP.NET AJAX, можно улучшить взаимодействие веб-приложений с пользователем и повысить их эффективность.  
  
 Технология ASP.NET AJAX состоит из библиотек клиентских сценариев и серверных компонентов, интегрированных для обеспечения надежной инфраструктуры разработки. Доступ к службе со страницы ASP.NET: если URL-адрес службы добавляется в элемент управления диспетчера скриптов ASP.NET на странице, операции службы могут вызываться с помощью кода JavaScript, что выглядит абсолютно аналогично обычному вызову функции JavaScript. В разделе [узнать ASP.NET AJAX](http://go.microsoft.com/fwlink/?LinkId=186475) об использовании веб-служб в AJAX framework.  
  
 Большинство служб Windows Communication Foundation (WCF) можно представить в виде службы, совместимой с ASP.NET AJAX, добавив соответствующую конечную точку ASP.NET AJAX.  
  
 При использовании Visual Studio можно использовать встроенный шаблон для служб WCF с поддержкой AJAX, доступных в **Добавление нового элемента** диалоговое окно при работе с веб-сайтов ASP.NET и веб-приложения.  
  
 Если шаблоны Visual Studio не используются, конечную точку ASP.NET AJAX можно создать двумя указанными ниже способами.  
  
-   Создайте конечную точку, используя динамическую активацию ведущего приложения, не применяя никакой конфигурации. Это основной подход при незнании системы конфигурации WCF. Дополнительные сведения см. в разделе [как: Добавление ASP.NET AJAX конфигурации конечной точки без с помощью](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
-   Добавьте конечную точку с поддержкой AJAX для службы WCF, с помощью конфигурации. Дополнительные сведения см. в разделе [как: использование конфигурации для добавления конечной точки ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).  
  
 Модель веб-программирования, описанной в [WCF Web HTTP программирования Общие сведения о модели](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md) могут быть использованы с службы ASP.NET AJAX. В частности:  
  
-   Для выбора команд HTTP GET и HTTP POST можно использовать атрибуты <xref:System.ServiceModel.Web.WebGetAttribute> и <xref:System.ServiceModel.Web.WebInvokeAttribute>. При правильном применении это может существенно повысить производительность приложения. Дополнительные сведения см. в разделе [как: запросы Выбор между HTTP POST и HTTP GET для конечных точек ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md).  
  
-   Чтобы вынудить службу возвращать XML-данные вместо нотации объекта JavaScript (JSON) по умолчанию, можно применить свойства <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> и <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>. При использовании этой возможности с инфраструктурой ASP.NET AJAX клиент JavaScript будет принимать DOM-объект XML.  
  
    > [!WARNING]
    >  Для правильной работы необходимо с помощью операции задать тип содержимого text/xml. В противном случае клиент JavaScript будет принимать строку, содержащую XML вместо DOM-объекта XML.  
  
     В следующем примере показана операция, возвращающая XML-данные с типом содержимого, настроенным соответствующим образом.  
  
    ```  
    [OperationContract, WebGet(ResponseFormat=WebMessageFormat.Xml)]  
    public XElement GetData()  
    {  
    XElement x;  
    //Get some data here...  
  
    WebOperationContext.Current.OutgoingResponse.ContentType = "text/xml";      
    return x;  
    }  
    ```  
  
-   Если требуется совместимость с ASP.NET AJAX, никакие другие свойства в атрибутах <xref:System.ServiceModel.Web.WebGetAttribute> и <xref:System.ServiceModel.Web.WebInvokeAttribute> изменять нельзя. Можно использовать другие аспекты модели веб-программирования, пока не нарушены соглашения о вызовах ASP.NET AJAX.  
  
 Более сложные сценарии требуют некоторых дополнительных подробностей поддержки AJAX в WCF воспринимать:  
  
-   Чтобы понять, каким образом данные передаются между клиентом страница AJAX и службы WCF с помощью JavaScript, а также подробные сведения на сопоставление типов .NET Framework с типами JavaScript, в разделе [Поддержка JSON и других передачи форматов данных](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md).  
  
-   чтобы воспользоваться преимуществами возможностей ASP.NET, например проверкой подлинности на основе URL-адреса и доступом к данным сеансов ASP.NET, можно включить режим совместимости с ASP.NET с использованием конфигурации.  
  
 Конечные точки AJAX в WCF можно использовать даже без инфраструктуры ASP.NET AJAX. Для этого необходимо понимать архитектуру поддержки поддержки AJAX в WCF. Описание этой архитектуре см. в разделе [HTTP модель программирования WCF Web объекта](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md). Образец кода, демонстрирующий этот подход, в разделе [службы AJAX с JSON и XML-](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).  
  
## <a name="see-also"></a>См. также  
 [Модель веб-программирования HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [Практическое руководство. Добавление конечной точки ASP.NET AJAX без использования конфигурации](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)  
 [Практическое руководство. Использование конфигурации для добавления конечной точки ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)  
 [Практическое руководство. Выбор между запросами HTTP POST и HTTP GET для конечных точек ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md)
