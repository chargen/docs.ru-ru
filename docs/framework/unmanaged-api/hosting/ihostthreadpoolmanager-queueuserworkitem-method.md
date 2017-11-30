---
title: "Метод IHostThreadPoolManager::QueueUserWorkItem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostThreadPoolManager.QueueUserWorkItem
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostThreadPoolManager::QueueUserWorkItem
helpviewer_keywords:
- IHostThreadPoolManager::QueueUserWorkItem method [.NET Framework hosting]
- QueueUserWorkItem method [.NET Framework hosting]
ms.assetid: 41602053-8670-4827-9d61-cbfcba509b9c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9948673d6988de21c83c37538fb4d7c030296e58
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="ihostthreadpoolmanagerqueueuserworkitem-method"></a><span data-ttu-id="5a099-102">Метод IHostThreadPoolManager::QueueUserWorkItem</span><span class="sxs-lookup"><span data-stu-id="5a099-102">IHostThreadPoolManager::QueueUserWorkItem Method</span></span>
<span data-ttu-id="5a099-103">Помещает в очередь для выполнения функции и указывает объект, содержащий данные для использования этой функцией.</span><span class="sxs-lookup"><span data-stu-id="5a099-103">Queues a function for execution, and specifies an object containing data to be used by that function.</span></span> <span data-ttu-id="5a099-104">Функция выполняется, когда поток становится доступной.</span><span class="sxs-lookup"><span data-stu-id="5a099-104">The function executes when a thread becomes available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a099-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5a099-105">Syntax</span></span>  
  
```  
HRESULT QueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID Context,  
    [in] ULONG Flags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5a099-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="5a099-106">Parameters</span></span>  
 `Function`  
 <span data-ttu-id="5a099-107">[in] Указатель на функцию, который представляет функцию для выполнения.</span><span class="sxs-lookup"><span data-stu-id="5a099-107">[in] A function pointer that represents the function to execute.</span></span>  
  
 `Context`  
 <span data-ttu-id="5a099-108">[in] Объект, содержащий данные для использования с `Function`.</span><span class="sxs-lookup"><span data-stu-id="5a099-108">[in] An object that contains data to be used by `Function`.</span></span>  
  
 `Flags`  
 <span data-ttu-id="5a099-109">[in] Один из флагов значений, определенных для Win32 `QueueUserWorkItem` метод, который управляет выполнением.</span><span class="sxs-lookup"><span data-stu-id="5a099-109">[in] One of the flags values, as defined for the Win32 `QueueUserWorkItem` method, that control execution.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5a099-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="5a099-110">Return Value</span></span>  
  
|<span data-ttu-id="5a099-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5a099-111">HRESULT</span></span>|<span data-ttu-id="5a099-112">Описание</span><span class="sxs-lookup"><span data-stu-id="5a099-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5a099-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="5a099-113">S_OK</span></span>|<span data-ttu-id="5a099-114">`QueueUserWorkItem`успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="5a099-114">`QueueUserWorkItem` returned successfully.</span></span>|  
|<span data-ttu-id="5a099-115">ЗНАЧЕНИЕ HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5a099-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5a099-116">Общеязыковая среда выполнения (CLR) не был загружен в процесс или находится в состоянии, в котором не может выполнять управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="5a099-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5a099-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5a099-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5a099-118">Истекло время ожидания вызова.</span><span class="sxs-lookup"><span data-stu-id="5a099-118">The call timed out.</span></span>|  
|<span data-ttu-id="5a099-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5a099-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5a099-120">Вызывающий объект не является владельцем блокировки.</span><span class="sxs-lookup"><span data-stu-id="5a099-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5a099-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5a099-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5a099-122">Событие было отменено заблокированный поток или ожидал волокон.</span><span class="sxs-lookup"><span data-stu-id="5a099-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5a099-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5a099-123">E_FAIL</span></span>|<span data-ttu-id="5a099-124">Неизвестная Неустранимая ошибка.</span><span class="sxs-lookup"><span data-stu-id="5a099-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5a099-125">Если метод вернет значение E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="5a099-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5a099-126">Последующие вызовы размещение методы возвращают значение HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5a099-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a099-127">Примечания</span><span class="sxs-lookup"><span data-stu-id="5a099-127">Remarks</span></span>  
 <span data-ttu-id="5a099-128">`QueueUserWorkItem`ставит в очередь рабочий элемент в рабочем потоке пула потоков.</span><span class="sxs-lookup"><span data-stu-id="5a099-128">`QueueUserWorkItem` queues a work item to a worker thread in the thread pool.</span></span> <span data-ttu-id="5a099-129">Его сигнатура и типы параметров идентичны соответствующей функции Win32, которая имеет то же имя.</span><span class="sxs-lookup"><span data-stu-id="5a099-129">Its signature and parameter types are identical to those of the corresponding Win32 function, which has the same name.</span></span> <span data-ttu-id="5a099-130">Дополнительные сведения см. в документации по платформе Windows.</span><span class="sxs-lookup"><span data-stu-id="5a099-130">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a099-131">Требования</span><span class="sxs-lookup"><span data-stu-id="5a099-131">Requirements</span></span>  
 <span data-ttu-id="5a099-132">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a099-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a099-133">**Заголовок:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5a099-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5a099-134">**Библиотека:** включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5a099-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5a099-135">**Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a099-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a099-136">См. также</span><span class="sxs-lookup"><span data-stu-id="5a099-136">See Also</span></span>  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="5a099-137">IHostThreadPoolManager-интерфейс</span><span class="sxs-lookup"><span data-stu-id="5a099-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)