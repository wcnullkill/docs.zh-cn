---
title: "&lt;assemblyIdentity&gt;元素&lt;运行时&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/assemblyIdentity
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assemblyIdentity
helpviewer_keywords:
- <assemblyIdentity> element
- container tags, <assemblyIdentity> element
- assemblyIdentity element
ms.assetid: cea4d187-6398-4da4-af09-c1abc6a349c1
caps.latest.revision: "17"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 740b08806dff65d3ce1b8de378138c2647944fd4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="ltassemblyidentitygt-element-for-ltruntimegt"></a>&lt;assemblyIdentity&gt;元素&lt;运行时&gt;
包含有关程序集的标识信息。  
  
 \<configuration>  
\<运行时 >  
\<assemblyBinding >  
\<dependentAssembly >  
\<assemblyIdentity >  
  
## <a name="syntax"></a>语法  
  
```xml  
   <assemblyIdentity    
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|`name`|必需的特性。<br /><br /> 程序集的名称|  
|`culture`|可选特性。<br /><br /> 一个字符串，指定的语言和国家/地区的程序集。|  
|`publicKeyToken`|可选特性。<br /><br /> 一个十六进制值，指定的程序集的强名称。|  
|`processorArchitecture`|可选特性。<br /><br /> 指定包含特定于处理器的代码程序集的处理器体系结构的值"x86"、"amd64"、"msil"或"ia64"之一。 值不区分大小写。 如果该特性被赋予任何其他值，整个`<assemblyIdentity>`元素将被忽略。 请参阅<xref:System.Reflection.ProcessorArchitecture>。|  
  
## <a name="processorarchitecture-attribute"></a>processorArchitecture 属性  
  
|值|描述|  
|-----------|-----------------|  
|`amd64`|仅 64 位 AMD 处理器。|  
|`ia64`|仅 64 位 Intel 处理器。|  
|`msil`|特定于处理器和每字位数|  
|`x86`|32 位 Intel 处理器、 是本机或在 64 位平台上的 Windows (WOW) 环境上的 Windows 中。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|`assemblyBinding`|包含有关程序集版本重定向和程序集位置的信息。|  
|`configuration`|公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。|  
|`dependentAssembly`|封装每个程序集的绑定策略和程序集位置。 使用一个`<dependentAssembly>`每个程序集的元素。|  
|`runtime`|包含有关程序集绑定和垃圾回收的信息。|  
  
## <a name="remarks"></a>备注  
 每个 **\<dependentAssembly >**元素都必须有一个 **\<assemblyIdentity >**子元素。  
  
 如果`processorArchitecture`属性是否存在、`<assemblyIdentity>`元素仅适用于具有相应的处理器体系结构的程序集。 如果`processorArchitecture`属性不存在，`<assemblyIdentity>`元素可以应用于任何处理器体系结构包含的程序集。  
  
 下面的示例演示两个程序集具有相同的名称，面向两个不同两个处理器体系结构，以及其版本不维护同步配置文件。当应用程序执行 x86 平台第一个`<assemblyIdentity>`元素得到应用，另一个被忽略。 如果应用程序执行在非 x86 或 ia64 平台上，同时将被忽略。  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"  
                  processorArchitecture="x86" />  
            <bindingRedirect oldVersion= "1.0.0.0"   
                  newVersion="1.1.0.0" />  
         </dependentAssembly>  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"   
                  processorArchitecture="ia64" />  
            <bindingRedirect oldVersion="1.0.0.0"   
                  newVersion="2.0.0.0" />  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 如果配置文件包含`<assemblyIdentity>`元素没有`processorArchitecture`属性，然后在不包含相匹配的平台，而无需元素的元素`processorArchitecture`使用属性。  
  
## <a name="example"></a>示例  
 下面的示例演示如何提供有关程序集的信息。  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for myAssembly.-->  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另请参阅  
 [运行时设置架构](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [配置文件架构](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [重定向程序集版本](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
