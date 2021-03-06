---
title: 動的再構成
ms.date: 03/30/2017
ms.assetid: b20786ae-cce6-4f91-b6cb-9cae116faf8b
ms.openlocfilehash: a147a1d6cf61001832661376363ecc850ecad309
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401341"
---
# <a name="dynamic-reconfiguration"></a>動的再構成
このサンプルでは、Windows Communication Foundation (WCF) ルーティング サービスを使用します。 ルーティング サービスは、WCF コンポーネント、アプリケーションでコンテンツ ベースのルーターを含めるが簡単です。 このサンプルでは、ルーティング サービスを使用して通信するために標準の WCF 電卓のサンプルを適応します。 このサンプルでは、実行時にルーティング サービスを動的に再構成する方法を示します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\DynamicReconfiguration`  
  
## <a name="sample-details"></a>サンプルの詳細  
 このサンプルでは、実行時にルーティング サービスを動的に再構成するために、5 秒ごとにタイマーを作動させ、新しい <xref:System.ServiceModel.Routing.RoutingConfiguration> オブジェクトを作成して適用します。 この構成は、通常の電卓のエンドポイントまたは丸め処理を行う電卓のエンドポイントのいずれかを示しています。 電卓クライアント アプリケーションは、ルーティング サービスがその時点でどちらのサービスにルーティングするように構成されているかに応じて、いずれか一方のサービスからメッセージを受け取ります。  
  
 ルーティング サービスのカスタム動作を介した動的再構成機能が使用されます。 このカスタム動作は、5 秒ごとに作動する単純なスレッド タイマーを含むサービス拡張をアタッチします。このスレッド タイマーにより、`UpdateRules` メソッドへのコールバックが発生し、 新しいルーティング構成が作成および適用されます。 実際の配置では、このコールバックは、別の種類のイベント (SQL-Event 通知や WS-Discovery アナウンスなど) の結果として行われる可能性があります。  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を使用して DynamicReconfiguration.sln を開きます。  
  
2.  開くには**ソリューション エクスプ ローラー**、**ソリューション エクスプ ローラー**から、**ビュー**メニュー。  
  
3.  キーを押して**F5**または**CTRL + SHIFT + B** Visual Studio でします。  
  
    1.  自動的に起動に必要なプロジェクト キーを押すかかどうか**f5 キーを押して**ソリューションを右クリックし、選択、**プロパティ**します。 選択、**スタートアップ プロジェクト**ノードの下**共通プロパティ**左側のウィンドウでします。 選択、**マルチ スタートアップ プロジェクト**オプション ボタンをクリックし、すべてのプロジェクトに設定、**開始**アクション。  
  
    2.  プロジェクトをビルドする場合**CTRL + SHIFT + B**、次のアプリケーションを開始する必要があります。  
  
        1.  電卓クライアント (./CalculatorClient/bin/client.exe)  
  
        2.  電卓サービス (./CalculatorService/bin/service.exe)  
  
        3.  丸め処理を行う電卓サービス (./RoundingCalcService/bin/service.exe)  
  
        4.  ルーティング サービス (./RoutingService/bin/RoutingService.exe)  
  
4.  電卓クライアントのコンソール ウィンドウで、Enter キーを押してクライアントを開始し、電卓サービス操作を呼び出します。  
  
     ルーティング サービスは、丸め処理を行う電卓と通常の電卓に交互にメッセージをルーティングします。これはルーティング構成が 5 秒ごとに動的に変化するためです。 ルーティング サービスがどちらのエンドポイントにメッセージを送信するように構成されているかに応じて、異なる出力がクライアント コンソールに表示されます。  
  
5.  Enter キーを 5 秒以上にわたって繰り返し押して、サービスから返される結果が変化することを確認します。  
  
    1.  次に、ルーター サービスが丸め処理を行う電卓サービスにメッセージをルーティングするように構成されている場合に返される出力を示します。  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.2  
        Divide(22,7) = 3.1  
        ```  
  
    2.  次に、ルーティング サービスが通常の電卓サービスにメッセージをルーティングするように構成されている場合に返される出力を示します。  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
6.  また、電卓サービスと丸め処理を行う電卓サービスは、呼び出された操作のログをそれぞれのコンソール ウィンドウに出力します。  
  
7.  クライアント コンソール ウィンドウでは、"quit"を入力し、ENTER を押して終了します。  
  
8.  サービスを終了するには、サービス コンソール ウィンドウで Enter キーを押します。  
  
## <a name="scenario"></a>シナリオ  
 このサンプルでは、1 つのエンドポイントを介して複数の種類または実装のサービスを公開することを可能にするコンテンツ ベースのルーターとして機能するルーターを示します。  
  
### <a name="real-world-scenario"></a>実際のシナリオ  
 Contoso では、すべてのサービスを仮想化して 1 つのエンドポイントのみを公開し、そのエンドポイントを通じて複数の異なる種類のサービスへのアクセスを提供したいと考えています。 この場合は、ルーティング サービスのコンテンツ ベースのルーティング機能を使用して受信要求の送信先を決定します。  
  
## <a name="see-also"></a>関連項目  
 [AppFabric のホストおよび永続化のサンプル](https://go.microsoft.com/fwlink/?LinkId=193961)
