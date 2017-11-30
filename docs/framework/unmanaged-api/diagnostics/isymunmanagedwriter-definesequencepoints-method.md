---
title: "Метод ISymUnmanagedWriter::DefineSequencePoints"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.DefineSequencePoints
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::DefineSequencePoints
helpviewer_keywords:
- DefineSequencePoints method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineSequencePoints method [.NET Framework debugging]
ms.assetid: 64202baf-be6b-40ba-8162-8cc6c0c9b8e1
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 836774114798324ac16d3263e58dd56665a9aa49
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a><span data-ttu-id="5a2d7-102">Метод ISymUnmanagedWriter::DefineSequencePoints</span><span class="sxs-lookup"><span data-stu-id="5a2d7-102">ISymUnmanagedWriter::DefineSequencePoints Method</span></span>
<span data-ttu-id="5a2d7-103">Определяет группу точек следования в текущем методе.</span><span class="sxs-lookup"><span data-stu-id="5a2d7-103">Defines a group of sequence points within the current method.</span></span> <span data-ttu-id="5a2d7-104">Каждая Начальная строка и начальный столбец определяют начало оператора в методе.</span><span class="sxs-lookup"><span data-stu-id="5a2d7-104">Each starting line and starting column define the start of a statement within a method.</span></span> <span data-ttu-id="5a2d7-105">Каждая конечная строка и конечный столбец определяют конец оператора в методе.</span><span class="sxs-lookup"><span data-stu-id="5a2d7-105">Each ending line and ending column define the end of a statement within a method.</span></span> <span data-ttu-id="5a2d7-106">Массивы должны быть упорядочены по возрастанию смещений.</span><span class="sxs-lookup"><span data-stu-id="5a2d7-106">The arrays should be sorted in increasing order of offsets.</span></span> <span data-ttu-id="5a2d7-107">Смещение всегда отсчитывается от начала метода, в байтах.</span><span class="sxs-lookup"><span data-stu-id="5a2d7-107">The offset is always measured from the start of the method, in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a2d7-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5a2d7-108">Syntax</span></span>  
  
```  
HRESULT DefineSequencePoints(  
    [in] ISymUnmanagedDocumentWriter*  document,  
    [in] ULONG32 spCount,  
    [in, size_is(spCount)] ULONG32     offsets[],  
    [in, size_is(spCount)] ULONG32     lines[],  
    [in, size_is(spCount)] ULONG32     columns[],  
    [in, size_is(spCount)] ULONG32     endLines[],  
    [in, size_is(spCount)] ULONG32     endColumns[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5a2d7-109">Параметры</span><span class="sxs-lookup"><span data-stu-id="5a2d7-109">Parameters</span></span>  
 `document`  
 <span data-ttu-id="5a2d7-110">[in] Объект документа, для которого определяются точки следования.</span><span class="sxs-lookup"><span data-stu-id="5a2d7-110">[in] The document object for which the sequence points are being defined.</span></span>  
  
 `spCount`  
 <span data-ttu-id="5a2d7-111">[in] Объект `ULONG32` , которое обозначает размер каждого из `offsets`, `lines`, `columns`, `endLines`, и `endColumns` буферов.</span><span class="sxs-lookup"><span data-stu-id="5a2d7-111">[in] A `ULONG32` that that indicates the size of each of the `offsets`, `lines`, `columns`, `endLines`, and `endColumns` buffers.</span></span>  
  
 `offsets`  
 <span data-ttu-id="5a2d7-112">[in] Смещение точек следования определяются от начала метода.</span><span class="sxs-lookup"><span data-stu-id="5a2d7-112">[in] The offset of the sequence points measured from the beginning of the method.</span></span>  
  
 `lines`  
 <span data-ttu-id="5a2d7-113">[in] Номера начальной строки точки следования.</span><span class="sxs-lookup"><span data-stu-id="5a2d7-113">[in] The starting line numbers of the sequence points.</span></span>  
  
 `columns`  
 <span data-ttu-id="5a2d7-114">[in] Начальный номера столбцов точек следования.</span><span class="sxs-lookup"><span data-stu-id="5a2d7-114">[in] The starting column numbers of the sequence points.</span></span>  
  
 `endLines`  
 <span data-ttu-id="5a2d7-115">[in] Номера конечных строки точки следования.</span><span class="sxs-lookup"><span data-stu-id="5a2d7-115">[in] The ending line numbers of the sequence points.</span></span> <span data-ttu-id="5a2d7-116">Этот параметр является необязательным.</span><span class="sxs-lookup"><span data-stu-id="5a2d7-116">This parameter is optional.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="5a2d7-117">[in] Номера конечных столбцов точек следования.</span><span class="sxs-lookup"><span data-stu-id="5a2d7-117">[in] The ending column numbers of the sequence points.</span></span> <span data-ttu-id="5a2d7-118">Этот параметр является необязательным.</span><span class="sxs-lookup"><span data-stu-id="5a2d7-118">This parameter is optional.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5a2d7-119">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="5a2d7-119">Return Value</span></span>  
 <span data-ttu-id="5a2d7-120">Значение S_OK, если метод выполнен успешно; в противном случае — значение E_FAIL или другим кодом ошибки.</span><span class="sxs-lookup"><span data-stu-id="5a2d7-120">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a2d7-121">Требования</span><span class="sxs-lookup"><span data-stu-id="5a2d7-121">Requirements</span></span>  
 <span data-ttu-id="5a2d7-122">**Заголовок:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5a2d7-122">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a2d7-123">См. также</span><span class="sxs-lookup"><span data-stu-id="5a2d7-123">See Also</span></span>  
 [<span data-ttu-id="5a2d7-124">ISymUnmanagedWriter-интерфейс</span><span class="sxs-lookup"><span data-stu-id="5a2d7-124">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)