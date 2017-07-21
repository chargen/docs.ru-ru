---
title: "Настраиваемый диспетчер каналов | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 813acf03-9661-4d57-a3c7-eeab497321c6
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Настраиваемый диспетчер каналов
Этот образец демонстрирует построение пользовательского стека каналов путем непосредственной реализации <xref:System.ServiceModel.ServiceHostBase>, а также создание пользовательского диспетчера каналов в среде веб\-узла.Диспетчер каналов взаимодействует с <xref:System.ServiceModel.Channels.IChannelListener> для принятия каналов и получения сообщений из стека каналов.В рамках этого образца также представлен базовый образец, показывающий, как построить стек каналов в среде веб\-узла с помощью <xref:System.ServiceModel.Activation.VirtualPathExtension>.  
  
## Пользовательский ServiceHostBase  
 Вместо <xref:System.ServiceModel.ServiceHost> этот образец реализует базовый тип <xref:System.ServiceModel.ServiceHostBase> для демонстрации замены реализации стека [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] пользовательским уровнем обработки сообщений поверх стека каналов.Для построения прослушивателей и диспетчера каналов переопределяется виртуальный метод <xref:System.ServiceModel.ServiceHostBase.InitializeRuntime%2A>.  
  
 Чтобы реализовать службу, размещенную на веб\-сервере, возвратите расширение службы <xref:System.ServiceModel.Activation.VirtualPathExtension> из коллекции <xref:System.ServiceModel.ServiceHostBase.Extensions%2A> и добавьте его в коллекцию <xref:System.ServiceModel.Channels.BindingParameterCollection>, чтобы транспортному слою было известно, как настроить прослушиватель канала на основе параметров среды размещения, то есть параметров служб IIS\/службы активации Windows \(WAS\).  
  
## Настраиваемый диспетчер каналов  
 Пользовательский диспетчер каналов расширяет тип <xref:System.ServiceModel.Dispatcher.ChannelDispatcherBase>.Этот тип реализует логику программирования уровня канала.В этом образце для шаблона обмена сообщениями «запрос\-ответ» поддерживается только <xref:System.ServiceModel.Channels.IReplyChannel>, при этом пользовательский диспетчер каналов можно легко расширить, добавив другие типы каналов.  
  
 Сначала диспетчер открывает прослушиватель каналов, а затем принимает одноэлементный канал ответа.По этому каналу он запускает бесконечный цикл отправки сообщений \(запросов\).По каждому запросу он создает ответное сообщение и отправляет его назад клиенту.  
  
## Создание ответного сообщения  
 Обработка сообщений реализуется в типе `MyServiceManager`.В методе `HandleRequest` сначала проверяется заголовок `Action` сообщения, чтобы выяснить, поддерживается ли запрос.Стандартное действие протокола SOAP «http:\/\/tempuri.org\/HelloWorld\/Hello» определено для выполнения фильтрации сообщений.Это похоже на концепцию контракта службы из реализации [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] объекта <xref:System.ServiceModel.ServiceHost>.  
  
 Для выбора правильного действия протокола SOAP образец получает запрошенные данные сообщения и формирует соответствующий ответ на запрос, аналогично случаю <xref:System.ServiceModel.ServiceHost>.  
  
 В этом случае команда HTTP\-GET была специально обработана путем возврата пользовательского сообщения HTTP с тем, чтобы можно было открыть службу в браузере, чтобы удостовериться, что она правильно скомпилирована.Если действие протокола SOAP не совпадает, отправьте сообщение об ошибке, чтобы указать, что запрос не поддерживается.  
  
 В этом образце используется обычный клиент [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], в котором не сделано никаких предположений относительно службы.Поэтому служба создана специально с учетом соответствия результатам нормальной для [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] реализации <xref:System.ServiceModel.ServiceHost>.В результате этого в клиенте требуется наличие только контракта службы.  
  
## Использование образца  
 При прямом запуске клиентского приложения формируется следующий результат.  
  
```Output  
Клиент разговаривает со службой WCF типа «запрос-ответ».   
Введите приветствие серверу: «Привет»  
Ответ сервера: «Вы сказали: привет».Идентификатор сообщения: 1  
Ответ сервера: «Вы сказали: привет».Идентификатор сообщения: 2  
Ответ сервера: «Вы сказали: привет».Идентификатор сообщения: 3  
Ответ сервера: «Вы сказали: привет».Идентификатор сообщения: 4  
Ответ сервера: «Вы сказали: привет».Идентификатор сообщения: 5  
  
```  
  
 Службу также можно открыть в браузере с тем, чтобы сообщение HTTP\-GET было обработано на сервере.При этом возвращается хорошо отформатированный текст в формате HTML.  
  
> [!IMPORTANT]
>  Образцы уже могут быть установлены на компьютере.Перед продолжением проверьте следующий каталог \(по умолчанию\).  
>   
>  `<диск_установки>:\WF_WCF_Samples`  
>   
>  Если этот каталог не существует, перейдите на страницу [Образцы Windows Communication Foundation \(WCF\) и Windows Workflow Foundation \(WF\) для .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780), чтобы загрузить все образцы [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] и [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Этот образец расположен в следующем каталоге.  
>   
>  `<диск_установки>:\WF_WCF_Samples\WCF\Extensibility\Channels\CustomChannelDispatcher`