---
title: "SqlTypes と DataSet | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# SqlTypes と DataSet
ADO.NET 2.0 では、<xref:System.Data.SqlTypes> 名前空間を介した `DataSet` の型のサポートが拡張されました。  <xref:System.Data.SqlTypes> の型は、SQL Server データベースのデータ型と同じセマンティクスと有効桁数を備えたデータ型を用意するように設計されています。  <xref:System.Data.SqlType> の個々のデータ型には、それに相当する SQL Server のデータ型があり、基本となるデータ表現はいずれも同じです。  
  
 <xref:System.Data.DataSet> で直接 <xref:System.Data.SqlTypes> を使用できると、SQL Server データ型を操作するときに便利です。  <xref:System.Data.SqlTypes> は、SQL Server ネイティブのデータ型と同じセマンティクスをサポートしています。  <xref:System.Data.DataColumn> の定義でいずれかの <xref:System.Data.SqlTypes> を指定することで、decimal データ型または numeric データ型をいずれかの共通言語ランタイム \(CLR\) データ型に変換するときの精度の低下を防止します。  
  
## 例  
 次の例では、<xref:System.Data.DataTable> オブジェクトを作成し、CLR データ型の代わりに <xref:System.Data.SqlTypes> を使用して、<xref:System.Data.DataColumn> のデータ型を明示的に定義します。  このコードは、SQL Server の AdventureWorks データベースの Sales.SalesOrderDetail テーブルから取得されたデータを <xref:System.Data.DataTable> に挿入します。  コンソール ウィンドウには、各列のデータ型および SQL Server から取得された値が表示されます。  
  
 [!code-csharp[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/VB/source.vb#1)]  
  
## 参照  
 [SQL Server データ型のマッピング](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)   
 [パラメーターおよびパラメーター データ型の構成](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)