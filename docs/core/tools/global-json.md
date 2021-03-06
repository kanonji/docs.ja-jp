---
title: global.json の概要
description: .NET Core CLI コマンドを実行するときに global.json ファイルを使用して .NET Core SDK のバージョンを設定する方法について説明します。
author: mairaw
ms.author: mairaw
ms.date: 07/02/2018
ms.custom: updateeachrelease
ms.openlocfilehash: a7c9301e1beea49eebace5c8f8a7d159a8c12466
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2018
ms.locfileid: "37936972"
---
# <a name="globaljson-overview"></a>global.json の概要

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

*global.json* ファイルを使うと、.NET Core CLI コマンドを実行するときに使う .NET Core SDK のバージョンを定義できます。 .NET Core SDK の選択は、プロジェクトのターゲットであるランタイムの指定とは関係ありません。 .NET Core SDK のバージョンは、使われている .NET Core CLI ツールのバージョンを示します。 通常は、最新バージョンのツールを使うので、*global.json* ファイルは必要ありません。

代わりにランタイムを指定する方法について詳しくは、「[ターゲット フレームワーク](../../standard/frameworks.md)」をご覧ください。

.NET Core SDK は、現在の作業ディレクトリ (プロジェクト ディレクトリと同じではない場合があります) 内、またはその親ディレクトリのいずれかで、*global.json* ファイルを探します。

## <a name="globaljson-schema"></a>global.json のスキーマ

### <a name="sdk"></a>SDK

型: Object

選択する .NET Core SDK についての情報を指定します。

#### <a name="version"></a>version

型: String

使用する .NET Core SDK のバージョンです。

このフィールドについては次のことに注意してください。

- グロビングはサポートされていません。つまり、完全なバージョン番号を指定する必要があります。
- バージョン範囲はサポートされていません。

*global.json* ファイルの内容の例を次に示します。

