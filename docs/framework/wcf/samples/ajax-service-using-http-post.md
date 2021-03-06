---
title: HTTP POST を使用する AJAX サービス
ms.date: 03/30/2017
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
ms.openlocfilehash: c102d9d403cefb1bf3d4ab75859a81172895c2e0
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/01/2018
ms.locfileid: "43394916"
---
# <a name="ajax-service-using-http-post"></a>HTTP POST を使用する AJAX サービス
このサンプルでは Windows Communication Foundation (WCF) を使用して作成する方法、 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Asynchronous JavaScript and XML (AJAX) サービス HTTP POST を使用します。 AJAX サービスには、Web ブラウザー クライアントから基本的な JavaScript コードを使用してアクセスできます。 このサンプルでビルド、[基本的な AJAX サービス](../../../../docs/framework/wcf/samples/basic-ajax-service.md)サンプル; 2 つのサンプルの唯一の違いは、HTTP GET の代わりに HTTP POST を使用します。  
  
 Windows Communication Foundation (WCF) での AJAX のサポートがを介して ASP.NET AJAX と共に使用するために最適化された、`ScriptManager`コントロール。 WCF を使用して ASP.NET AJAX での例は、次を参照してください。、 [Ajax のサンプル](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)します。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 次のサンプルのサービスには、AJAX 固有のコードなしで WCF サービスです。  
  
 場合、<xref:System.ServiceModel.Web.WebInvokeAttribute>操作の属性を適用または<xref:System.ServiceModel.Web.WebGetAttribute>属性が適用されない、既定の HTTP 動詞 ("POST") が使用されます。 POST 要求は、GET 要求よりも作成が困難ですが、キャッシュされません。キャッシュが不適切な操作に対しては、POST 要求を使用します。  

```csharp
[ServiceContract(Namespace = "PostAjaxService")]  
public interface ICalculator  
{
    [WebInvoke]  
    double Add(double n1, double n2);  
    //Other operations omitted…  
}
```

 基本的な AJAX サービスのサンプルの場合と同様に、<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> を使用してサービスに AJAX エンドポイントを作成します。  
  
 GET 要求とは異なり、POST サービスはブラウザーから呼び出すことができません。 移動など、 http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200 POST サービスで想定されるので、エラーになります、`n1`と`n2`メッセージの本文で送信されるパラメーター-JSON 形式で — URL ではなく、します。  
  
 クライアントの Web ページの PostAjaxClientPage.aspx には、ユーザーがページ上のいずれかの操作ボタンをクリックするとサービスを呼び出す ASP.NET コードが含まれています。 サービスの応答と同じ方法で、[基本的な AJAX サービス](../../../../docs/framework/wcf/samples/basic-ajax-service.md)GET 要求では、サンプル。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  セットアップ手順を実行することを確認します。 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)します。  
  
2.  」の説明に従って、ソリューション PostAjaxService.sln をビルド[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)します。  
  
3.  移動 http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx (開かないで PostAjaxClientPage.aspx プロジェクト ディレクトリからブラウザーで)。  
  
## <a name="see-also"></a>関連項目
