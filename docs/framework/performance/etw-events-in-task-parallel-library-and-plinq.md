---
title: События трассировки событий Windows в библиотеке параллельных задач и PLINQ
ms.date: 03/30/2017
helpviewer_keywords:
- tasks, ETW events
ms.assetid: 87a9cff5-d86f-4e44-a06e-d12764d0dce2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3c5b372073b00f30312a83ae88ae0dbb6885d1a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="etw-events-in-task-parallel-library-and-plinq"></a>События трассировки событий Windows в библиотеке параллельных задач и PLINQ
Библиотека параллельных задач и PLINQ создают события трассировки событий Windows (ETW), которые можно использовать для профилирования и устранения неполадок в приложениях с помощью таких средств, как Windows Performance Analyzer. Однако в большинстве сценариев оптимальный способ профилирования параллельного кода приложения — использование [визуализатора параллелизма](/visualstudio/profiling/concurrency-visualizer) в [!INCLUDE[vsUltShort](../../../includes/vsultshort-md.md)].  
  
## <a name="task-parallel-library-etw-events"></a>События трассировки событий Windows в библиотеке параллельных задач (TPL)  
 В структуре EVENT_HEADER используется следующий идентификатор GUID ProviderId для событий, создаваемых <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> и <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType>:  
  
```  
0x2e5dba47, 0xa3d2, 0x4d16, 0x8e, 0xe0, 0x66, 0x71, 0xff, 0xdc, 0xd7, 0xb5  
```  
  
### <a name="parallel-loop-begin"></a>Начало параллельного цикла  
 EVENT_DESCRIPTOR.Task = 1  
  
 EVENT_DESCRIPTOR.Id = 1  
  
#### <a name="user-data"></a>Данные пользователя  
  
|**Name**|**Type**|**Описание**|  
|--------------|--------------|---------------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Идентификатор объекта TaskScheduler, который начал цикл.|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Идентификатор задачи, которая начала цикл.|  
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Уникальный идентификатор, используемый для обозначения вложений и пар для событий с семантикой ветвления и соединения.|  
|OperationType|<xref:System.Int32?displayProperty=nameWithType>|Указывает тип цикла:<br /><br /> 1 = ParallelInvoke<br /><br /> 2 = ParallelFor<br /><br /> 3 = ParallelForEach|  
|InclusiveFrom|<xref:System.Int64?displayProperty=nameWithType>|Начальное значение счетчика цикла|  
|ExclusiveTo|<xref:System.Int64?displayProperty=nameWithType>|Конечное значение счетчика цикла|  
  
### <a name="parallel-loop-end"></a>Конец параллельного цикла  
 EVENT_DESCRIPTOR.Task = 2  
  
 EVENT_DESCRIPTOR.Id = 2  
  
#### <a name="user-data"></a>Данные пользователя  
  
|**Name**|**Type**|**Описание**|  
|--------------|--------------|---------------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Идентификатор объекта TaskScheduler, который начал цикл.|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Идентификатор задачи, которая начала цикл.|  
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Уникальный идентификатор, используемый для обозначения вложений и пар для событий с семантикой ветвления и соединения.|  
|totalIterations|<xref:System.Int64?displayProperty=nameWithType>|Общее количество итераций|  
  
### <a name="parallel-invoke-begin"></a>Начало параллельного вызова  
 EVENT_DESCRIPTOR.Task = 3  
  
 EVENT_DESCRIPTOR.Id = 3  
  
#### <a name="user-data"></a>Данные пользователя  
  
|**Name**|**Type**|**Описание**|  
|--------------|--------------|---------------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Идентификатор объекта TaskScheduler, который начал цикл.|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Идентификатор задачи, которая начала цикл.|  
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Уникальный идентификатор, используемый для обозначения вложений и пар для событий с семантикой ветвления и соединения.|  
|totalIterations|<xref:System.Int64?displayProperty=nameWithType>|Общее количество итераций|  
|operationType|<xref:System.Int32?displayProperty=nameWithType>|Указывает тип цикла:<br /><br /> 1 = ParallelInvoke<br /><br /> 2 = ParallelFor<br /><br /> 3 = ParallelForEach|  
|ActionCount|<xref:System.Int32?displayProperty=nameWithType>|Количество действий, которые будут выполнены при параллельном вызове.|  
  
### <a name="parallel-invoke-end"></a>Конец параллельного вызова  
 EVENT_DESCRIPTOR.Task = 4  
  
 EVENT_DESCRIPTOR.Id = 4  
  
#### <a name="user-data"></a>Данные пользователя  
  
|**Name**|**Type**|**Описание**|  
|--------------|--------------|---------------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Идентификатор объекта TaskScheduler, который начал цикл.|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Идентификатор задачи, которая начала цикл.|  
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Уникальный идентификатор, используемый для обозначения вложений и пар для событий с семантикой ветвления и соединения.|  
  
## <a name="plinq-etw-events"></a>События трассировки событий Windows в PLINQ  
 GUID EVENT_HEADER.ProviderId для PLINQ:  
  
```  
0x159eeeec, 0x4a14, 0x4418, 0xa8, 0xfe, 0xfa, 0xab, 0xcd, 0x98, 0x78, 0x87  
```  
  
### <a name="parallel-query-begin"></a>Начало параллельного запроса  
 EVENT_DESCRIPTOR.Task = 1  
  
 EVENT_DESCRIPTOR.Id = 1  
  
#### <a name="user-data"></a>Данные пользователя  
  
|**Name**|**Type**|**Описание**|  
|--------------|--------------|---------------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Идентификатор объекта TaskScheduler, который начал цикл.|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Идентификатор задачи, которая начала цикл.|  
|QueryID|<xref:System.Int32?displayProperty=nameWithType>|Уникальный идентификатор запроса.|  
  
### <a name="parallel-query-end"></a>Конец параллельного запроса  
 EVENT_DESCRIPTOR.Task = 2  
  
 EVENT_DESCRIPTOR.Id = 2  
  
#### <a name="user-data"></a>Данные пользователя  
  
|**Name**|**Type**|**Описание**|  
|--------------|--------------|---------------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Идентификатор объекта TaskScheduler, который начал цикл.|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Идентификатор задачи, которая начала цикл.|  
|QueryID|<xref:System.Int32?displayProperty=nameWithType>|Уникальный идентификатор запроса.|  
  
## <a name="see-also"></a>См. также  
 [События трассировки событий Windows в .NET Framework](../../../docs/framework/performance/etw-events.md)  
 [Библиотека параллельных задач (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
