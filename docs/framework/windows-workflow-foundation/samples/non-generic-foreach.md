---
title: 非ジェネリックの ForEach
ms.date: 03/30/2017
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
ms.openlocfilehash: b94ad54d248af7f6ad45c11b9860dd415db840f9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/01/2018
ms.locfileid: "43419318"
---
# <a name="non-generic-foreach"></a>非ジェネリックの ForEach
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] などの制御フロー アクティビティのセットをツールボックスに付属<xref:System.Activities.Statements.ForEach%601>、反復処理に使用できる<!--zz <xref:System.Collections.IEnumerable%601> -->`System.Collections.IEnumerable`コレクション。  
  
 <xref:System.Activities.Statements.ForEach%601> 必要があります、<xref:System.Activities.Statements.ForEach%601.Values%2A>プロパティの型を<!--zz <xref:System.Collections.IEnumerable%601> -->`System.Collections.IEnumerable`します。 これは、ため、ユーザーを実装するデータ構造を反復<!--zz <xref:System.Collections.IEnumerable%601> -->`System.Collections.IEnumerable`インターフェイス (たとえば、 <xref:System.Collections.ArrayList>)。 <xref:System.Activities.Statements.ForEach%601> の非ジェネリック バージョンにはこの要件はありませんが、コレクション内の値の型の互換性を確保するために実行時の複雑さが増します。  
  
 このサンプルでは、非ジェネリックの <xref:System.Activities.Statements.ForEach%601> アクティビティとそのデザイナーを実装する方法を示します。 このアクティビティは、<xref:System.Collections.ArrayList> の反復処理に使用できます。  
  
## <a name="foreach-activity"></a>ForEach アクティビティ  
 C# および VB の `foreach` ステートメントは、コレクションの要素を列挙し、コレクションの各要素に対して埋め込みステートメントを実行します。 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] に相当する `foreach` のアクティビティは、<xref:System.Activities.Statements.ForEach%601> および <xref:System.Activities.Statements.ParallelForEach%601> です。 <xref:System.Activities.Statements.ForEach%601> アクティビティには、値のリストと本体が含まれます。 実行時に、リストが反復処理されて、リスト内の値ごとに本体が実行されます。  
  
 ほとんどの場合、ジェネリック バージョンのアクティビティを使用することをお勧めします。ジェネリック バージョンのアクティビティは、そのアクティビティを使用するシナリオの大半に対応し、コンパイル時の型チェックが実現するためです。 非ジェネリック バージョンは、非ジェネリックの <xref:System.Collections.IEnumerable> インターフェイスを実装する型を反復処理するために使用できます。  
  
## <a name="class-definition"></a>クラス定義  
 次のコード例は、非ジェネリックの `ForEach` アクティビティの定義を示しています。  
  
```  
[ContentProperty("Body")]  
public class ForEach : NativeActivity  
{  
    [RequiredArgument]  
    [DefaultValue(null)]  
    InArgument<IEnumerable> Values { get; set; }  
  
    [DefaultValue(null)]  
    [DependsOn("Values")]  
    ActivityAction<object> Body { get; set; }   
}  
```  
  
 Body (省略可能)  
 コレクション内の要素ごとに実行される <xref:System.Activities.ActivityAction> 型の <xref:System.Object>。 各要素は、`Argument` プロパティを使用して Body に渡されます。  
  
 Values (省略可能)  
 反復処理される要素のコレクション。 コレクションのすべての要素の型が互換性のある型であることが実行時に確認されます。  
  
## <a name="example-of-using-foreach"></a>ForEach の使用例  
 アプリケーションでの ForEach アクティビティの使用方法を次のコードに示します。  
  
```  
string[] names = { "bill", "steve", "ray" };  
  
DelegateInArgument<object> iterationVariable = new DelegateInArgument<object>() { Name = "iterationVariable" };  
  
Activity sampleUsage =  
    new ForEach  
    {  
       Values = new InArgument<IEnumerable>(c=> names),  
       Body = new ActivityAction<object>   
       {                          
           Argument = iterationVariable,  
           Handler = new WriteLine  
           {  
               Text = new InArgument<string>(env => string.Format("Hello {0}",                                                               iterationVariable.Get(env)))  
           }  
       }  
   };  
```  
  
|状態|メッセージ|重大度|例外の種類|  
|---------------|-------------|--------------|--------------------|  
|値が `null` である|必須のアクティビティ引数 'Values' の値が指定されませんでした。|Error|<xref:System.InvalidOperationException>|  
  
## <a name="foreach-designer"></a>ForEach デザイナー  
 サンプルのアクティビティ デザイナーは、組み込みの <xref:System.Activities.Statements.ForEach%601> アクティビティ用に提供されているデザイナーに外観が似ています。 ツールボックス、デザイナーが表示されます、**サンプル**、**非ジェネリック アクティビティ**カテゴリ。 デザイナーの名前は**ForEachWithBodyFactory**ツールボックスで、活動が公開するため、<xref:System.Activities.Presentation.IActivityTemplateFactory>で適切に構成されたアクティビティを作成するツールボックスで、<xref:System.Activities.ActivityAction>します。  
  
```  
public sealed class ForEachWithBodyFactory : IActivityTemplateFactory  
{  
    public Activity Create(DependencyObject target)  
    {  
        return new Microsoft.Samples.Activities.Statements.ForEach()  
        {  
            Body = new ActivityAction<object>()  
            {  
                Argument = new DelegateInArgument<object>()  
                {  
                    Name = "item"  
                }  
            }  
        };  
    }  
}  
```  
  
#### <a name="to-run-this-sample"></a>このサンプルを実行するには  
  
1.  選択したプロジェクトをソリューションのスタートアップ プロジェクトに設定します。  
  
    1.  **CodeTestClient**コードを使用して、アクティビティを使用する方法を示しています。  
  
    2.  **DesignerTestClient**デザイナー内でアクティビティを使用する方法を示しています。  
  
2.  プロジェクトをビルドして実行します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`
