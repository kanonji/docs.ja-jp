---
title: '方法: ワークフロー アプリケーションからサービスにアクセスする'
ms.date: 03/30/2017
ms.assetid: 925ef8ea-5550-4c9d-bb7b-209e20c280ad
ms.openlocfilehash: 5bc18b446d4bf818c874839a421793a997ddc543
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/01/2018
ms.locfileid: "43395932"
---
# <a name="how-to-access-a-service-from-a-workflow-application"></a>方法: ワークフロー アプリケーションからサービスにアクセスする
このトピックでは、ワークフロー コンソール アプリケーションからワークフロー サービスを呼び出す方法について説明します。 完了に依存、[方法: メッセージング アクティビティでワークフロー サービスを作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)トピック。 このトピックでは、ワークフロー アプリケーションからワークフロー サービスを呼び出す方法について説明します、ワークフロー アプリケーションから任意の Windows Communication Foundation (WCF) サービスを呼び出す場合と同じ方法を使用できます。

### <a name="create-a-workflow-console-application-project"></a>ワークフロー コンソール アプリケーション プロジェクトの作成

1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を起動します。

2.  作成した MyWFService プロジェクトを読み込む、[方法: メッセージング アクティビティでワークフロー サービスを作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)トピック。

3.  右クリックして、 **MyWFService**でソリューション、**ソリューション エクスプ ローラー**選択**追加**、**新しいプロジェクト**します。 選択**ワークフロー**で、**インストールされたテンプレート**と**ワークフロー コンソール アプリケーション**プロジェクトの種類の一覧から。 次の図に示すように、プロジェクトに MyWFClient という名前を付け、既定の場所を使用します。

     ![新しいプロジェクト ダイアログ ボックスを追加](../../../../docs/framework/wcf/feature-details/media/addnewprojectdlg.JPG "AddNewProjectDlg")

     をクリックして、 **OK**を閉じる、**新しいプロジェクト ダイアログの追加**します。

4.  プロジェクトが作成されると、Workflow1.xaml ファイルがデザイナーで開かれます。 をクリックして、**ツールボックス** タブを開くし、ツールボックス ウィンドウを開いたままにプッシュピンをクリックします。 既にでない場合、ツールボックスを開きます。

5.  キーを押して**Ctrl**+**F5**をビルドして、サービスを起動します。 以前と同様に、ASP.NET 開発サーバーが起動され、Internet Explorer に WCF ヘルプ ページが表示されます。 このページの URI は、次の手順で使用する必要があるため、確認しておいてください。

     ![WCF ヘルプ ページと URI を表示する、つまり](../../../../docs/framework/wcf/feature-details/media/iewcfhelppagewuri.JPG "IEWCFHelpPageWURI")

6.  右クリックして、 **MyWFClient**プロジェクト、**ソリューション エクスプ ローラー**選択と**追加** > **サービス参照の**します。 をクリックして、 **Discover**サービスの現在のソリューションを検索するボタンをクリックします。 [サービス] ボックスで、Service1.xamlx の横にある三角形をクリックします。 Service1 の横にある三角形をクリックして、Service1 サービスによって実装されるコントラクトの一覧を表示します。 展開、 **Service1**内のノード、**サービス**一覧。 Echo 操作が表示されます、**操作**次の図に示すように一覧表示します。

     ![サービス参照 ダイアログ ボックスを追加](../../../../docs/framework/wcf/feature-details/media/addservicereference.JPG "AddServiceReference")

     既定の名前空間を保持し、をクリックして**OK**を閉じる、**サービス参照の追加**ダイアログ。 次のダイアログ ボックスが表示されます。

     ![サービス参照の追加の通知ダイアログ](../../../../docs/framework/wcf/feature-details/media/asrdlg.JPG "ASRDlg")

     クリックして**OK**ダイアログ ボックスを閉じます。 次に、Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。 新しいセクションが追加されたツールボックスの通知と呼ばれる**MyWFClient.ServiceReference1.Activities**します。 この選択肢を展開して、次の図のように、追加されている Echo アクティビティを確認します。

     ![ツールボックスにアクティビティをエコー](../../../../docs/framework/wcf/feature-details/media/echoactivity.JPG "EchoActivity")

7.  ドラッグ アンド ドロップ、 <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence`アクティビティをデザイナー画面にします。 下、**制御フロー**ツールボックスのセクション。

8.  <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence`フォーカスにアクティビティをクリックして、**変数**リンクし、という名前の文字列変数を追加`inString`します。 変数の既定値を付けます`"Hello, world"`という名前の文字列変数と`outString`次の図に示すようにします。

     ![変数の追加](../../../../docs/framework/wcf/feature-details/media/instringvar.JPG "inStringVar")

9. ドラッグ アンド ドロップ、**エコー**にアクティビティ、 <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence`します。 バインドのプロパティ ウィンドウで、`inMsg`への引数、`inString`変数と`outMsg`への引数、`outString`変数を次の図に示すように。 これにより、`inString` 変数の値を操作に渡し、戻り値を取得し、その戻り値を `outString` 変数に格納します。

     ![変数への引数のバインド](../../../../docs/framework/wcf/feature-details/media/argumentbind.JPG "ArgumentBind")

10. ドラッグ アンド ドロップ、 **WriteLine**アクティビティの下、**エコー**サービスの呼び出しによって返される文字列を表示するアクティビティ。 **WriteLine**にアクティビティがある、**プリミティブ**ツールボックス内のノード。 バインド、**テキスト**の引数、 **WriteLine**アクティビティを`outString`」と入力して変数`outString`テキスト ボックスに、 **WriteLine**アクティビティ。 この時点で、ワークフローは次の図のようになります。

     ![完全なクライアント ワークフロー](../../../../docs/framework/wcf/feature-details/media/completeclientwf.JPG "CompleteClientWF")

11. MyWFService ソリューションを右クリックして**スタートアップ プロジェクトの設定.**.選択、**マルチ スタートアップ プロジェクト**ボタンを選択します**開始**内の各プロジェクト、**アクション**列の次の図に示すようにします。

     ![スタートアップ プロジェクトのオプション](../../../../docs/framework/wcf/feature-details/media/startupprojects.JPG "StartupProjects")

12. Ctrl キーを押しながら F5 キーを押し、サービスとクライアントの両方を起動します。 ASP.NET 開発サーバー、サービスをホストする、Internet Explorer に WCF ヘルプ ページが表示されます、および、クライアント ワークフロー アプリケーションがコンソール ウィンドウで起動され、(「こんにちは, world」) のサービスから返される文字列が表示されます。

## <a name="see-also"></a>関連項目

- [ワークフロー サービス](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [方法 : メッセージング アクティビティを使用してワークフロー サービスを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)
- [Web プロジェクトでのワークフローから WCF サービスの使用](https://go.microsoft.com/fwlink/?LinkId=207725)