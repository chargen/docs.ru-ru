---
title: "Интерфейс IHostAssemblyStore"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAssemblyStore
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAssemblyStore
helpviewer_keywords: IHostAssemblyStore interface [.NET Framework hosting]
ms.assetid: cccb650f-abe0-41e2-9fd1-b383788eb1f6
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 284afbe73bea28a0aafe8d5e9e030c43be94aea4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="ihostassemblystore-interface"></a><span data-ttu-id="122a7-102">Интерфейс IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="122a7-102">IHostAssemblyStore Interface</span></span>
<span data-ttu-id="122a7-103">Предоставляет методы, позволяющие основному приложению загружать сборки и модули независимо от общеязыковой среды выполнения (CLR).</span><span class="sxs-lookup"><span data-stu-id="122a7-103">Provides methods that allow a host to load assemblies and modules independently of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="122a7-104">Методы</span><span class="sxs-lookup"><span data-stu-id="122a7-104">Methods</span></span>  
  
|<span data-ttu-id="122a7-105">Метод</span><span class="sxs-lookup"><span data-stu-id="122a7-105">Method</span></span>|<span data-ttu-id="122a7-106">Описание</span><span class="sxs-lookup"><span data-stu-id="122a7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="122a7-107">ProvideAssembly-метод</span><span class="sxs-lookup"><span data-stu-id="122a7-107">ProvideAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)|<span data-ttu-id="122a7-108">Возвращает ссылку на сборку, которая не ссылается [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) возвращается из вызова [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span><span class="sxs-lookup"><span data-stu-id="122a7-108">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) returned from a call to [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span>|  
|[<span data-ttu-id="122a7-109">ProvideModule-метод</span><span class="sxs-lookup"><span data-stu-id="122a7-109">ProvideModule Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)|<span data-ttu-id="122a7-110">Разрешает модуль в сборку или связанный файл ресурсов (а не внедренные).</span><span class="sxs-lookup"><span data-stu-id="122a7-110">Resolves a module within an assembly or a linked (not embedded) resource file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="122a7-111">Примечания</span><span class="sxs-lookup"><span data-stu-id="122a7-111">Remarks</span></span>  
 <span data-ttu-id="122a7-112">`IHostAssemblyStore`предоставляет способ для узла для загрузки сборок, эффективно исходя из удостоверения сборки.</span><span class="sxs-lookup"><span data-stu-id="122a7-112">`IHostAssemblyStore` provides a way for a host to load assemblies efficiently based on assembly identity.</span></span> <span data-ttu-id="122a7-113">Основное приложение загружает сборки, возвращая `IStream` экземпляры, которые указывают непосредственно на байты.</span><span class="sxs-lookup"><span data-stu-id="122a7-113">The host loads assemblies by returning `IStream` instances that point directly at the bytes.</span></span>  
  
 <span data-ttu-id="122a7-114">Среда CLR определяет реализовал ли узел `IHostAssemblyStore` путем вызова `IHostAssemblyManager::GetNonHostAssemblyStores` при инициализации.</span><span class="sxs-lookup"><span data-stu-id="122a7-114">The CLR determines whether a host has implemented `IHostAssemblyStore` by calling `IHostAssemblyManager::GetNonHostAssemblyStores` upon initialization.</span></span> <span data-ttu-id="122a7-115">Это позволяет узлу, например, для управления с привязкой к пользовательским сборкам, но полагаются на среду выполнения для привязки к сборкам .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="122a7-115">This allows the host, for example, to control binding to user assemblies, but to rely on the runtime to bind to .NET Framework assemblies.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="122a7-116">В реализации, предоставляя `IHostAssemblyStore`, узел указывает, ее планируется устранить все сборки, на которые не ссылается `ICLRAssemblyReferenceList` , возвращенные `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span><span class="sxs-lookup"><span data-stu-id="122a7-116">In providing an implementation of `IHostAssemblyStore`, the host specifies its intent to resolve all assemblies that are not referenced by the `ICLRAssemblyReferenceList` returned from `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="122a7-117">.NET Framework версии 2.0 не предоставляет способ для узла для загрузки образа в машинном коде для сборки, в соответствии со [генератором машинных образов (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) программы.</span><span class="sxs-lookup"><span data-stu-id="122a7-117">The .NET Framework version 2.0 does not provide a way for the host to load the native image of an assembly, as provided by the [Native Image Generator (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) utility.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="122a7-118">Требования</span><span class="sxs-lookup"><span data-stu-id="122a7-118">Requirements</span></span>  
 <span data-ttu-id="122a7-119">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="122a7-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="122a7-120">**Заголовок:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="122a7-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="122a7-121">**Библиотека:** включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="122a7-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="122a7-122">**Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="122a7-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="122a7-123">См. также</span><span class="sxs-lookup"><span data-stu-id="122a7-123">See Also</span></span>  
 [<span data-ttu-id="122a7-124">ICLRAssemblyReferenceList-интерфейс</span><span class="sxs-lookup"><span data-stu-id="122a7-124">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="122a7-125">Ihostassemblymanager-интерфейс</span><span class="sxs-lookup"><span data-stu-id="122a7-125">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="122a7-126">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="122a7-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)