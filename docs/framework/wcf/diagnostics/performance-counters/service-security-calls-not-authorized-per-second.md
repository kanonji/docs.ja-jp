---
title: 'サービス : 1 秒あたりの承認されていないセキュリティ呼び出し'
ms.date: 03/30/2017
ms.assetid: 1eeade5a-ea62-4757-b1f9-1b1b1746abd1
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: f2c921991f059d7dfe5661dfe688ec9675d0d5fe
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/01/2018
ms.locfileid: "43399414"
---
# <a name="service-security-calls-not-authorized-per-second"></a>サービス : 1 秒あたりの承認されていないセキュリティ呼び出し
カウンター名 : 1 秒あたりの承認されていないセキュリティ呼び出し  
  
## <a name="description"></a>説明  
 有効なユーザーから適切な保護を適用して送信されたが、特定のタスクの実行がユーザーに許可されていない受信メッセージの 1 秒あたりの数です。  
  
 このカウンターは <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> メソッドで `false` が返された場合にインクリメントされます。  
  
 このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkId=94649)、次の数式を使用して、その値が計算されます。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
