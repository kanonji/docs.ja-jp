---
title: 要素のツリーおよびシリアル化
ms.date: 03/30/2017
f1_keywords:
- AutoGeneratedOrientationPage
helpviewer_keywords:
- element tree [WPF]
- serialization [WPF]
- tree [WPF]
ms.assetid: 8f57e879-180b-421f-b3d0-ac007ff2ce80
ms.openlocfilehash: 9fcaf10bbed23a6c8b8cdc8355a2575574d2207a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542862"
---
# <a name="element-tree-and-serialization"></a>要素のツリーおよびシリアル化
WPF プログラミングの各要素は、多くの場合、ある種の相互ツリー リレーションシップにあります。 たとえば、XAML で作成するアプリケーション UI は、オブジェクト ツリーとして概念化できます。 要素のツリーはさらに、論理ツリーとビジュアル ツリーという 2 つのツリーに分割できます。これらのツリーは異なるものですが、同時に並列関係である場合もありまます。 WPF でのシリアル化には、これら 2 つのツリーの状態およびアプリケーション状態の保存と、ファイル (通常は XAML) へのその書き込みが含まれます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [WPF のツリー](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)  
 [XamlWriter.Save のシリアル化の制限](../../../../docs/framework/wpf/advanced/serialization-limitations-of-xamlwriter-save.md)  
 [オブジェクト ツリーに存在しないオブジェクト要素の初期化](../../../../docs/framework/wpf/advanced/initialization-for-object-elements-not-in-an-object-tree.md)  
 [方法トピック](../../../../docs/framework/wpf/advanced/element-tree-and-serialization-how-to-topics.md)  
  
## <a name="reference"></a>参照  
 <xref:System.Windows.Markup>  
  
 <xref:System.Windows.LogicalTreeHelper>  
  
 <xref:System.Windows.Media.VisualTreeHelper>  
  
## <a name="related-sections"></a>関連項目  
 [WPF アーキテクチャ](../../../../docs/framework/wpf/advanced/wpf-architecture.md)  
  [WPF の XAML](../../../../docs/framework/wpf/advanced/xaml-in-wpf.md)  
  [基本要素](../../../../docs/framework/wpf/advanced/base-elements.md)  
  [プロパティ](../../../../docs/framework/wpf/advanced/properties-wpf.md)  
  [イベント](../../../../docs/framework/wpf/advanced/events-wpf.md)  
  [入力](../../../../docs/framework/wpf/advanced/input-wpf.md)  
  [リソース](../../../../docs/framework/wpf/advanced/resources-wpf.md)  
  [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
  [スレッド モデル](../../../../docs/framework/wpf/advanced/threading-model.md)
