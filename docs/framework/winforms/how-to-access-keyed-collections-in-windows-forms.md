---
title: "如何：在 Windows 窗体中访问键控集合"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyed collections [Windows Forms]
- collections [Windows Forms], accessing with keys
ms.assetid: b9b79b8b-d9bf-4f8c-b9d6-9578bc3219d3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2bca9b56f37c815bfa9f1520467ae0ae864c14ac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-keyed-collections-in-windows-forms"></a>如何：在 Windows 窗体中访问键控集合
-   可通过键访问单个集合项。 此功能已添加到 Windows 窗体应用程序通常使用的许多集合类。 以下列表显示了一些具有可访问键控的集合的集合类：  
  
-   <xref:System.Windows.Forms.ListView.ListViewItemCollection>  
  
-   <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection>  
  
-   <xref:System.Windows.Forms.Control.ControlCollection>  
  
-   <xref:System.Windows.Forms.TabControl.TabPageCollection>  
  
-   <xref:System.Windows.Forms.TreeNodeCollection>  
  
 与集合中的项关联的密钥通常是项的名称。 下面的过程演示如何使用集合类来执行常见任务。  
  
### <a name="to-find-and-give-focus-to-a-nested-control-in-a-control-collection"></a>若要查找并将焦点移至控件集合中的嵌套控件  
  
-   使用<xref:System.Windows.Forms.Control.ControlCollection.Find%2A>和<xref:System.Windows.Forms.Control.Focus%2A>方法以指定要查找并设置焦点的控件的名称。  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#1)]  
  
### <a name="to-access-an-image-in-an-image-collection"></a>若要访问图像集合中的图像  
  
-   使用<xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A>属性来指定想要访问的图像的名称。  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#2)]  
  
### <a name="to-set-a-tab-page-as-the-selected-tab"></a>要设置为已选定选项卡的选项卡页  
  
-   使用<xref:System.Windows.Forms.TabControl.SelectedTab%2A>属性连同<xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A>属性来指定要将设置为已选定选项卡的选项卡页的名称。  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#3)]  
  
## <a name="see-also"></a>另请参阅  
 [Windows 窗体入门](../../../docs/framework/winforms/getting-started-with-windows-forms.md)  
 [如何：使用 Windows 窗体 ImageList 组件添加或删除图像](../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
