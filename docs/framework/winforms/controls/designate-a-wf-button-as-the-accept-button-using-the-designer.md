---
title: '方法 : デザイナーを使用して Windows フォームの Button コントロールを承認ボタンとして指定する'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: a1da0590-755f-49f2-aca7-609fac6351bf
ms.openlocfilehash: ca049e86ab53fbd84cb24e81b0a850050ec2823f
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/30/2018
ms.locfileid: "43254967"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button-using-the-designer"></a>方法 : デザイナーを使用して Windows フォームの Button コントロールを承認ボタンとして指定する
任意の Windows フォームで指定することができます、<xref:System.Windows.Forms.Button>コントロールを承認ボタン、既定のボタンとも呼ばれます。 ユーザーが ENTER キーを押すと、フォームの他のコントロールにフォーカスがあるの既定のボタンがクリックされました。 フォーカスを持つコントロールが別のボタン例外:、フォーカスのあるボタンをクリックする場合、-複数行テキスト ボックス、または ENTER キーをトラップするカスタム コントロール。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-designate-the-accept-button"></a>同意する ボタンを指定するには  
  
1.  ボタンが存在するフォームを選択します。  
  
2.  **プロパティ**ウィンドウで、設定フォームの<xref:System.Windows.Forms.Form.AcceptButton%2A>プロパティを<xref:System.Windows.Forms.Button>コントロールの名前。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.Form.AcceptButton%2A>  
 [Button コントロールの概要](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [Windows フォームの Button コントロールを選択する方法](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [方法: Windows フォームのボタンのクリックに応答する](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [方法: デザイナーを使用して Windows フォームの Button コントロールをキャンセル ボタンとして指定する](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-cancel-button-using-the-designer.md)  
 [Button コントロール](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
