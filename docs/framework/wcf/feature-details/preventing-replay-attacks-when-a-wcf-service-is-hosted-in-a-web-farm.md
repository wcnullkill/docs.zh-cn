---
title: "当 Web 场中承载 WCF 服务时防止重放攻击"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c2ed695-7a31-4257-92bd-9e9731b886a5
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 383a93bee7a63bef966f4252ace13105d96ae505
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2017
---
# <a name="preventing-replay-attacks-when-a-wcf-service-is-hosted-in-a-web-farm"></a>当 Web 场中承载 WCF 服务时防止重放攻击
当使用消息安全性时，WCF 通过从传入的消息创建 NONCE 并检查内部 `InMemoryNonceCache` 以查看是否存在生成的 NONCE，从而防止重播攻击。 如果存在，则该消息作为重播被丢弃。 当 WCF 服务承载在 Web 场中时，因为不跨 Web 场中的节点共享 `InMemoryNonceCache`，所以服务易于受重播攻击。  为了缓解这种情况，WCF 4.5 提供了一个可扩展点，使您能够通过从抽象类 <xref:System.ServiceModel.Security.NonceCache> 中派生类来实现您自己的共享 NONCE 缓存。  
  
## <a name="noncecache-implementation"></a>NonceCache 实现  
 若要实现您自己的共享 NONCE 缓存，请从 <xref:System.ServiceModel.Security.NonceCache> 派生类并重写 <xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> 和 <xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A> 方法。 <xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> 将检查缓存中是否存在指定的 NONCE。 <xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A> 将尝试向缓存添加 NONCE。 一旦实现类，您就可以通过对实例进行实例化并将其分配给 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.NonceCache%2A> 来进行客户端重播检测，并分配给  <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NonceCache%2A> 以进行服务器端重播检测，从而将其挂钩。 没有支持此功能的现成配置。  
  
## <a name="see-also"></a>另请参阅  
 [消息安全](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 [SymmetricSecurityBindingElement](../../../../docs/framework/wcf/diagnostics/wmi/symmetricsecuritybindingelement.md)
