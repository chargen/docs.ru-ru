---
title: "Threads and Threading | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "multiple threads"
  - "threading [.NET Framework]"
  - "threading [.NET Framework], multiple threads"
ms.assetid: 5baac3aa-e603-4fa6-9f89-0f2c1084e6b1
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# Threads and Threading
Для разделения различных выполняемых приложений в операционных системах используются процессы.  Потоки являются основными элементами, для которых операционная система выделяет время процессора; внутри процесса может выполняться более одного потока.  Каждый поток поддерживает обработчик исключений, планируемый приоритет и набор структур, используемых системой для сохранения контекста потока во время его планирования.  Контекст потока содержит все необходимые данные для возобновления выполнения \(включая набор регистров процессора и стек\) в адресном пространстве ведущего процесса потока.  
  
 Далее .NET Framework подразделяет процесс операционной системы на облегченные управляемые подпроцессы, вызывающие домены приложения, представленные <xref:System.AppDomain?displayProperty=fullName>.  Один или несколько управляемых потоков \(представленных <xref:System.Threading.Thread?displayProperty=fullName>\) могут выполняться в одном или нескольких доменах приложения в одном управляемом процессе.  Несмотря на то, что каждый домен приложения запускается с одним потоком, в коде данного домена можно создать дополнительные домены приложения и потоки.  Благодаря этому управляемый поток может свободно перемещаться между доменами приложения внутри одного того же управляемого процесса; между несколькими доменами приложения одновременно может перемещаться только один поток.  
  
 Операционная система, поддерживающая приоритетную многозадачность, создает эффект одновременного выполнения нескольких потоков из нескольких процессов.  Это выполняется путем последовательного распределения доступного времени процессора между требуемыми потоками.  Текущий выполняемый поток приостанавливается по истечении выделенного времени; после этого запускается другой поток.  При переключении от одного потока к другому контекст потока, работа которого была приостановлена, сохраняется, и загружается контекст следующего потока из очереди.  
  
 Количество выделяемого для потока времени определяется операционной системой и процессором.  Поскольку это время мало, выполнение нескольких потоков будет происходить почти одновременно, даже при наличии одного процессора.  В многопроцессорной системе выполняемые потоки распределяются между доступными процессорами.  
  
