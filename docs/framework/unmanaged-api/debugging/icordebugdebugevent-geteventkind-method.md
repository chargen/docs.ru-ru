---
title: "Метод ICorDebugDebugEvent::GetEventKind"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cf3296eafb3e3ff933092240f8f353b2b69a89c3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdebugeventgeteventkind-method"></a><span data-ttu-id="3e852-102">Метод ICorDebugDebugEvent::GetEventKind</span><span class="sxs-lookup"><span data-stu-id="3e852-102">ICorDebugDebugEvent::GetEventKind Method</span></span>
<span data-ttu-id="3e852-103">Указывает тип события, который представляет этот объект `ICorDebugDebugEvent`.</span><span class="sxs-lookup"><span data-stu-id="3e852-103">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e852-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3e852-104">Syntax</span></span>  
  
```  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3e852-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="3e852-105">Parameters</span></span>  
 <span data-ttu-id="3e852-106">pDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="3e852-106">pDebugEventKind</span></span>  
 <span data-ttu-id="3e852-107">Указатель на [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) член перечисления, указывающее тип события.</span><span class="sxs-lookup"><span data-stu-id="3e852-107">A pointer to a [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) enumeration member that indicates the type of event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e852-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="3e852-108">Remarks</span></span>  
 <span data-ttu-id="3e852-109">На основе значения `pDebugEventKind` можно вызвать `QueryInterface`, чтобы получить более точный интерфейс событий отладки, содержащий дополнительные данные.</span><span class="sxs-lookup"><span data-stu-id="3e852-109">Based on the value of `pDebugEventKind`, you can call `QueryInterface` to get a more precise debug event interface that has additional data.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3e852-110">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="3e852-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e852-111">Требования</span><span class="sxs-lookup"><span data-stu-id="3e852-111">Requirements</span></span>  
 <span data-ttu-id="3e852-112">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e852-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e852-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3e852-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3e852-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e852-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e852-115">**Версии платформы .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e852-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e852-116">См. также</span><span class="sxs-lookup"><span data-stu-id="3e852-116">See Also</span></span>  
 [<span data-ttu-id="3e852-117">Интерфейс ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="3e852-117">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 [<span data-ttu-id="3e852-118">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="3e852-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)