---
title: /debug (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- debug compiler switches
- /debug compiler option [Visual Basic]
- -debug compiler option [Visual Basic]
- debug compiler option [Visual Basic]
ms.assetid: c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f1c90b28f1df18e7e0a4f9e22730e1c3476fa650
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="debug-visual-basic"></a>/debug (Visual Basic)
使编译器生成调试信息并将其放在输出文件。  
  
## <a name="syntax"></a>语法  
  
```  
/debug[+ | -]  
' -or-  
/debug:[full | pdbonly]  
```  
  
## <a name="arguments"></a>参数  
  
|术语|定义|  
|---|---|  
|`+` &#124; `-`|可选。 指定`+`或`/debug`使编译器生成调试信息并将其放在.pdb 文件。 指定`-`具有相同的效果与不指定`/debug`。|  
|`full` &#124; `pdbonly`|可选。 指定编译器生成的调试信息的类型。 如果不指定`/debug:pdbonly`，默认值是`full`，从而使你可以将调试器附加到正在运行的程序。 `pdbonly`自变量允许源代码进行调试时在程序启动在调试器中，但仅在正在运行的程序附加到调试器时，才显示程序集语言代码。|  
  
## <a name="remarks"></a>备注  
 使用此选项创建调试版本。 如果不指定`/debug`， `/debug+`，或`/debug:full`，你将无法调试程序的输出文件。  
  
 默认情况下，调试信息不会发出 (`/debug-`)。 若要发出调试信息，请指定`/debug`或`/debug+`。  
  
 有关如何配置应用程序的调试性能的信息，请参阅[令映像更易于调试](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md)。  
  
|在 Visual Studio 中设置 /debug 集成开发环境|  
|---|  
|1.在“解决方案资源管理器” 中选择了项目的情况下，在“项目”  菜单上单击“属性” 。 有关详细信息，请参阅[项目设计器简介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。<br />2.单击“编译”选项卡。<br />3.单击**高级编译选项**。<br />4.修改中的值**生成调试信息**框。|  
  
## <a name="example"></a>示例  
 下面的示例将调试信息放入输出文件`App.exe`。  
  
```  
vbc /debug /out:app.exe test.vb  
```  
  
## <a name="see-also"></a>另请参阅  
 [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)  
 [示例编译命令行](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
