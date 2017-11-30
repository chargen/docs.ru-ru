---
title: "Метод ICorDebugModule::GetGlobalVariableValue"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.GetGlobalVariableValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::GetGlobalVariableValue
helpviewer_keywords:
- ICorDebugModule::GetGlobalVariableValue method [.NET Framework debugging]
- GetGlobalVariableValue method [.NET Framework debugging]
ms.assetid: bbc0881c-6a59-41a0-b5ee-2f3d1b71684c
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 00fb56353652e2fdeac7d7b42c030d9105cc9aca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodulegetglobalvariablevalue-method"></a><span data-ttu-id="ac41e-102">Метод ICorDebugModule::GetGlobalVariableValue</span><span class="sxs-lookup"><span data-stu-id="ac41e-102">ICorDebugModule::GetGlobalVariableValue Method</span></span>
<span data-ttu-id="ac41e-103">Получает значение указанной глобальной переменной.</span><span class="sxs-lookup"><span data-stu-id="ac41e-103">Gets the value of the specified global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac41e-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ac41e-104">Syntax</span></span>  
  
```  
HRESULT GetGlobalVariableValue(  
    [in]  mdFieldDef      fieldDef,  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ac41e-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="ac41e-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="ac41e-106">[in] `mdFieldDef` Маркер, который ссылается на метаданные, описывающие глобальной переменной.</span><span class="sxs-lookup"><span data-stu-id="ac41e-106">[in] An `mdFieldDef` token that references the metadata describing the global variable.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="ac41e-107">[out] Указатель на адрес объекта ICorDebugValue, который представляет значение заданной глобальной переменной.</span><span class="sxs-lookup"><span data-stu-id="ac41e-107">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified global variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac41e-108">Требования</span><span class="sxs-lookup"><span data-stu-id="ac41e-108">Requirements</span></span>  
 <span data-ttu-id="ac41e-109">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac41e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac41e-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ac41e-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ac41e-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac41e-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac41e-112">**Версии платформы .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac41e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>