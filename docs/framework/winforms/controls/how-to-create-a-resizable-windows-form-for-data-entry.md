---
title: '方法 : データ入力用のサイズ変更可能な Windows フォームを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- layout [Windows Forms], resizing
- forms [Windows Forms], creating resizable
- Windows Forms, resizable
ms.assetid: babdf198-404c-485d-a914-ed370c6ecd99
ms.openlocfilehash: a319fba43c6735cd5552dd71d1fb614a6192da97
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/01/2018
ms.locfileid: "43384818"
---
# <a name="how-to-create-a-resizable-windows-form-for-data-entry"></a>方法 : データ入力用のサイズ変更可能な Windows フォームを作成する
レイアウトが優れていると、その親フォームの寸法の変更に柔軟に対応できます。 <xref:System.Windows.Forms.TableLayoutPanel> コントロールを使用すると、フォームの寸法の変更に応じて一貫した方法でコントロールの位置とサイズが変更されるように、フォームのレイアウトを調整できます。 <xref:System.Windows.Forms.TableLayoutPanel> コントロールは、コントロールの内容の変更によってレイアウトの変更が生じる場合にも便利です。 この手順で説明するプロセスは、Visual Studio 環境内で実行できます。  「[チュートリアル: データ入力用のサイズ変更可能な Windows フォームの作成](https://msdn.microsoft.com/library/991eahec\(v=vs.110\))」も参照してください。  
  
## <a name="example"></a>例  
 ユーザーによるフォームのサイズ変更に適切に対応するレイアウトを <xref:System.Windows.Forms.TableLayoutPanel> コントロールを使用して作成する方法を次の例に示します。 また、ローカリゼーションに適切に対応するレイアウトも示します。  
  
 [!code-cpp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/cpp/basicdataentryform.cpp#1)]
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/CS/basicdataentryform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/VB/basicdataentryform.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System、System.Data、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。  
  
 コマンドラインからこの例を Visual Basic または Visual c# の構築方法の詳細については、次を参照してください。 [、コマンドラインからビルドする](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)します。 新しいプロジェクトにコードを貼り付けることによって、この例では、Visual Studio を構築することもできます。  「[方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [方法: TableLayoutPanel コントロールで子コントロールを固定およびドッキングする](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [方法: ローカリゼーションに対応した Windows フォーム レイアウトをデザインする](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 [Microsoft Windows ユーザー エクスペリエンス、Official Guidelines for ユーザー インターフェイス開発者および設計者です。Redmond、WA: Microsoft Press、1999 年。(USBN: 0-7356-0566-1)](https://www.microsoft.com/mspress/southpacific/books/book11588.htm)
