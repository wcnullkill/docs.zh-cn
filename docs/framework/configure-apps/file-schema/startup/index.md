---
title: "启动设置架构"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 61ea6d0c974683e73e835720cff48ff84169217e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="startup-settings-schema"></a>启动设置架构
启动设置会指定应运行应用程序的公共语言运行时的版本。  
  
|元素|描述|  
|-------------|-----------------|  
|[\<requiredRuntime>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|指定应用程序仅支持 1.0 版本的公共语言运行时。 使用 1.1 版运行时生成的应用程序应使用 **\<supportedRuntime>** 元素。|  
|[\<supportedRuntime>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|指定应用程序支持的公共语言运行时版本。|  
|[\<startup>](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)|包含 **\<requiredRuntime>** 和 **\<supportedRuntime>** 元素。|  
  
## <a name="see-also"></a>另请参阅  
 [配置文件架构](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<PaveOver> 指定要使用的运行时版本](http://msdn.microsoft.com/en-us/c376208d-980d-42b4-865b-fbe0d9cc97c2)