```json
{
  "sdk": {
    "version": "2.1.300"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a>global.json と .NET Core CLI

*global.json* ファイルでバージョンを設定するには、使用可能なバージョンがわかっていると便利です。 サポートされている使用可能な SDK の完全な一覧は、[.NET のダウンロード](https://www.microsoft.com/net/download/all) サイトで確認できます。 .NET Core SDK 2.1 以降では、次のコマンドを実行して、お使いのコンピューターに既にインストールされている SDK のバージョンを確認できます。

```console
dotnet --list-sdks
```

.NET Core SDK の別のバージョンをコンピューターにインストールするには、[.NET のダウンロード](https://www.microsoft.com/net/download/all) サイトにアクセスしてください。

次の例のような [dotnet new](dotnet-new.md) コマンドを実行することにより、新しい *global.json* ファイルを現在のディレクトリに作成できます。

```console
dotnet new globaljson --sdk-version 2.1.300
```

## <a name="matching-rules"></a>照合ルール

> [!NOTE]
> 照合ルールは、.NET Core ランタイムの一部である apphost によって制御されます。
> 複数のランタイムがサイドバイサイドでインストールされている場合は、最新バージョンのホストが使用されます。

.NET Core 2.0 以降では、使用する SDK のバージョンを決定するときに次のルールが適用されます。

- *global.json* ファイルが見つからない場合、または *global.json* で SDK のバージョンが指定されていない場合は、インストールされている最新バージョンの SDK が使用されます。 SDK の最新バージョンはリリースまたはプレリリースのどちらでもよく、最も高いバージョン番号が採用されます。
- *global.json* で SDK のバージョンが指定されている場合:
  - 指定されている SDK のバージョンがコンピューターで見つかった場合は、その厳密なバージョンが使用されます。
  - 指定されている SDK のバージョンがコンピューターで見つからない場合は、そのバージョンの SDK の**パッチ バージョン**でインストールされている最新のものが使用されます。 インストールされている最新の SDK **パッチ バージョン**は、リリースまたはプレリリースのどちらでもよく、最も高いバージョン番号が採用されます。 .NET Core 2.1 以降では、指定されている**パッチ バージョン**より低い**パッチ バージョン**は、SDK の選択で無視されます。
  - 指定されたバージョンの SDK および適切な SDK **パッチ バージョン**が見つからない場合は、エラーがスローされます。

現在、SDK のバージョンは次の部分で構成されます。

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

SDK バージョン 2.1.100 以降の番号の最後の部分 (`xyz`) の最初の桁 (`x`) は、.NET Core SDK の**機能リリース**を表します。 一般に、リリース サイクルは .NET Core より .NET Core SDK の方が速くなります。

**パッチ バージョン**は、SDK バージョン 2.1.100 以降の番号の最後の部分 (`xyz`) の最後の 2 桁 (`yz`) で定義されます。 たとえば、SDK のバージョンとして `2.1.300` を指定した場合、SDK の選択では `2.1.399` まで検索されますが、`2.1.400` は `2.1.300` のパッチ バージョンとして考慮されません。

.NET Core SDK のバージョン `2.1.100` から `2.1.201` までは、バージョン番号体系の移行の間にリリースされたため、`xyz` の表記を正しく処理していません。 *global.json* ファイルでこれらのバージョンを指定する場合は、指定するバージョンがターゲット コンピューター上にあることを確認するよう強くお勧めします。

.NET Core SDK 1.x では、バージョンを指定して、完全に一致するものが見つからない場合は、インストールされている最新バージョンの SDK が使われました。 SDK の最新バージョンはリリースまたはプレリリースのどちらでもよく、最も高いバージョン番号が採用されます。

## <a name="troubleshooting-build-warnings"></a>ビルドの警告のトラブルシューティング

> [!WARNING]
> You are working with a preview version of the .NET Core SDK. You can define the SDK version via a global.json file in the current project. More at https://go.microsoft.com/fwlink/?linkid=869452 (.NET Core SDK のプレビュー バージョンを使用しています。現在のプロジェクトの global.json ファイルを使用して、SDK のバージョンを定義できます。詳しくは https://go.microsoft.com/fwlink/?linkid=869452 をご覧ください)

この警告は、プレビュー バージョンの .NET Core SDK を使用してプロジェクトがコンパイルされていることを示します (「[照合ルール](#matching-rules)」セクションを参照)。 .NET Core SDK のバージョンには高品質の履歴とコミットメントがあります。 ただし、プレビュー バージョンを使用したくない場合は、*global.json* ファイルをプロジェクトの階層構造に追加して使用する SDK のバージョンを指定し、`dotnet --list-sdks` を使用してそのバージョンがコンピューターにインストールされていることを確認します。 新しいバージョンがリリースされたときに新しいバージョンを使用するには、*global.json* ファイルを削除するか、または新しいバージョンを使用するようにファイルを更新します。

> [!WARNING]
> Startup project '{startupProject}' targets framework '.NETCoreApp' version '{targetFrameworkVersion}'. This version of the Entity Framework Core .NET Command-line Tools only supports version 2.0 or higher. For information on using older versions of the tools, see https://go.microsoft.com/fwlink/?linkid=871254 (スタートアップ プロジェクト '{startupProject}' で、フレームワーク '.NETCoreApp' バージョン '{targetFrameworkVersion}' がターゲットになっています。このバージョンの Entity Framework Core .NET コマンド ライン ツールは、バージョン 2.0 以降のみをサポートします。古いバージョンのツールの使用については、https://go.microsoft.com/fwlink/?linkid=871254 をご覧ください)

.NET Core SDK 2.1 (v. 2.1.300) 以降では、`dotnet ef` コマンドが SDK に含まれます。 この警告は、プロジェクトのターゲットが EF Core 1.0 または 1.1 であり、.NET Core SDK 2.1 以降のバージョンと互換性がないことを示します。 プロジェクトをコンパイルするには、.NET Core SDK 2.0 (v. 2.1.201) 以前のバージョンをコンピューターにインストールしてください。 詳細については、「[EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet)」(EF Core .NET コマンドライン ツール) を参照してください。

## <a name="see-also"></a>関連項目

[プロジェクト SDK の解決方法](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)