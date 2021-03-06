---
title: AppDomainInfo
ms.date: 03/30/2017
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
ms.openlocfilehash: 7189448a930298837089cf3ac2743cb7e073ae02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486982"
---
# <a name="appdomaininfo"></a>AppDomainInfo
アプリケーション ドメイン情報  
  
## <a name="syntax"></a>構文  
  
```  
class AppDomainInfo  
{  
  sint32 AppDomainId;  
  boolean IsDefault;  
  boolean LogMalformedMessages;  
  boolean LogMessagesAtServiceLevel;  
  boolean LogMessagesAtTransportLevel;  
  TraceListener MessageLoggingTraceListeners[];  
  string Name;  
  string PerformanceCounters;  
  sint32 ProcessId;  
  string ServiceConfigPath;  
  string TraceLevel;  
  TraceListener wmiTraceListeners[];  
};  
```  
  
## <a name="methods"></a>メソッド  
 AppDomainInfo クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  
 AppDomainInfo クラスには、次のプロパティがあります。  
  
### <a name="appdomainid"></a>AppDomainId  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 AppDomain の ID です。  
  
### <a name="isdefault"></a>IsDefault  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 AppDomain が既定の AppDomain かどうかを示します。  
  
### <a name="logmalformedmessages"></a>LogMalformedMessages  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り/書き込み  
  
 非整形式メッセージをログに記録するかどうかを指定する値です。  
  
### <a name="logmessagesatservicelevel"></a>LogMessagesAtServiceLevel  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り/書き込み  
  
 メッセージをサービス レベルでトレースするかどうかを指定する値です (暗号化およびトランスポート関連の変換前)。  
  
### <a name="logmessagesattransportlevel"></a>LogMessagesAtTransportLevel  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り/書き込み  
  
 メッセージをトランスポート レベルでトレースするかどうかを指定する値です。  
  
### <a name="messageloggingtracelisteners"></a>MessageLoggingTraceListeners  
 データ型 : TraceListener 配列  
  
 アクセスの種類 : 読み取り専用  
  
 System.Wmi.MessageLogging トレース ソースをリッスンするコレクション トレース リスナーです。  
  
### <a name="name"></a>名前  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 AppDomain の名前です。  
  
### <a name="performancecounters"></a>PerformanceCounters  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 AppDomain におけるアクティブなパフォーマンス カウンターのスコープです。  
  
### <a name="processid"></a>ProcessId  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 プロセス ID です。  
  
### <a name="serviceconfigpath"></a>ServiceConfigPath  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 サービスの構成へのパスです。  
  
### <a name="tracelevel"></a>TraceLevel  
 データ型: string  
  
 アクセスの種類 : 読み取り/書き込み  
  
 System.Wmi トレース ソースのトレース レベル。  
  
### <a name="servicemodeltracelisteners"></a>ServiceModelTraceListeners  
 データ型 : TraceListener 配列  
  
 アクセスの種類 : 読み取り専用  
  
 System.ServiceModel トレース ソースのリスナーのコレクション。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|Namespace|root\ServiceModel で定義|