## Использование нескольких потоков  
 Для обеспечения быстроты работы пользователя используемое программное обеспечение должно как можно быстрее реагировать на его действия.  В то же время оно должно производить вычисления, необходимые для быстрого представления данных.  Если в приложении используется однопоточное выполнение можно совмещать [асинхронное программирование](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md) с [удаленным взаимодействием .NET Framework](http://msdn.microsoft.com/ru-ru/eccb1d31-0a22-417a-97fd-f4f1f3aa4462) или [веб\-службами XML](http://msdn.microsoft.com/ru-ru/1e64af78-d705-4384-b08d-591a45f4379c), созданными с помощью ASP.NET. Это позволяет увеличить быстроту ответа системы на действия пользователя и уменьшить время обработки данных в приложении.  При выполнении большого количества операций ввода\-вывода для увеличения быстроты ответа системы можно также использовать порты завершения ввода\-вывода.  
  
### Достоинства многопоточности  
 Использование более одного потока является наиболее мощным средством увеличения быстроты ответа системы на действия пользователя, а также средством обработки данных, необходимых для одновременного выполнения задачи.  Для обработки данных в фоновом режиме на компьютере с одним процессором этот эффект достигается путем использования небольших периодов времени между событиями пользователя.  Например, пока пользователь вносит изменения в электронную таблицу, другой поток в данном приложении может пересчитывать другие части этой таблицы.  
  
 Производительность такого приложения на компьютере с несколькими процессорами будет существенно выше.  Для выполнения следующих задач в домене приложения необходимо использовать несколько потоков.  
  
-   Взаимодействие по сети с веб\-сервером и базой данных.  
  
-   Выполнение операций, занимающих много времени.  
  
-   Разделение задач по приоритетам.  Например, поток с высоким приоритетом отвечает за срочные задачи, с низким приоритетом — за все остальные.  
  
-   Сохранение возможности ответа для интерфейса пользователя при выделении времени для фоновой задачи.  
  
### Недостатки многопоточности  
 Для увеличения производительности и уменьшения количества используемых ресурсов системы рекомендуется использовать как можно меньше потоков.  Кроме того, при использовании потоков необходимо учитывать требования к ресурсам и возможность возникновения ошибок при разработке приложения.  Существуют следующие требования к ресурсам.  
  
-   Память, используемая системой для обработки контекстных данных, необходимых в процессах, объектах **AppDomain** и потоках.  Поэтому количество создаваемых процессов, объектов **AppDomain** и потоков ограничено объемом доступной памяти.  
  
-   Время процессора, используемое для отслеживания количества потоков.  Если количество потоков велико, большинство из них не будет работать должным образом.  Если большинство текущих потоков находится в одном процессе, потоки других процессов планируются реже.  
  
-   Контроль выполнения кода с большим количеством потоков достаточно сложен и может являться причиной ошибок.  
  
-   При уничтожении потоков необходимо учитывать возможные проблемы и предусмотреть способы их решения.  
  
 При совместном доступе к ресурсам могут возникать конфликты.  Для их предотвращения нужно синхронизировать или контролировать доступ к общим ресурсам.  Ошибка синхронизации доступа \(в одном или разных доменах приложения\) может привести к зависанию \(поток перестает выполняться, ожидая завершения работы другого поток, который, в свою очередь, ожидает завершения работы первого потока\) и состояниям гонки \(возникновение непредвиденных результатов из\-за неверной временной зависимости между двумя событиями\).  Система содержит синхронизирующие объекты, используемые для управления распределением ресурсов между потоками.  Синхронизация ресурсов упрощается, если количество потоков невелико.  
  
 Ресурсы, требующие синхронизации:  
  
-   системные ресурсы \(последовательные порты\);  
  
-   ресурсы, используемые несколькими процессами \(дескрипторы файлов\);  
  
-   ресурсы отдельного домена приложения \(глобальные, статические поля или поля экземпляров\), к которым обращаются несколько потоков.  
  
### Разработка потоков и приложений  
 Как правило, обработка нескольких потоков для относительно простых задач, не влияющих на работу других потоков, и при отсутствии планирования задач, выполняется с помощью класса <xref:System.Threading.ThreadPool>.  Однако существует ряд причин для создания собственных потоков.  
  
-   Задаче необходимо задать приоритет.  
  
-   Выполнение задачи может занять много времени \(при этом блокируются другие задачи\).  
  
-   Необходимо поместить поток в однопотоковый апартамент \(все потоки **ThreadPool** являются многопотоковыми апартаментами\).  
  
-   С потоком требуется связать устойчивое удостоверение.  Например, определенный поток используется для отмены или приостановки текущего потока, или для обнаружения потока по его имени.  
  
-   Если необходимо выполнять фоновые потоки, которые взаимодействуют с пользовательским интерфейсом, платформа .NET Framework версии 2.0 предоставляет компонент <xref:System.ComponentModel.BackgroundWorker> который взаимодействует с потоком пользовательского интерфейса с помощью событий, используя маршалинг между потоками.  
  
### Поточность и исключения  
 Не обрабатывайте исключения в потоках.  Необработанные исключения в потоках, даже в фоновых потоках, как правило, приводит к прерыванию процесса.  Существует три исключения из этого правила:  
  
-   Исключение <xref:System.Threading.ThreadAbortException> создается в потоке, потому что была вызвана перегрузка <xref:System.Threading.Thread.Abort%2A>.  
  
-   Исключение <xref:System.AppDomainUnloadedException> создается в потоке, так как выгружается домен приложения.  
  
-   Среда CLR или процесс основного приложения прерывает выполнение потока.  
  
 Для получения дополнительной информации см. [Exceptions in Managed Threads](../../../docs/standard/threading/exceptions-in-managed-threads.md).  
  
> [!NOTE]
>  В .NET Framework версии 1.0 и 1.1 среда CLR без уведомления перехватывает некоторые исключения, например в потоках пула потоков.  Это может привести к повреждению состояния приложения и, в конце концов, приведет к зависанию приложений, отладить которые будет очень трудно.  
  
## См. также  
 <xref:System.Threading.ThreadPool>   
 <xref:System.ComponentModel.BackgroundWorker>   
 [Synchronizing Data for Multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)   
 [The Managed Thread Pool](../../../docs/standard/threading/the-managed-thread-pool.md)