---
title: "Метод ICorProfilerCallback::AssemblyUnloadStarted"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.AssemblyUnloadStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::AssemblyUnloadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyUnloadStarted method [.NET Framework profiling]
- AssemblyUnloadStarted method [.NET Framework profiling]
ms.assetid: 6e47b7e5-0335-4dd3-8c42-d3c07d62b102
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2631650b55ec440a39a3c1a2e0c911f8868fed75
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a><span data-ttu-id="db10c-102">Метод ICorProfilerCallback::AssemblyUnloadStarted</span><span class="sxs-lookup"><span data-stu-id="db10c-102">ICorProfilerCallback::AssemblyUnloadStarted Method</span></span>
<span data-ttu-id="db10c-103">Уведомляет профилировщик о том, что сборка выгружается.</span><span class="sxs-lookup"><span data-stu-id="db10c-103">Notifies the profiler that an assembly is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db10c-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="db10c-104">Syntax</span></span>  
  
```  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="db10c-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="db10c-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="db10c-106">[in] Идентифицирует сборку, которая выгружается.</span><span class="sxs-lookup"><span data-stu-id="db10c-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db10c-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="db10c-107">Remarks</span></span>  
 <span data-ttu-id="db10c-108">Значение `assemblyId` является недопустимым для информационного запроса после `AssemblyUnloadStarted` возвращает метод — это профилировщика последнюю возможность получить сведения об этой сборки.</span><span class="sxs-lookup"><span data-stu-id="db10c-108">The value of `assemblyId` is not valid for an information request after the `AssemblyUnloadStarted` method returns — this is the profiler's last chance to get information about this assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db10c-109">Требования</span><span class="sxs-lookup"><span data-stu-id="db10c-109">Requirements</span></span>  
 <span data-ttu-id="db10c-110">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db10c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db10c-111">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="db10c-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="db10c-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="db10c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db10c-113">**Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db10c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db10c-114">См. также</span><span class="sxs-lookup"><span data-stu-id="db10c-114">See Also</span></span>  
 [<span data-ttu-id="db10c-115">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="db10c-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="db10c-116">Метод AssemblyUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="db10c-116">AssemblyUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)