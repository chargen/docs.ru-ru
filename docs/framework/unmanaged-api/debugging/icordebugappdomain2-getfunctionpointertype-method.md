---
title: "Метод ICorDebugAppDomain2::GetFunctionPointerType"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain2.GetFunctionPointerType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain2::GetFunctionPointerType
helpviewer_keywords:
- ICorDebugAppDomain2::GetFunctionPointerType method [.NET Framework debugging]
- GetFunctionPointerType method [.NET Framework debugging]
ms.assetid: 0aba6096-5b38-435c-a72a-86d35db4daef
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 85c07ec6177621b571a376ad58a386e8ed31ea63
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomain2getfunctionpointertype-method"></a><span data-ttu-id="4d789-102">Метод ICorDebugAppDomain2::GetFunctionPointerType</span><span class="sxs-lookup"><span data-stu-id="4d789-102">ICorDebugAppDomain2::GetFunctionPointerType Method</span></span>
<span data-ttu-id="4d789-103">Возвращает указатель на функцию с заданной подписью.</span><span class="sxs-lookup"><span data-stu-id="4d789-103">Gets a pointer to a function that has a given signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d789-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4d789-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionPointerType (  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType   *ppTypeArgs[],  
    [out] ICorDebugType                      **ppType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4d789-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="4d789-105">Parameters</span></span>  
 `nTypeArgs`  
 <span data-ttu-id="4d789-106">[in] Количество аргументов типа для функции.</span><span class="sxs-lookup"><span data-stu-id="4d789-106">[in] The number of type arguments for the function.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="4d789-107">[in] Массив указателей, каждый из которых указывает на объект ICorDebugType, представляющий аргумент типа функции.</span><span class="sxs-lookup"><span data-stu-id="4d789-107">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument of the function.</span></span> <span data-ttu-id="4d789-108">Первый элемент — тип возвращаемого значения; все другие элементы — это тип параметра.</span><span class="sxs-lookup"><span data-stu-id="4d789-108">The first element is the return type; each of the other elements is a parameter type.</span></span>  
  
 `ppType`  
 <span data-ttu-id="4d789-109">[out] Указатель на адрес `ICorDebugType` объект, который представляет указатель на функцию.</span><span class="sxs-lookup"><span data-stu-id="4d789-109">[out] A pointer to the address of an `ICorDebugType` object that represents the pointer to the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d789-110">Требования</span><span class="sxs-lookup"><span data-stu-id="4d789-110">Requirements</span></span>  
 <span data-ttu-id="4d789-111">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d789-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d789-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4d789-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4d789-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4d789-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d789-114">**Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d789-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>