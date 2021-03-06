---
title: Метод ICorDebugManagedCallback2::ExceptionUnwind
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.ExceptionUnwind
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind
helpviewer_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind method [.NET Framework debugging]
- ExceptionUnwind method [.NET Framework debugging]
ms.assetid: aaf5938d-179c-4eaa-8d35-8523a4fadded
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 92c4f488dcdc5712dcd2632f489fb0cd65d05ee6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmanagedcallback2exceptionunwind-method"></a>Метод ICorDebugManagedCallback2::ExceptionUnwind
Предоставляет уведомление о состоянии во время процесса очистки исключения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT ExceptionUnwind (  
    [in] ICorDebugAppDomain                  *pAppDomain,  
    [in] ICorDebugThread                     *pThread,  
    [in] CorDebugExceptionUnwindCallbackType  dwEventType,  
    [in] DWORD                                dwFlags  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pAppDomain`  
 [in] Указатель на объект ICorDebugAppDomain, который представляет домен приложения, содержащий поток, в котором возникло исключение.  
  
 `pThread`  
 [in] Указатель на объект ICorDebugThread, представляющий поток, в котором возникло исключение.  
  
 `dwEventType`  
 [in] Значение перечисления CorDebugExceptionUnwindCallbackType, который указывает событие, о котором обратный вызов во время фазы перемотки.  
  
 `dwFlags`  
 [in] Значение [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) перечисления, в котором указываются дополнительные сведения об исключении.  
  
## <a name="remarks"></a>Примечания  
 `ExceptionUnwind` вызывается в различных точках во время фазы перемотки процесс обработки исключений. `ExceptionUnwind` можно вызывать несколько раз во время одного исключения.  
  
 Если `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, указатель инструкций будет в конечном кадре потока в точке последовательности (это может быть несколько инструкций до) инструкцией, вызвавшей исключение.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Интерфейс ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [Интерфейс ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
