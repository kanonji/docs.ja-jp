---
title: 入れ子にされた型
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- types, nested
- public nested types
- type design guidelines, nested types
- nested types
- members [.NET Framework], type
- class library design guidelines [.NET Framework], nested types
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6c0eca851746899654636d36dce679acffc07ef0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573660"
---
# <a name="nested-types"></a>入れ子にされた型
入れ子になった型は、それを囲む型と呼ばれる別の種類のスコープ内で定義された型です。 入れ子になった型は、その外側の型のすべてのメンバーにアクセスします。 たとえば、それを囲む型のすべての先祖で定義されたフィールドを保護して、それを囲む型で定義されてプライベート フィールドにアクセス権を持ちます。  
  
 一般に、入れ子にされた型慎重に使用します。 直接呼び出すべきではないいくつかの理由があります。 一部の開発者は、概念を完全に習熟していません。 これらの開発者、たとえば、問題がありますの入れ子にされた型の変数を宣言する構文を使用します。 入れ子にされた型は、外側の型とも非常に密接に結び付いているし、そのため、汎用的な型にすることが適していません。  
  
 入れ子にされた型は、その外側の型の実装の詳細をモデル化に最適です。 エンドユーザーは、入れ子にされた型の変数を宣言することはほとんどなく、入れ子にされた型を明示的にインスタンス化することはほぼありません必要があります。 たとえば、コレクションの列挙子は、そのコレクションの入れ子にされた型を指定できます。 列挙子は通常、それを囲む型でインスタンス化され、多くの言語では、foreach ステートメントをサポート、列挙子変数まれであるために、宣言するのには、エンドユーザーがします。  
  
 **✓ DO** 入れ子にされた型とその外側の型間の関係のあるメンバーのアクセシビリティのセマンティクスは次のことをお勧めときに、入れ子にされた型を使用します。  
  
 **X DO NOT** 論理的なグループとしてパブリック入れ子にされた型を使用して構築以外の場合はこの名前空間を使用します。  
  
 **X AVOID** 入れ子にされた型をパブリックに公開します。 唯一の例外は、入れ子にされた型の変数がサブクラスまたはその他の高度なカスタマイズのシナリオなど、まれなシナリオでのみ宣言する必要があるかどうかです。  
  
 **X DO NOT** 型が、含んでいる型の外部で参照されている可能性が高い場合は、入れ子にされた型を使用します。  
  
 たとえば、クラスに定義されたメソッドに渡される列挙型であり、いないクラスに入れ子にされた型として定義すべきです。  
  
 **X DO NOT** クライアント コードでインスタンス化する必要がある場合は、入れ子にされた型を使用します。  型にパブリック コンス トラクターがある場合は、その必要があります可能性があります入れ子にします。  
  
 型が、独自のフレームワーク内の場所を示すためには、型はインスタンス化することができる場合 (できます作成し、使用して、外側の型を使用することがなく破棄)、したがって必要がある入れ子になっていないとします。 内部の型は広く再利用できません、リレーションシップがない場合、外部型の外部で外側の型と責任も負わないものです。  
  
 **X DO NOT** インターフェイスのメンバーとして入れ子にされた型を定義します。 多くの言語は、このような構造をサポートしていません。  
  
 *部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>関連項目  
 [型デザインのガイドライン](../../../docs/standard/design-guidelines/type.md)  
 [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
