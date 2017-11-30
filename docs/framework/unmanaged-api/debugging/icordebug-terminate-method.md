---
title: "Метод ICorDebug::Terminate"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.Terminate
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug::Terminate
helpviewer_keywords:
- Terminate method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Terminate method [.NET Framework debugging]
ms.assetid: fffe5616-0896-4426-ab5e-21869b514883
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b18bb6222296c5e8875f983d47118f938a54bcc2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="e28c8-102">Метод ICorDebug::Terminate</span><span class="sxs-lookup"><span data-stu-id="e28c8-102">ICorDebug::Terminate Method</span></span>
<span data-ttu-id="e28c8-103">Завершает `ICorDebug` объекта.</span><span class="sxs-lookup"><span data-stu-id="e28c8-103">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e28c8-104">`Terminate`не следует вызывать до [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) получил обратного вызова для всех отлаживаемых процессов.</span><span class="sxs-lookup"><span data-stu-id="e28c8-104">`Terminate` should not be called until an [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e28c8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e28c8-105">Syntax</span></span>  
  
```  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="e28c8-106">Примечания</span><span class="sxs-lookup"><span data-stu-id="e28c8-106">Remarks</span></span>  
 <span data-ttu-id="e28c8-107">`Terminate`должно вызываться при `ICorDebug` объект больше не нужен.</span><span class="sxs-lookup"><span data-stu-id="e28c8-107">`Terminate` must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e28c8-108">Требования</span><span class="sxs-lookup"><span data-stu-id="e28c8-108">Requirements</span></span>  
 <span data-ttu-id="e28c8-109">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e28c8-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e28c8-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e28c8-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e28c8-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e28c8-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e28c8-112">**Версии платформы .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e28c8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e28c8-113">См. также</span><span class="sxs-lookup"><span data-stu-id="e28c8-113">See Also</span></span>  
 [<span data-ttu-id="e28c8-114">ICorDebug-интерфейс</span><span class="sxs-lookup"><span data-stu-id="e28c8-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)