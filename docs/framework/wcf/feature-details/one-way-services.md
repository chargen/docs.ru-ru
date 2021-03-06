---
title: Односторонние службы
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], one-way service contracts
- WCF [WCF], one-way service contracts
- service contracts [WCF], defining one-way
ms.assetid: 19053a36-4492-45a3-bfe6-0365ee0205a3
ms.openlocfilehash: 03efc27f2ba54ca22f03e3ece84770fe0dcadbb3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="one-way-services"></a>Односторонние службы
По умолчанию операция службы выполняется по шаблону "запрос-ответ". В соответствии с шаблоном "запрос-ответ" клиент ждет ответного сообщения, даже если операция службы представлена в коде в виде метода `void`. В случае односторонних операций передается только одно сообщение. Получатель не отправляет ответное сообщение, а отправитель не ожидает получения этого сообщения.  
  
 Односторонний шаблон используется в следующих случаях.  
  
-   Если клиент должен вызывать операции и не зависит от результата выполнения этих операций на уровне операций.  
  
-   При использовании класса <xref:System.ServiceModel.NetMsmqBinding> или <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>. (Дополнительные сведения об этом сценарии см. в разделе [очереди в WCF](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md).)  
  
 Если операция является односторонней, ответное сообщение, в котором могут передаваться сведения об ошибке, клиенту не отправляется. Условия возникновения ошибок можно определять с помощью функций соответствующей привязки, например надежных сеансов, или посредством разработки дуплексного контракта службы, который использует две односторонних операции - односторонний контракт от клиента к службе для вызова операции службы и еще один односторонний контракт между службой и клиентом, чтобы служба могла вернуть клиенту ошибки, используя реализуемый в клиенте обратный вызов.  
  
 Чтобы создать односторонний контракт службы, определите контракт службы, примените класс <xref:System.ServiceModel.OperationContractAttribute> к каждой из операций, и установите свойство <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> равным `true`, как показано в следующем примере кода.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOneWayCalculator  
{  
    [OperationContract(IsOneWay=true)]  
    void Add(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Subtract(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Multiply(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Divide(double n1, double n2);  
}  
```  
  
 Полный пример см. в разделе [одностороннего](../../../../docs/framework/wcf/samples/one-way.md) образца.  
  
## <a name="clients-blocking-with-one-way-operations"></a>Блокировка клиентов с помощью односторонних операций  
 Очень важно помнить, что, хотя некоторые односторонние приложения возобновляют работу, как только исходящие данные будут переданы по сетевому подключению, в некоторых случаях реализация привязки или службы может привести к клиенту WCF с помощью односторонних операций. В клиентские приложения WCF объекта клиента WCF не возвращается до исходящие данные переданы по сетевому подключению. Это относится ко всем шаблонам обмена сообщениями, включая односторонние операции; это означает, что любая проблема, связанная с передачей данных через транспортный канал, не позволит клиенту вернуть управление. В зависимости от проблемы ее результатом может быть исключение или задержка при отправке сообщения службе.  
  
 Например, если транспорту не удается найти конечную точку, исключение <xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType> будет создано без большой задержки. Однако также возможна ситуация, при которой службе по какой-либо причине не удается считать данные из сети, в результате чего операция отправки на стороне клиента не может быть завешена. В этих случаях, если превышается время <xref:System.ServiceModel.Channels.Binding.SendTimeout%2A?displayProperty=nameWithType> привязки транспорта клиента, создается исключение <xref:System.TimeoutException?displayProperty=nameWithType> - но не раньше истечения времени ожидания. Кроме того, службе может быть отправлено так много сообщений, что в какой-то момент служба больше не сможет их обрабатывать. В этом случае односторонний клиент также блокируется, пока служба не сможет обработать сообщения или пока не будет создано исключение.  
  
 Подобная блокировка также может происходить в том случае, если свойство <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> службы имеет значение <xref:System.ServiceModel.ConcurrencyMode.Single>, а привязка использует сеансы. В этом случае диспетчер принудительно упорядочивает входящие сообщения (требование сеансов), что не допускает чтения из сети следующего сообщения, пока служба не обработала предыдущее сообщение для этого сеанса. Клиент в этом случае также блокируется, но появление исключения зависит от того, успеет ли служба обработать ожидающие данные, пока не истечет установленное на стороне клиента время ожидания.  
  
 Можно частично ограничить эту проблему, поместив буфер между объектом клиента и операцией отправки транспорта клиента. Например, при использовании асинхронных вызовов или очереди сообщений в памяти объект клиента может быстро возвращать управление. Оба подхода могут расширить функциональность, но размер пула потоков и очереди сообщений по-прежнему накладывает ограничения.  
  
 Вместо этого рекомендуется изучить различные элементы управления службы и клиента и испытать различные сценарии работы приложения, чтобы определить наилучшую конфигурацию на каждой из сторон. Например, если использование сеансов блокирует обработку сообщений на стороне службы, можно установить для свойства <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> значение <xref:System.ServiceModel.InstanceContextMode.PerCall>, чтобы каждое сообщение обрабатывалось отдельным экземпляром службы, а также установить свойство <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> равным <xref:System.ServiceModel.ConcurrencyMode.Multiple>, чтобы одновременно распределять сообщения могло более одного потока. Еще одно возможное решение - увеличить квоты чтения привязок службы и клиента.  
  
## <a name="see-also"></a>См. также  
 [Одностороннее взаимодействие](../../../../docs/framework/wcf/samples/one-way.md)
