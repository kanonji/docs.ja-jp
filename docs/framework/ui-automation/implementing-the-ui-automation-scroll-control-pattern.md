---
title: UI オートメーション Scroll コントロール パターンの実装
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Scroll control pattern
- control patterns, Scroll
- Scroll control pattern
ms.assetid: 73d64242-6cbb-424c-92dd-dc69530b7899
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 2a32d0684aa42eb5d12f200541f6daf22d3989cc
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/01/2018
ms.locfileid: "43389329"
---
# <a name="implementing-the-ui-automation-scroll-control-pattern"></a>UI オートメーション Scroll コントロール パターンの実装
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 に関する最新情報については[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]を参照してください[Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746)します。  
  
 このトピックでは、イベントおよびプロパティに関する情報など、 <xref:System.Windows.Automation.Provider.IScrollProvider>の実装のためのガイドラインと規則について説明します。 その他のリファレンスへのリンクは、トピックの最後に記載します。  
  
 <xref:System.Windows.Automation.ScrollPattern> コントロール パターンは、子オブジェクトのコレクションのスクロール可能なコンテナーとして機能するコントロールをサポートするために使用します。 通常は、スクロール バーを使用してスクロール機能をサポートするためにコントロールが必要ですが、ここでは必要ありません。  
  
 ![スクロール バーのないコントロールをスクロールします。](../../../docs/framework/ui-automation/media/uia-scrollpattern-without-scrollbars.PNG "UIA_ScrollPattern_Without_Scrollbars")  
スクロール バーを使用しないスクロール コントロールの例  
  
 このコントロールを実装するコントロールの例については、「 [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)」を参照してください。  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>実装のガイドラインと規則  
 スクロール コントロール パターンを実装する場合は、次のガイドラインと規則に留意してください。  
  
-   このコントロールの子は <xref:System.Windows.Automation.Provider.IScrollItemProvider>を実装する必要があります。  
  
-   コンテナー コントロールのスクロール バーは <xref:System.Windows.Automation.ScrollPattern> コントロール パターンをサポートしません。 代わりに、 <xref:System.Windows.Automation.RangeValuePattern> コントロール パターンをサポートする必要があります。  
  
-   スクロールをパーセンテージで測定する場合は、スクロール目盛りに関連するすべての値または量を 0 ～ 100 の範囲に正規化する必要があります。  
  
-   <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> と <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> は <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>とは無関係です。  
  
-   場合<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>  =  `false`し<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>100% に設定する必要がありますと<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>に設定する必要があります<xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>します。 同様に、 <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> = `false` の場合は、 <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> を 100% に設定し、 <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> を <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>」をご覧ください。 これにより、UI オートメーション クライアント内でこれらのプロパティ値を使用する、<xref:System.Windows.Automation.ScrollPattern.SetScrollPercent%2A>メソッドを回避しながら、[競合状態](https://support.microsoft.com/default.aspx?scid=kb;en-us;317723)スクロールがアクティブ化される方向をクライアントに関心がない場合。  
  
-   <xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalScrollPercent%2A> はロケール固有です。 HorizontalScrollPercent = 100.0 の設定では、左から右に読む英語などの言語の場合、右端に相当する位置にコントロールのスクロール位置を設定する必要があります。 また、右から左に読むアラビア語などの言語の場合は、HorizontalScrollPercent = 100.0 の設定でスクロール位置を左端の位置に設定する必要があります。  
  
<a name="Required_Members_for_IScrollProvider"></a>   
## <a name="required-members-for-iscrollprovider"></a>IScrollProvider の必須メンバー  
 <xref:System.Windows.Automation.Provider.IScrollProvider>の実装には、次のプロパティとメソッドが必要です。  
  
|必須メンバー|メンバーの型|メモ|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalScrollPercent%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticalScrollPercent%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalViewSize%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticalViewSize%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontallyScrollable%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticallyScrollable%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A>|メソッド|なし|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>|メソッド|なし|  
  
 このコントロール パターンには、関連するイベントがありません。  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>例外  
 プロバイダーは、次の例外をスローする必要があります。  
  
|例外の種類|条件|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|コントロールが水平または垂直スクロールの場合にだけ<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A> の値をサポートするはずが、 <xref:System.Windows.Automation.ScrollAmount.SmallIncrement> の値が渡された場合に、 <xref:System.Windows.Automation.ScrollAmount.LargeIncrement> がこの例外をスローします。|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> は、倍精度浮動小数点型に変換できない値が渡された場合に、この例外をスローします。|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> は、100 を超える値または 0 未満の値が渡された場合に、この例外をスローします ( <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>に相当する -1 を除く)。|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A> と <xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> はどちらも、サポートされていない方向にスクロールされたときに、この例外をスローします。|  
  
## <a name="see-also"></a>関連項目  
 [UI Automation コントロール パターンの概要](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [UI オートメーション プロバイダーでのコントロール パターンのサポート](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [クライアントの UI オートメーション コントロール パターン](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [UI Automation ツリーの概要](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [UI オートメーションにおけるキャッシュの使用](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
