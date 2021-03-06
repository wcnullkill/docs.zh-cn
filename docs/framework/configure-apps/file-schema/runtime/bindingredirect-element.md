---
title: "&lt;bindingRedirect&gt;元素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/bindingRedirect
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bindingRedirect
helpviewer_keywords:
- <bindingRedirect> element
- container tags, <bindingRedirect> element
- bindingRedirect element
ms.assetid: 67784ecd-9663-434e-bd6a-26975e447ac0
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3bc8abc019ddb271c8c1246b280be754585bfd61
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="ltbindingredirectgt-element"></a>&lt;bindingRedirect&gt;元素
将一个程序集版本重定向到另一个版本。  
  
 \<configuration>  
\<运行时 >  
\<assemblyBinding >  
\<dependentAssembly >  
\<bindingRedirect >  
  
## <a name="syntax"></a>语法  
  
```xml  
   <bindingRedirect    
oldVersion="existing assembly version"  
newVersion="new assembly version"/>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|`oldVersion`|必需的特性。<br /><br /> 指定最初请求的程序集的版本。 程序集版本号的格式是*major.minor.build.revision*。 该版本号的每个部分的有效值介于 0 和 65535 之间。<br /><br /> 你还可以按下列格式指定版本范围：<br /><br /> *n.n.n.n-n.n.n.n*|  
|`newVersion`|必需的特性。<br /><br /> 指定要使用而不是最初请求的版本格式的程序集的版本： *n.n.n.n*<br /><br /> 此值可以指定 `oldVersion` 之前的版本。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|无||  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|`assemblyBinding`|包含有关程序集版本重定向和程序集位置的信息。|  
|`configuration`|公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。|  
|`dependentAssembly`|封装每个程序集的绑定策略和程序集位置。 为每个程序集使用一个 dependentAssembly 元素。|  
|`runtime`|包含有关程序集绑定和垃圾回收的信息。|  
  
## <a name="remarks"></a>备注  
 在针对具有强名称的程序集生成 .NET Framework 应用程序时，默认情况下，应用程序在运行时使用该版本的程序集，即使提供了新版本也是如此。 但是，你可以将应用程序配置为针对更新版本的程序集运行。 有关运行时如何使用这些文件来确定要使用的程序集版本的详细信息，请参阅[运行时如何定位程序集](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)。  
  
 通过在一个 `bindingRedirect` 元素中包含多个 `dependentAssembly` 元素，你可以重定向多个程序集版本。 你还可从程序集的更新版本重定向到较旧版本。  
  
 应用程序配置文件中的显式程序集绑定重定向需要安全权限。 这适用于对 .NET Framework 程序集和来自第三方的程序集的重定向。 通过设置授予此权限<xref:System.Security.Permissions.SecurityPermissionFlag>标志<xref:System.Security.Permissions.SecurityPermission>。 有关详细信息，请参阅[程序集绑定重定向安全权限](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md)。  
  
## <a name="example"></a>示例  
 下面的示例演示如何将一个程序集版本重定向到另一个版本。  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另请参阅  
 [运行时设置架构](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [配置文件架构](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [重定向程序集版本](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
