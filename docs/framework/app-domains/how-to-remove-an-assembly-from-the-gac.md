---
title: "方法 : グローバル アセンブリ キャッシュからアセンブリを削除する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アセンブリ [.NET Framework], グローバル アセンブリ キャッシュ"
  - "削除 (グローバル アセンブリ キャッシュ内のアセンブリを)"
  - "GAC (グローバル アセンブリ キャッシュ), 削除 (アセンブリを)"
  - "Gacutil.exe"
  - "グローバル アセンブリ キャッシュ ツール"
  - "グローバル アセンブリ キャッシュ, 削除 (アセンブリを)"
  - "削除 (グローバル アセンブリ キャッシュからアセンブリを)"
  - "厳密な名前を付けたアセンブリ, グローバル アセンブリ キャッシュ"
ms.assetid: acdcc588-b458-436d-876c-726de68244c1
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : グローバル アセンブリ キャッシュからアセンブリを削除する
グローバル アセンブリ キャッシュ \(GAC\) からアセンブリを削除するには、次の 2 つの方法があります。  
  
-   [グローバル アセンブリ キャッシュ ツール \(Gacutil.exe\)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) を使用する方法。  このオプションを使用すると、開発およびテスト時に GAC に配置したアセンブリをアンインストールできます。  
  
-   [Windows インストーラー](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx) を使用する方法。  インストール パッケージをテストするとき、そして実稼働システムのために、アセンブリをアンインストールするにはこのオプションを使用する必要があります。  
  
### Gacutil.exe によるアセンブリの削除  
  
1.  コマンド プロンプトに次のコマンドを入力します。  
  
     **gacutil –u** \<*assembly name*\>  
  
     このコマンドで、*assembly name* はグローバル アセンブリ キャッシュから削除されるアセンブリの名前です。  
  
    > [!WARNING]
    >  アセンブリが一部のアプリケーションで引き続き必要となる可能性があるので、Gacutil.exe を使用して実稼働システムのアセンブリを削除しないでください。  代わりに、GAC にインストールされる各アセンブリの参照カウントを保持する Windows インストーラーを使用する必要があります。  
  
 次の例では、`hello.dll` という名前のアセンブリが、グローバル アセンブリ キャッシュから削除されます。  
  
```  
gacutil -u hello  
```  
  
### Windows インストーラーでアセンブリを削除する  
  
1.  **コントロール パネル**の**プログラムと機能**アプリで、アンインストールするアプリを選択します。  インストール パッケージが GAC にアセンブリを配置した場合、それらが別のアプリケーションによって使用されないときは、Windows インストーラーはそれらを削除します。  
  
    > [!NOTE]
    >  Windows インストーラーは、GAC にインストールされたアセンブリの参照カウントを保持します。  アセンブリの参照カウントがゼロになる場合 \(それが Windows インストーラー パッケージによってインストールされたアプリケーションによって使用されないことを示す\) にのみ、アセンブリが GAC から削除されます。  
  
## 参照  
 [アセンブリとグローバル アセンブリ キャッシュの使用](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)   
 [方法: グローバル アセンブリ キャッシュへのアセンブリのインストール](../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)   
 [Gacutil.exe \(グローバル アセンブリ キャッシュ ツール\)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)