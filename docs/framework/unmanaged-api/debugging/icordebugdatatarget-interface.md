---
title: "Интерфейс ICorDebugDataTarget"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugDataTarget
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugDataTarget
helpviewer_keywords: ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: df5f05be-bed7-4f3c-bc89-dbb435d79a0b
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 030ad5e61d215bd840da5b16a56e4b8f8b7791ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatarget-interface"></a><span data-ttu-id="42bcd-102">Интерфейс ICorDebugDataTarget</span><span class="sxs-lookup"><span data-stu-id="42bcd-102">ICorDebugDataTarget Interface</span></span>
<span data-ttu-id="42bcd-103">Предоставляет интерфейс обратного вызова, обеспечивающий доступ к конкретному целевому процессу.</span><span class="sxs-lookup"><span data-stu-id="42bcd-103">Provides a callback interface that provides access to a particular target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="42bcd-104">Методы</span><span class="sxs-lookup"><span data-stu-id="42bcd-104">Methods</span></span>  
  
|<span data-ttu-id="42bcd-105">Метод</span><span class="sxs-lookup"><span data-stu-id="42bcd-105">Method</span></span>|<span data-ttu-id="42bcd-106">Описание</span><span class="sxs-lookup"><span data-stu-id="42bcd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="42bcd-107">Метод GetPlatform</span><span class="sxs-lookup"><span data-stu-id="42bcd-107">GetPlatform Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)|<span data-ttu-id="42bcd-108">Предоставляет сведения о платформе, включая архитектуру процессора и операционной системы, на котором выполняется целевой процесс.</span><span class="sxs-lookup"><span data-stu-id="42bcd-108">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>|  
|[<span data-ttu-id="42bcd-109">Метод ReadVirtual</span><span class="sxs-lookup"><span data-stu-id="42bcd-109">ReadVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-readvirtual-method.md)|<span data-ttu-id="42bcd-110">Получает блок непрерывной памяти, начиная с указанного адреса и возвращает его в указанный буфер.</span><span class="sxs-lookup"><span data-stu-id="42bcd-110">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>|  
|[<span data-ttu-id="42bcd-111">Метод GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="42bcd-111">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getthreadcontext-method.md)|<span data-ttu-id="42bcd-112">Запрашивает текущий контекст потока для указанного потока.</span><span class="sxs-lookup"><span data-stu-id="42bcd-112">Requests the current thread context for the specified thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42bcd-113">Примечания</span><span class="sxs-lookup"><span data-stu-id="42bcd-113">Remarks</span></span>  
 <span data-ttu-id="42bcd-114">`ICorDebugDataTarget`и его методы имеют следующие характеристики:</span><span class="sxs-lookup"><span data-stu-id="42bcd-114">`ICorDebugDataTarget` and its methods have the following characteristics:</span></span>  
  
-   <span data-ttu-id="42bcd-115">Службы отладки вызывают методы этого интерфейса для доступа к памяти и другими данными в целевом процессе.</span><span class="sxs-lookup"><span data-stu-id="42bcd-115">The debugging services call methods on this interface to access memory and other data in the target process.</span></span>  
  
-   <span data-ttu-id="42bcd-116">Клиент отладчика должен реализовывать этот интерфейс, в зависимости от конкретного целевого объекта (например, активный процесс или дамп памяти).</span><span class="sxs-lookup"><span data-stu-id="42bcd-116">The debugger client must implement this interface as appropriate for the particular target (for example, a live process or a memory dump).</span></span>  
  
-   <span data-ttu-id="42bcd-117">`ICorDebugDataTarget` Методы могут вызываться только из методов, реализованных в других `ICorDebug*` интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="42bcd-117">The `ICorDebugDataTarget` methods can be invoked only from within methods implemented in other `ICorDebug*` interfaces.</span></span> <span data-ttu-id="42bcd-118">Это гарантирует, что клиент отладчика управляет для потока, в который он вызывается и когда.</span><span class="sxs-lookup"><span data-stu-id="42bcd-118">This ensures that the debugger client has control over which thread it is invoked on, and when.</span></span>  
  
-   <span data-ttu-id="42bcd-119">`ICorDebugDataTarget` Реализация должна всегда возвращать актуальные сведения о цели.</span><span class="sxs-lookup"><span data-stu-id="42bcd-119">The `ICorDebugDataTarget` implementation must always return up-to-date information about the target.</span></span>  
  
 <span data-ttu-id="42bcd-120">Целевой процесс следует останавливать и не изменяется во всех отношениях `ICorDebug*` интерфейсы (и, следовательно, `ICorDebugDataTarget` методы) вызываются.</span><span class="sxs-lookup"><span data-stu-id="42bcd-120">The target process should be stopped and not changed in any way while `ICorDebug*` interfaces (and therefore `ICorDebugDataTarget` methods) are being called.</span></span> <span data-ttu-id="42bcd-121">Если целью является активного процесса и его изменения состояния [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) метод должен вызываться снова, чтобы предоставить экземпляр ICorDebugProcess замены.</span><span class="sxs-lookup"><span data-stu-id="42bcd-121">If the target is a live process and its state changes, the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method has to be called again to provide a replacement ICorDebugProcess instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="42bcd-122">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="42bcd-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42bcd-123">Требования</span><span class="sxs-lookup"><span data-stu-id="42bcd-123">Requirements</span></span>  
 <span data-ttu-id="42bcd-124">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42bcd-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42bcd-125">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="42bcd-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42bcd-126">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42bcd-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42bcd-127">**Версии платформы .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42bcd-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42bcd-128">См. также</span><span class="sxs-lookup"><span data-stu-id="42bcd-128">See Also</span></span>  
 [<span data-ttu-id="42bcd-129">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="42bcd-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="42bcd-130">Отладка</span><span class="sxs-lookup"><span data-stu-id="42bcd-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)