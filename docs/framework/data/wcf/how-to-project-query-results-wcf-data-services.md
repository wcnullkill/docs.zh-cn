---
title: "如何：投影查询结果（WCF 数据服务）"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- projection [WCF Data Services]
- WCF Data Services, projection
- query projection [WCF Data Services]
- WCF Data Services, querying
ms.assetid: 474ac625-8770-43ba-8320-d3315ea9530f
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0b22801f421a551d08c1bac555ee7dcb84d9e2f0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-project-query-results-wcf-data-services"></a>如何：投影查询结果（WCF 数据服务）
投影提供减少查询返回的数据量的机制，方法是指定在响应中仅返回某个实体的某些属性。 你可以对结果执行投影[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]查询通过使用`$select`查询选项或通过使用[选择](~/docs/csharp/language-reference/keywords/select-clause.md)子句 ([选择](~/docs/visual-basic/language-reference/queries/select-clause.md)在 Visual Basic 中) 中的 LINQ 查询。 有关详细信息，请参阅[查询数据服务](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)。  
  
 本主题中的示例使用罗斯文示例数据服务和自动生成的客户端数据服务类。 在完成时创建此服务和客户端数据类[WCF 数据服务快速入门](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)。  
  
## <a name="example"></a>示例  
 下面的示例演示一个 LINQ 查询，该查询将 Customers 实体投影到新的 CustomerAddress 类型，该类型仅包含特定地址属性以及标识属性。 此 `CustomerAddress` 类是在客户端上定义的并且具有客户端库可将它识别为实体类型的特性。  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#selectcustomeraddress)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#selectcustomeraddress)]  
  
## <a name="example"></a>示例  
 下面的示例演示一个 LINQ 查询，该查询将返回的 Customers 实体投影到新的 CustomerAddressNonEntity 类型，该类型仅包含特定地址属性，不包含标识属性。 此 `CustomerAddressNonEntity` 类是在客户端上定义的，但不具有作为实体类型的特性。  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#selectcustomeraddressnonentity)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#selectcustomeraddressnonentity)]  
  
## <a name="example"></a>示例  
 下面的示例演示的定义`CustomerAddress``CustomerAddressNonEntity`前面的示例中使用的类型。  
  
 [!code-csharp[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customeraddress.cs#customeraddressdefinition)]
 [!code-vb[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customeraddress.vb#customeraddressdefinition)]
