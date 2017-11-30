---
title: "ICorProfilerCallback4::ReJITCompilationFinished 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4.ReJITCompilationFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4::ReJITCompilationFinished
helpviewer_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished method [.NET Framework profiling]
- ReJITCompilationFinished method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 3b5cff02-2005-44eb-a2bc-50214c4b0e1d
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 768c77a91c072cadc2975d9dde704c134e719220
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback4rejitcompilationfinished-method"></a><span data-ttu-id="7673b-102">ICorProfilerCallback4::ReJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="7673b-102">ICorProfilerCallback4::ReJITCompilationFinished Method</span></span>
<span data-ttu-id="7673b-103">通知探查器在实时 (JIT) 编译器已完成重新编译函数。</span><span class="sxs-lookup"><span data-stu-id="7673b-103">Notifies the profiler that the just-in-time (JIT) compiler has finished recompiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7673b-104">语法</span><span class="sxs-lookup"><span data-stu-id="7673b-104">Syntax</span></span>  
  
```  
HRESULT ReJITCompilationFinished(  
    [in] FunctionID functionId,    [in] ReJITID rejitId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7673b-105">参数</span><span class="sxs-lookup"><span data-stu-id="7673b-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="7673b-106">[in]已重新编译的函数 ID。</span><span class="sxs-lookup"><span data-stu-id="7673b-106">[in] The ID of the function that was recompiled.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="7673b-107">[in] JIT 重新编译的函数的标识。</span><span class="sxs-lookup"><span data-stu-id="7673b-107">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="7673b-108">[in]一个值，该值指示是否已成功 JIT 重新编译。</span><span class="sxs-lookup"><span data-stu-id="7673b-108">[in] A value that indicates whether the JIT recompilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="7673b-109">[in]`true`以指示阻止可能导致运行时等待从此回调; 中返回调用线程`false`以指示，阻止将不会影响运行时该操作。</span><span class="sxs-lookup"><span data-stu-id="7673b-109">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  
  
 <span data-ttu-id="7673b-110">值为`true`不损害运行时，但可能会影响分析结果。</span><span class="sxs-lookup"><span data-stu-id="7673b-110">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7673b-111">要求</span><span class="sxs-lookup"><span data-stu-id="7673b-111">Requirements</span></span>  
 <span data-ttu-id="7673b-112">**平台：**请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7673b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7673b-113">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7673b-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7673b-114">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7673b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7673b-115">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7673b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7673b-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7673b-116">See Also</span></span>  
 [<span data-ttu-id="7673b-117">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="7673b-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="7673b-118">ICorProfilerCallback4 接口</span><span class="sxs-lookup"><span data-stu-id="7673b-118">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 [<span data-ttu-id="7673b-119">JITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="7673b-119">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)  
 [<span data-ttu-id="7673b-120">ReJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="7673b-120">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)