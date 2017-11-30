---
title: "Метод ICorProfilerCallback2::SurvivingReferences"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback2.SurvivingReferences
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback2::SurvivingReferences
helpviewer_keywords:
- ICorProfilerCallback2::SurvivingReferences method [.NET Framework profiling]
- SurvivingReferences method [.NET Framework profiling]
ms.assetid: f165200e-3a91-47f7-88fc-13ff10c8babc
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3764bfb79b39af897600202e8bc0f2ffbc4da95b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback2survivingreferences-method"></a><span data-ttu-id="6390b-102">Метод ICorProfilerCallback2::SurvivingReferences</span><span class="sxs-lookup"><span data-stu-id="6390b-102">ICorProfilerCallback2::SurvivingReferences Method</span></span>
<span data-ttu-id="6390b-103">Предоставляет информацию о структуре объектов в куче в результате сборки мусора без сжатия.</span><span class="sxs-lookup"><span data-stu-id="6390b-103">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6390b-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6390b-104">Syntax</span></span>  
  
```  
HRESULT SurvivingReferences(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] ULONG  
                cObjectIDRangeLength[] );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6390b-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="6390b-105">Parameters</span></span>  
 `cSurvivingObjectIDRanges`  
 <span data-ttu-id="6390b-106">[in] Количество блоков смежных объектов, оставшихся в результате сборки мусора без сжатия.</span><span class="sxs-lookup"><span data-stu-id="6390b-106">[in] The number of blocks of contiguous objects that survived as the result of the non-compacting garbage collection.</span></span> <span data-ttu-id="6390b-107">То есть значение `cSurvivingObjectIDRanges` является размером массивов `objectIDRangeStart` и `cObjectIDRangeLength`, в которых хранятся идентификаторы `ObjectID` и длины каждого блока объектов соответственно.</span><span class="sxs-lookup"><span data-stu-id="6390b-107">That is, the value of `cSurvivingObjectIDRanges` is the size of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays, which store an `ObjectID` and a length, respectively, for each block of objects.</span></span>  
  
 <span data-ttu-id="6390b-108">Следующие два аргумента `SurvivingReferences` являются параллельными массивами.</span><span class="sxs-lookup"><span data-stu-id="6390b-108">The next two arguments of `SurvivingReferences` are parallel arrays.</span></span> <span data-ttu-id="6390b-109">Иными словами, `objectIDRangeStart` и `cObjectIDRangeLength` относятся к одному и тому же блоку смежных объектов.</span><span class="sxs-lookup"><span data-stu-id="6390b-109">In other words, `objectIDRangeStart` and `cObjectIDRangeLength` concern the same block of contiguous objects.</span></span>  
  
 `objectIDRangeStart`  
 <span data-ttu-id="6390b-110">[in] Массив значений `ObjectID`, каждое из которых является начальным адресом блока смежных активных объектов в памяти.</span><span class="sxs-lookup"><span data-stu-id="6390b-110">[in] An array of `ObjectID` values, each of which is the starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="6390b-111">[in] Массив целых чисел, каждое из которых представляет размер оставшегося блока смежных объектов в памяти.</span><span class="sxs-lookup"><span data-stu-id="6390b-111">[in] An array of integers, each of which is the size of a surviving block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="6390b-112">Размер указывается для каждого блока, ссылка на который имеется в массиве `objectIDRangeStart`.</span><span class="sxs-lookup"><span data-stu-id="6390b-112">A size is specified for each block that is referenced in the `objectIDRangeStart` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6390b-113">Примечания</span><span class="sxs-lookup"><span data-stu-id="6390b-113">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6390b-114">Этот метод сообщает размеры как `MAX_ULONG` для объектов с размером более 4 ГБ на 64-разрядных платформах.</span><span class="sxs-lookup"><span data-stu-id="6390b-114">This method reports sizes as `MAX_ULONG` for objects that are greater than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="6390b-115">Объекты, размер которых превышает 4 ГБ, используйте [ICorProfilerCallback4::SurvivingReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md) метод вместо него.</span><span class="sxs-lookup"><span data-stu-id="6390b-115">For objects that are larger than 4 GB, use the [ICorProfilerCallback4::SurvivingReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="6390b-116">Для определения того, уцелел ли объект после сборки мусора, элементы массивов `objectIDRangeStart` и `cObjectIDRangeLength` должны интерпретироваться следующим образом.</span><span class="sxs-lookup"><span data-stu-id="6390b-116">The elements of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays should be interpreted as follows to determine whether an object survived the garbage collection.</span></span> <span data-ttu-id="6390b-117">Предположим, что значение `ObjectID` (`ObjectID`) находится в следующем диапазоне:</span><span class="sxs-lookup"><span data-stu-id="6390b-117">Assume that an `ObjectID` value (`ObjectID`) lies within the following range:</span></span>  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="6390b-118">При любом значении `i`, находящемся в указанном ниже диапазоне, объект уцелел после сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="6390b-118">For any value of `i` that is in the following range, the object has survived the garbage collection:</span></span>  
  
 <span data-ttu-id="6390b-119">0 <= `i` < `cSurvivingObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="6390b-119">0 <= `i` < `cSurvivingObjectIDRanges`</span></span>  
  
 <span data-ttu-id="6390b-120">Сборка мусора без сжатия освобождает память, занятую "мертвыми" объектами, но не сжимает освобожденное пространство.</span><span class="sxs-lookup"><span data-stu-id="6390b-120">A non-compacting garbage collection reclaims the memory occupied by "dead" objects, but does not compact that freed space.</span></span> <span data-ttu-id="6390b-121">В результате этого память возвращается в кучу, но активные объекты не перемещаются.</span><span class="sxs-lookup"><span data-stu-id="6390b-121">As a result, memory is returned to the heap, but no "live" objects are moved.</span></span>  
  
 <span data-ttu-id="6390b-122">Среда CLR вызывает метод `SurvivingReferences` для выполнения сборки мусора без сжатия.</span><span class="sxs-lookup"><span data-stu-id="6390b-122">The common language runtime (CLR) calls `SurvivingReferences` for non-compacting garbage collections.</span></span> <span data-ttu-id="6390b-123">Для мусора со сжатием [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) вызывается.</span><span class="sxs-lookup"><span data-stu-id="6390b-123">For compacting garbage collections, [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) is called instead.</span></span> <span data-ttu-id="6390b-124">Отдельная операция сборки мусора может предусматривать сжатие для одного поколения и не предусматривать — для другого.</span><span class="sxs-lookup"><span data-stu-id="6390b-124">A single garbage collection can be compacting for one generation and non-compacting for another.</span></span> <span data-ttu-id="6390b-125">Для сборки мусора в каком-либо конкретном поколении профилировщик получит либо обратный вызов `SurvivingReferences`, либо обратный вызов `MovedReferences` (но не оба вызова).</span><span class="sxs-lookup"><span data-stu-id="6390b-125">For a garbage collection on any particular generation, the profiler will receive either a `SurvivingReferences` callback or a `MovedReferences` callback, but not both.</span></span>  
  
 <span data-ttu-id="6390b-126">Несколько обратных вызовов `SurvivingReferences` может быть получено в ходе определенной сборки мусора из-за ограниченной внутренней буферизации, нескольких потоков отчетов в случае сборки мусора на сервере и по другим причинам.</span><span class="sxs-lookup"><span data-stu-id="6390b-126">Multiple `SurvivingReferences` callbacks might be received during a particular garbage collection, due to limited internal buffering, multiple threads reporting in the case of server garbage collection, and other reasons.</span></span> <span data-ttu-id="6390b-127">При получении нескольких обратных вызовов во время сборки мусора информация накапливается — все ссылки, сообщаемые в обратных вызовах `SurvivingReferences`, сохранятся после сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="6390b-127">In the case of multiple callbacks during a garbage collection, the information is cumulative — all references that are reported in any `SurvivingReferences` callback survive the garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6390b-128">Требования</span><span class="sxs-lookup"><span data-stu-id="6390b-128">Requirements</span></span>  
 <span data-ttu-id="6390b-129">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6390b-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6390b-130">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6390b-130">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6390b-131">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6390b-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6390b-132">**Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6390b-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6390b-133">См. также</span><span class="sxs-lookup"><span data-stu-id="6390b-133">See Also</span></span>  
 [<span data-ttu-id="6390b-134">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="6390b-134">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="6390b-135">Интерфейс ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="6390b-135">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [<span data-ttu-id="6390b-136">Метод SurvivingReferences2</span><span class="sxs-lookup"><span data-stu-id="6390b-136">SurvivingReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)