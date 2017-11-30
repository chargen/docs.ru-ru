---
title: "Метод ICLRMetaHost::QueryLegacyV2RuntimeBinding"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHost.RequestRuntimeLoadedNotification
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHost::QueryLegacyV2RuntimeBinding
helpviewer_keywords:
- QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
- ICLRMetaHost::QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
ms.assetid: 9929817e-acc9-40b7-960c-598664e04b60
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c273a1690828e37c8f7fcf5071e42e5bb2c58228
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmetahostquerylegacyv2runtimebinding-method"></a><span data-ttu-id="44944-102">Метод ICLRMetaHost::QueryLegacyV2RuntimeBinding</span><span class="sxs-lookup"><span data-stu-id="44944-102">ICLRMetaHost::QueryLegacyV2RuntimeBinding Method</span></span>
<span data-ttu-id="44944-103">Возвращает интерфейс, представляющий среду выполнения, к которому устаревшей политике активации связывается, например, с помощью `useLegacyV2RuntimeActivationPolicy` атрибут [ \<запуска > элемент](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) запись файла конфигурации, напрямую используя Устаревшие интерфейсы API активации или вызывая [ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) метод.</span><span class="sxs-lookup"><span data-stu-id="44944-103">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44944-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="44944-104">Syntax</span></span>  
  
```  
HRESULT QueryLegacyV2RuntimeBinding (  
    [in] REFIID riid,  
    [out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="44944-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="44944-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="44944-106">[in] Единственным допустимым значением для этого параметра является Required.Currently `IID_ICLRRuntimeInfo`.</span><span class="sxs-lookup"><span data-stu-id="44944-106">[in] Required.Currently the only valid value for this parameter is `IID_ICLRRuntimeInfo`.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="44944-107">[out] Обязательный.</span><span class="sxs-lookup"><span data-stu-id="44944-107">[out] Required.</span></span> <span data-ttu-id="44944-108">По возвращении из этого метода содержит указатель на [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) интерфейс, представляющий среду выполнения, которая привязана к устаревшей политике активации.</span><span class="sxs-lookup"><span data-stu-id="44944-108">When this method returns, contains a pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that represents a runtime that has been bound to legacy activation policy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="44944-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="44944-109">Return Value</span></span>  
 <span data-ttu-id="44944-110">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="44944-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="44944-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="44944-111">HRESULT</span></span>|<span data-ttu-id="44944-112">Описание</span><span class="sxs-lookup"><span data-stu-id="44944-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="44944-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="44944-113">S_OK</span></span>|<span data-ttu-id="44944-114">Метод успешно выполнен, и возвращена среда выполнения, которая была привязана к устаревшей политике активации.</span><span class="sxs-lookup"><span data-stu-id="44944-114">The method completed successfully and returned a runtime that was bound to legacy activation policy.</span></span>|  
|<span data-ttu-id="44944-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="44944-115">S_FALSE</span></span>|<span data-ttu-id="44944-116">Метод успешно выполнен, но устаревшая среда выполнения еще не привязана.</span><span class="sxs-lookup"><span data-stu-id="44944-116">The method completed successfully, but a legacy runtime has not yet been bound.</span></span>|  
|<span data-ttu-id="44944-117">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="44944-117">E_NOINTERFACE</span></span>|<span data-ttu-id="44944-118">Метод обнаружил среду выполнения, которая была привязана к устаревшей политике активации, но параметр `riid` не поддерживается этой средой.</span><span class="sxs-lookup"><span data-stu-id="44944-118">The method found a runtime that was bound to legacy activation policy, but `riid` is not supported by that runtime.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44944-119">Примечания</span><span class="sxs-lookup"><span data-stu-id="44944-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44944-120">Требования</span><span class="sxs-lookup"><span data-stu-id="44944-120">Requirements</span></span>  
 <span data-ttu-id="44944-121">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44944-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44944-122">**Заголовок:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="44944-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="44944-123">**Библиотека:** включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="44944-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="44944-124">**Версии платформы .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44944-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44944-125">См. также</span><span class="sxs-lookup"><span data-stu-id="44944-125">See Also</span></span>  
 [<span data-ttu-id="44944-126">ICLRMetaHost-интерфейс</span><span class="sxs-lookup"><span data-stu-id="44944-126">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="44944-127">Размещение</span><span class="sxs-lookup"><span data-stu-id="44944-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)