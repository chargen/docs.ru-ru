---
title: "Метод IMetaDataImport::GetMethodProps"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetMethodProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetMethodProps
helpviewer_keywords:
- GetMethodProps method [.NET Framework metadata]
- IMetaDataImport::GetMethodProps method [.NET Framework metadata]
ms.assetid: e0667ef7-1d31-4c89-a2d3-d426f023f8d2
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d02369f1e401f49548f4fdb0fc177dc7403654d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetmethodprops-method"></a><span data-ttu-id="b706f-102">Метод IMetaDataImport::GetMethodProps</span><span class="sxs-lookup"><span data-stu-id="b706f-102">IMetaDataImport::GetMethodProps Method</span></span>
<span data-ttu-id="b706f-103">Возвращает метаданные, связанные с методом, на который ссылается указанный токен MethodDef.</span><span class="sxs-lookup"><span data-stu-id="b706f-103">Gets the metadata associated with the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b706f-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b706f-104">Syntax</span></span>  
  
```  
HRESULT GetMethodProps (  
    [in]  mdMethodDef         mb,  
    [out] mdTypeDef           *pClass,  
    [out] LPWSTR              szMethod,  
    [in]  ULONG               cchMethod,  
    [out] ULONG               *pchMethod,  
    [out] DWORD               *pdwAttr,  
    [out] PCCOR_SIGNATURE     *ppvSigBlob,  
    [out] ULONG               *pcbSigBlob,  
    [out] ULONG               *pulCodeRVA,  
    [out] DWORD               *pdwImplFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b706f-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="b706f-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="b706f-106">[in] Токен MethodDef, который представляет метод для возврата метаданных для.</span><span class="sxs-lookup"><span data-stu-id="b706f-106">[in] The MethodDef token that represents the method to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="b706f-107">[out] Указатель на маркер TypeDef, который представляет тип, реализующий метод.</span><span class="sxs-lookup"><span data-stu-id="b706f-107">[out] A Pointer to a TypeDef token that represents the type that implements the method.</span></span>  
  
 `szMethod`  
 <span data-ttu-id="b706f-108">[out] Указатель на буфер, имеет имя метода.</span><span class="sxs-lookup"><span data-stu-id="b706f-108">[out] A Pointer to a buffer that has the method's name.</span></span>  
  
 `cchMethod`  
 <span data-ttu-id="b706f-109">[in] Запрошенный размер `szMethod`.</span><span class="sxs-lookup"><span data-stu-id="b706f-109">[in] The requested size of `szMethod`.</span></span>  
  
 `pchMethod`  
 <span data-ttu-id="b706f-110">[out] Указатель на размер в расширенных символах с `szMethod`, или в случае усечения фактическое число расширенных символов в имени метода.</span><span class="sxs-lookup"><span data-stu-id="b706f-110">[out] A Pointer to the size in wide characters of `szMethod`, or in the case of truncation, the actual number of wide characters in the method name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="b706f-111">[out] Указатель на любой флаги, связанные с методом.</span><span class="sxs-lookup"><span data-stu-id="b706f-111">[out] A pointer to any flags associated with the method.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="b706f-112">[out] Указатель на двоичную подпись метаданных метода.</span><span class="sxs-lookup"><span data-stu-id="b706f-112">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="b706f-113">[out] Указатель на размер в байтах `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="b706f-113">[out] A Pointer to the size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="b706f-114">[out] Указатель на относительный виртуальный адрес метода.</span><span class="sxs-lookup"><span data-stu-id="b706f-114">[out] A pointer to the relative virtual address of the method.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="b706f-115">[out] Указатель на любой флаги реализации метода.</span><span class="sxs-lookup"><span data-stu-id="b706f-115">[out] A pointer to any implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b706f-116">Требования</span><span class="sxs-lookup"><span data-stu-id="b706f-116">Requirements</span></span>  
 <span data-ttu-id="b706f-117">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b706f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b706f-118">**Заголовок:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b706f-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b706f-119">**Библиотека:** включена как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b706f-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b706f-120">**Версии платформы .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b706f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b706f-121">См. также</span><span class="sxs-lookup"><span data-stu-id="b706f-121">See Also</span></span>  
 [<span data-ttu-id="b706f-122">IMetaDataImport-интерфейс</span><span class="sxs-lookup"><span data-stu-id="b706f-122">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="b706f-123">IMetaDataImport2-интерфейс</span><span class="sxs-lookup"><span data-stu-id="b706f-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)