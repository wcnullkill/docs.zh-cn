---
title: "分部（方法）（C# 参考）"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: partialmethod_CSharpKeyword
helpviewer_keywords: partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
caps.latest.revision: "26"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 03962a59d5dbe0146cad9835f81d41c06914795b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="partial-method-c-reference"></a>分部（方法）（C# 参考）
分部方法在分部类型的一部分中定义了签名，并在该类型的另一部分中定义了实现。 通过分部方法，类设计器可提供与事件处理程序类似的方法挂钩，以便开发者决定是否实现。 如果开发者不提供实现，则编译器在编译时删除签名。 以下条件适用于分部方法：  
  
-   分部类型各部分中的签名必须匹配。  
  
-   方法必须返回 void。  
  
-   不允许使用访问修饰符。 分部方法是隐式专用的。  
  
 下列示例显示在分部类的两个部分中定义的分部方法：  
  
 [!code-csharp[csrefKeywordsContextual#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-method_1.cs)]  
  
 有关详细信息，请参阅[分部类和方法](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)。  
  
## <a name="see-also"></a>另请参阅  
 [C# 参考](../../../csharp/language-reference/index.md)  
 [分部（类型）](../../../csharp/language-reference/keywords/partial-type.md)
