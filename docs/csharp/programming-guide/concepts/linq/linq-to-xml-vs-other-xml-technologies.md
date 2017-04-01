---
title: "LINQ to XML およびその他の XML テクノロジ | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 01b8e746-12d3-471d-b811-7539e4547784
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8ac37ce1a225a66069e34abedd2ee0c273b8f8a9
ms.lasthandoff: 03/13/2017

---
# <a name="linq-to-xml-vs-other-xml-technologies"></a>LINQ to XML およびその他の XML テクノロジ
このトピックでは、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] を他の XML テクノロジ (<xref:System.Xml.XmlReader>、XSLT、MSXML、XmlLite) と比較します。 使用するテクノロジを決定するときに、ここで説明する情報を参照してください。  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] とドキュメント オブジェクト モデル (DOM) の比較については、「[LINQ to XML およびDOM (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-dom.md)」を参照してください。  
  
## <a name="linq-to-xml-vs-xmlreader"></a>LINQ to XML およびXmlReader  
 <xref:System.Xml.XmlReader> は、高速、前方参照専用、非キャッシュのパーサーです。  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] は <xref:System.Xml.XmlReader> の上位に実装され、緊密に統合されています。 ただし、<xref:System.Xml.XmlReader> を単独で使用することもできます。  
  
 たとえば、1 秒間に何百もの XML ドキュメントを解析する Web サービスを構築する際に、これらのドキュメントの構造が同じであるため、XML を解析するために実装するコードの作成が 1 つだけで済む場合は、 この場合、<xref:System.Xml.XmlReader> を単独で使用することが考えられます。  
  
 一方、多数の小さい XML ドキュメントを解析するシステムを構築する際に、ドキュメントがそれぞれ異なる場合は、生産性の向上という観点から [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] を使用します。  
  
## <a name="linq-to-xml-vs-xslt"></a>LINQ to XML およびXSLT  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] と XSLT は、どちらも広範な XML ドキュメント変換機能を備えています。 XSLT は、ルール ベースの宣言型の方法です。 高度な XSLT プログラミングでは、ステートレスな方法が重視される関数型のプログラミング スタイルで XSLT を記述します。 変換は、副作用なしで実装される純粋関数を使用して記述できます。 このルール ベース (関数型) の方法に精通している開発者は多くありません。また、修得するのは難しく、相当の学習時間を要する場合があります。  
  
 XSLT は、パフォーマンスの高いアプリケーションを生成する、生産性の高いシステムとして利用できます。 たとえば、Web 関連の大企業の中には、さまざまなデータ ソースを基に取得した XML から HTML を生成するための手段として XSLT を使用している企業もあります。 XSLT を CLR コードにコンパイルするマネージ XSLT エンジンは、一部のシナリオではネイティブ XSLT エンジンより高いパフォーマンスを発揮します。  
  
 ただし、XSLT では、多くの開発者が持っている C# や Visual Basic の知識は活かされません。 開発者は、別の複雑なプログラミング言語でコードを記述する必要があります。 C# (または Visual Basic) と XSLT など、統合されていない 2 つの開発システムを使用すると、ソフトウェア システムの開発や保守が困難になります。  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] の変換は、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] のクエリ式を修得すれば、使いやすいテクノロジとして威力を発揮します。 基本的には、関数型構築を使用して、さまざまなソースからデータを取り込んで <xref:System.Xml.Linq.XElement> オブジェクトを動的に構築し、全体をまとめて新しい XML ツリーを作成することによって XML ドキュメントを作成します。 変換では、まったく新しいドキュメントを生成できます。 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] を使用すると、変換を比較的簡単かつ直感的に構築でき、結果のコードも読みやすいものになります。 このため、開発と保守のコストを削減できます。  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] は、XSLT に置き換わることを目的としていません。 複雑なドキュメント中心の XML 変換 (特に、ドキュメントの構造が明確に定義されていない場合) では、引き続き XSLT が最適なツールになります。  
  
 XSLT には、W3C (World Wide Web Consortium) 標準という利点があります。 標準となっている技術を使用するだけで十分な場合は、XSLT の方が適切といえます。  
  
 XSLT は XML であるため、プログラムで操作できます。  
  
## <a name="linq-to-xml-vs-msxml"></a>LINQ to XML およびMSXML  
 MSXML は、Microsoft Windows に付属する、XML 処理のための COM ベース テクノロジです。 MSXML は DOM をネイティブで実装し、XPath と XSLT をサポートしています。 MSXML には、非キャッシュの SAX2 イベントベース パーサーも含まれています。  
  
 MSXML はパフォーマンスが高く、セキュリティもほとんどのシナリオで既定で確保されます。また、Internet Explorer でアクセスできるため、AJAX スタイルのアプリケーションでクライアント側での XML の処理を実行できます。 MSXML は、C++、JavaScript、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 6.0 など、COM をサポートするすべてのプログラミング言語から使用できます。  
  
 ただし共通言語ランタイム (CLR) に基づくマネージ コードで使用することは推奨されません。  
  
## <a name="linq-to-xml-vs-xmllite"></a>LINQ to XML およびXmlLite  
 XmlLite は、非キャッシュ、前方参照専用のプル パーサーで、 主に C++ で使用されます。 マネージ コードで使用することは推奨されません。  
  
 XmlLite の最大の利点は、ほとんどのシナリオで、軽量かつ高速で安全な XML パーサーとして利用できることです。 XmlLite は脅威の対象となる要素がほとんどないため、 信頼されていないドキュメントを解析し、サービス拒否攻撃やデータ漏洩攻撃などからの保護が必要な場合は、優れた方法となります。  
  
 XmlLite は、[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] と統合されていません。 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] の利用動機となるプログラミングの生産性の向上はもたらされません。  
  
## <a name="see-also"></a>関連項目  
 [はじめに (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/getting-started-linq-to-xml.md)