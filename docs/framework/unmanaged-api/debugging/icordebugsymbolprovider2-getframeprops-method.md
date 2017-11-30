---
title: "Метод ICorDebugSymbolProvider2::GetFrameProps"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3892b8da3286132709792513f055d6ce75bd3fce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="e16af-102">Метод ICorDebugSymbolProvider2::GetFrameProps</span><span class="sxs-lookup"><span data-stu-id="e16af-102">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>
<span data-ttu-id="e16af-103">Возвращает начальный относительный виртуальный адрес метода и родительского фрейма для указанного относительного виртуального адреса кода.</span><span class="sxs-lookup"><span data-stu-id="e16af-103">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e16af-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e16af-104">Syntax</span></span>  
  
```  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e16af-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="e16af-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="e16af-106">[in] Относительный виртуальный адрес кода.</span><span class="sxs-lookup"><span data-stu-id="e16af-106">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="e16af-107">[out] Указатель на начальный относительный виртуальный адрес метода.</span><span class="sxs-lookup"><span data-stu-id="e16af-107">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="e16af-108">[out] Указатель на начальный относительный виртуальный адрес фрейма.</span><span class="sxs-lookup"><span data-stu-id="e16af-108">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e16af-109">Примечания</span><span class="sxs-lookup"><span data-stu-id="e16af-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e16af-110">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="e16af-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e16af-111">Требования</span><span class="sxs-lookup"><span data-stu-id="e16af-111">Requirements</span></span>  
 <span data-ttu-id="e16af-112">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e16af-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e16af-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e16af-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e16af-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e16af-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e16af-115">**Версии платформы .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e16af-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e16af-116">См. также</span><span class="sxs-lookup"><span data-stu-id="e16af-116">See Also</span></span>  
 [<span data-ttu-id="e16af-117">Интерфейс ICorDebugSymbolProvider2</span><span class="sxs-lookup"><span data-stu-id="e16af-117">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 [<span data-ttu-id="e16af-118">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="e16af-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)