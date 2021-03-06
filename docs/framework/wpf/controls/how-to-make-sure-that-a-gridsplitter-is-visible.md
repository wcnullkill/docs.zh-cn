---
title: "如何：确保 GridSplitter 可见"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: GridSplitter control [WPF], ensuring visibility of
ms.assetid: 0a62a964-89c8-48f0-9023-5df721a8cf47
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e8692d356b1b20c7405b4478cef1d16c173389ce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-sure-that-a-gridsplitter-is-visible"></a>如何：确保 GridSplitter 可见
此示例演示如何确保<xref:System.Windows.Controls.GridSplitter>通过中的其他控件未隐藏控件<xref:System.Windows.Controls.Grid>。  
  
## <a name="example"></a>示例  
 <xref:System.Windows.Controls.Panel.Children%2A>的<xref:System.Windows.Controls.Grid>中标记或代码中定义的顺序呈现控件。 <xref:System.Windows.Controls.GridSplitter>如果你没有定义它们中的最后一个元素，可以由其他控件隐藏控件<xref:System.Windows.Controls.Panel.Children%2A>集合或如果你为提供其他控制更高<xref:System.Windows.Controls.Panel.ZIndexProperty>。  
  
 若要防止隐藏<xref:System.Windows.Controls.GridSplitter>控件，执行下列操作之一。  
  
-   请确保<xref:System.Windows.Controls.GridSplitter>控件是最后<xref:System.Windows.Controls.Panel.Children%2A>添加到<xref:System.Windows.Controls.Grid>。 下面的示例演示<xref:System.Windows.Controls.GridSplitter>中的最后一个元素<xref:System.Windows.Controls.Panel.Children%2A>集合<xref:System.Windows.Controls.Grid>。  
  
 [!code-xaml[GridSplitterSnips#GridSplitterLastChild](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterlastchild)]  
  
-   设置<xref:System.Windows.Controls.Panel.ZIndexProperty>上<xref:System.Windows.Controls.GridSplitter>得高于的控件，否则将其隐藏。 以下示例给出了<xref:System.Windows.Controls.GridSplitter>控制更高<xref:System.Windows.Controls.Panel.ZIndexProperty>比<xref:System.Windows.Controls.Button>控件。  
  
 [!code-xaml[GridSplitterSnips#GridSplitterZIndex](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterzindex)]  
  
-   否则将隐藏在控件上设置边距<xref:System.Windows.Controls.GridSplitter>以便<xref:System.Windows.Controls.GridSplitter>公开。 下面的示例设置边距上的控件，否则将覆盖和隐藏<xref:System.Windows.Controls.GridSplitter>。  
  
 [!code-xaml[GridSplitterSnips#GridSplitterMargin](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplittermargin)]  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.Windows.Controls.GridSplitter>  
 [操作说明主题](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
