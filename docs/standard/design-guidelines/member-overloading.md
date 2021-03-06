---
title: メンバーのオーバーロード
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c77f08cd573dc40083718b783ae01233ca00766
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573556"
---
# <a name="member-overloading"></a>メンバーのオーバーロード
メンバーのオーバー ロードでは、数または型のパラメーターでのみが異なる同じ名前を持っていて、同じ型に 2 つ以上のメンバーの作成を意味します。 たとえば、次のようにで、`WriteLine`メソッドはオーバー ロードします。  
  
```  
public static class Console {  
    public void WriteLine();  
    public void WriteLine(string value);  
    public void WriteLine(bool value);  
    ...  
}  
```  
  
 メソッド、コンス トラクター、およびインデックス付きプロパティは、パラメーターを持つことができます、ためメンバーのみをオーバー ロードすることができます。  
  
 オーバー ロードでは、使いやすさ、生産性、および再利用可能なライブラリの読みやすさを向上させるための最も重要な手法の 1 つです。 パラメーターの数のオーバー ロードできるようになりますコンス トラクターとメソッドの単純なバージョンを提供します。 パラメーターの型のオーバー ロードできるようになりますさまざまな種類の選択したセットに対して同じ操作を実行するメンバーに対して同じメンバー名を使用します。  
  
 **✓ DO** 短いオーバー ロードで使用される既定値を示すためにわかりやすいパラメーター名を使用しようとしています。  
  
 **X AVOID** オーバー ロードのパラメーター名は任意で変更します。 1 つのオーバー ロードのパラメーターは、別のオーバー ロードのパラメーターと同じ入力を表している場合、パラメーターは、同じ名前を持つ必要があります。  
  
 **X AVOID** メンバーをオーバー ロードされているのパラメーターの順序で一貫していません。 同じ名前のパラメーターは、すべてのオーバー ロード内の同じ位置に表示されます。  
  
 **✓ DO** (拡張機能が必要な場合)、最長のオーバー ロードだけの仮想を作成します。 短いオーバー ロードは、長いのオーバー ロードにを通じて単に呼び出す必要があります。  
  
 **X DO NOT** 使用`ref`または`out`メンバーをオーバー ロードする修飾子です。  
  
 一部の言語では、次のようにオーバー ロードへの呼び出しを解決できません。 さらに、このようなオーバー ロード通常完全に異なるセマンティクスを持つされずにおそらく必要がありますオーバー ロードが 2 つの異なるメソッド代わりにします。  
  
 **X DO NOT** 同じ位置と類似した種類のパラメーターを使用してまだセマンティクスが異なるオーバー ロードがあります。  
  
 **✓ DO** 許可`null`省略可能な引数に渡されます。  
  
 **✓ DO** メンバーの既定の引数を持つメンバーを定義するのではなく、オーバー ロードを使用します。  
  
 既定の引数は、CLS 準拠ではありません。  
  
 *部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>関連項目  
 [メンバーのデザインのガイドライン](../../../docs/standard/design-guidelines/member.md)  
 [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
