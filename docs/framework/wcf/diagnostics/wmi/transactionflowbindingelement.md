---
title: TransactionFlowBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fa5394e874e35b80b01796642e18d69c71e867dc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2017
---
# <a name="transactionflowbindingelement"></a>TransactionFlowBindingElement
TransactionFlowBindingElement  
  
## <a name="syntax"></a>语法  
  
```  
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a>方法  
 TransactionFlowBindingElement 类未定义任何方法。  
  
## <a name="properties"></a>属性  
 TransactionFlowBindingElement 类具有以下属性：  
  
### <a name="issuedtokens"></a>IssuedTokens  
 数据类型：String  
  
 访问类型：只读  
  
 指定对已颁发的安全令牌标头（来自 WS-Trust 的 IssuedTokens）的要求。  
  
### <a name="transactionprotocol"></a>TransactionProtocol  
 数据类型：String  
  
 访问类型：只读  
  
 对事务进行流处理时使用的事务处理协议。  
  
### <a name="transactions"></a>事务  
 数据类型：Boolean  
  
 访问类型：只读  
  
 指示是否支持传入事务。  
  
## <a name="requirements"></a>要求  
  
|MOF|已在 Servicemodel.mof 中声明。|  
|---------|-----------------------------------|  
|命名空间|已在 root\ServiceModel 中定义|  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
