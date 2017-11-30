---
title: "ICorDebugHeapValue3::GetThreadOwningMonitorLock 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapValue3.GetThreadOwningMonitorLock
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapValue3::GetThreadOwningMonitorLock
helpviewer_keywords:
- GetThreadOwningMonitorLock method [.NET Framework debugging]
- ICorDebugHeapValue3::GetThreadOwningMonitorLock method [.NET Framework debugging]
ms.assetid: e06fc19d-2cf4-4cad-81a3-137a68af8969
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3571f546f71515a980c5415e568ae85eb0863d42
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a><span data-ttu-id="d136e-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock 方法</span><span class="sxs-lookup"><span data-stu-id="d136e-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock Method</span></span>
<span data-ttu-id="d136e-103">返回拥有此对象的监视器锁的托管的线程。</span><span class="sxs-lookup"><span data-stu-id="d136e-103">Returns the managed thread that owns the monitor lock on this object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d136e-104">语法</span><span class="sxs-lookup"><span data-stu-id="d136e-104">Syntax</span></span>  
  
```  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d136e-105">参数</span><span class="sxs-lookup"><span data-stu-id="d136e-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="d136e-106">[out]拥有此对象的监视器锁的托管的线程。</span><span class="sxs-lookup"><span data-stu-id="d136e-106">[out] The managed thread that owns the monitor lock on this object.</span></span>  
  
 `pAcquisitionCount`  
 <span data-ttu-id="d136e-107">[out]此线程将不得不之前它将返回给正在没有所有者释放锁的次数。</span><span class="sxs-lookup"><span data-stu-id="d136e-107">[out] The number of times this thread would have to release the lock before it returns to being unowned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d136e-108">返回值</span><span class="sxs-lookup"><span data-stu-id="d136e-108">Return Value</span></span>  
 <span data-ttu-id="d136e-109">此方法返回以下特定 HRESULT 以及表示方法失败的 HRESULT 错误。</span><span class="sxs-lookup"><span data-stu-id="d136e-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d136e-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d136e-110">HRESULT</span></span>|<span data-ttu-id="d136e-111">描述</span><span class="sxs-lookup"><span data-stu-id="d136e-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d136e-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="d136e-112">S_OK</span></span>|<span data-ttu-id="d136e-113">该方法已成功完成。</span><span class="sxs-lookup"><span data-stu-id="d136e-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="d136e-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="d136e-114">S_FALSE</span></span>|<span data-ttu-id="d136e-115">没有托管的线程拥有对此对象的监视器锁。</span><span class="sxs-lookup"><span data-stu-id="d136e-115">No managed thread owns the monitor lock on this object.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="d136e-116">异常</span><span class="sxs-lookup"><span data-stu-id="d136e-116">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d136e-117">备注</span><span class="sxs-lookup"><span data-stu-id="d136e-117">Remarks</span></span>  
 <span data-ttu-id="d136e-118">如果托管的线程拥有对此对象的监视器锁：</span><span class="sxs-lookup"><span data-stu-id="d136e-118">If a managed thread owns the monitor lock on this object:</span></span>  
  
-   <span data-ttu-id="d136e-119">该方法返回，则为 S_OK。</span><span class="sxs-lookup"><span data-stu-id="d136e-119">The method returns S_OK.</span></span>  
  
-   <span data-ttu-id="d136e-120">使线程对象在线程退出才有效。</span><span class="sxs-lookup"><span data-stu-id="d136e-120">The thread object is valid until the thread exits.</span></span>  
  
 <span data-ttu-id="d136e-121">如果没有托管的线程拥有对此对象的监视器锁`ppThread`和`pAcquisitionCount`不变，并且该方法返回 S_FALSE。</span><span class="sxs-lookup"><span data-stu-id="d136e-121">If no managed thread owns the monitor lock on this object, `ppThread` and `pAcquisitionCount` are unchanged, and the method returns S_FALSE.</span></span>  
  
 <span data-ttu-id="d136e-122">如果`ppThread`或`pAcquisitionCount`不是有效的指针，结果不可确定。</span><span class="sxs-lookup"><span data-stu-id="d136e-122">If `ppThread` or `pAcquisitionCount` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="d136e-123">出错时，无法确定哪些，如果有的话，线程拥有对此对象的监视器锁该方法将返回一个 HRESULT，指示失败。</span><span class="sxs-lookup"><span data-stu-id="d136e-123">If an error occurs such that it cannot be determined which, if any, thread owns the monitor lock on this object, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d136e-124">要求</span><span class="sxs-lookup"><span data-stu-id="d136e-124">Requirements</span></span>  
 <span data-ttu-id="d136e-125">**平台：**请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d136e-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d136e-126">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d136e-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d136e-127">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d136e-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d136e-128">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d136e-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d136e-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d136e-129">See Also</span></span>  
 [<span data-ttu-id="d136e-130">调试接口</span><span class="sxs-lookup"><span data-stu-id="d136e-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="d136e-131">调试</span><span class="sxs-lookup"><span data-stu-id="d136e-131">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)