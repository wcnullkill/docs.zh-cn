---
title: "如何：在 StackPanel 和 DockPanel 之间进行选择"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], DockPanel
- DockPanel control [WPF], StackPanel control compared to
- StackPanel control [WPF], DockPanel control compared to
- controls [WPF], StackPanel
ms.assetid: f9239086-451f-42e6-81f7-ef89ef349742
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 40d99e090a0599c98560e4102d18d35ee7174259
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-choose-between-stackpanel-and-dockpanel"></a>如何：在 StackPanel 和 DockPanel 之间进行选择
此示例演示如何使用之间进行选择<xref:System.Windows.Controls.StackPanel>或<xref:System.Windows.Controls.DockPanel>时堆栈中的内容<xref:System.Windows.Controls.Panel>。  
  
## <a name="example"></a>示例  
 尽管你可以使用<xref:System.Windows.Controls.DockPanel>或<xref:System.Windows.Controls.StackPanel>以堆叠子元素，这两个控件不始终生成相同的结果。 例如，你将放置子元素的顺序可能会影响中的子元素的大小<xref:System.Windows.Controls.DockPanel>但未显示在<xref:System.Windows.Controls.StackPanel>。 出现此不同的行为是因为<xref:System.Windows.Controls.StackPanel>度量值的方向堆叠在<xref:System.Double>。<xref:System.Double.PositiveInfinity>; 但是，<xref:System.Windows.Controls.DockPanel>测量仅的可用大小。  
  
 下面的示例演示此主要区别<xref:System.Windows.Controls.DockPanel>和<xref:System.Windows.Controls.StackPanel>。  
  
 [!code-cpp[StackPanelOvw4#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.Windows.Controls.StackPanel>  
 <xref:System.Windows.Controls.DockPanel>  
 [面板概述](../../../../docs/framework/wpf/controls/panels-overview.md)
