---
title: 公式の .NET Docker イメージ
description: コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | 公式の .NET Docker イメージ
ms.date: 01/13/2021
ms.openlocfilehash: 072e565260bf81c123ee837ccca46fbdf7c67361
ms.sourcegitcommit: 78eb25647b0c750cd80354ebd6ce83a60668e22c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2021
ms.locfileid: "99065123"
---
# <a name="official-net-docker-images"></a>公式の .NET Docker イメージ

公式の .NET Docker イメージは Microsoft により作成および最適化された Docker イメージです。 [Docker Hub](https://hub.docker.com/u/microsoft/) の Microsoft リポジトリで一般公開されています。 各リポジトリには、.NET のバージョンに応じて、また OS (Linux Debian、Alpine Linux、Windows Nano Server、Windows Server Core など) とそのバージョンに応じて、複数のイメージを含めることができます。

.NET Core 2.1 以降は、ASP.NET Core 用を含む .NET Core 以降のすべてのイメージが Docker Hub の .NET イメージ リポジトリ <https://hub.docker.com/_/microsoft-dotnet/> で提供されています。

2018 年 5 月以降、Microsoft のイメージは [Microsoft コンテナー レジストリにシンジケート化](https://azure.microsoft.com/blog/microsoft-syndicates-container-catalog/)されています。 公式カタログは引き続き Docker Hub でのみ利用でき、イメージをプルするための更新されたアドレスをそこで確認できます。

ほとんどのイメージ リポジトリではさまざまなタグを利用できるため、特定のフレームワーク バージョンだけでなく、OS (Linux ディストリビューションまたは Windows のバージョン) も選択できます。

## <a name="net-and-docker-image-optimizations-for-development-versus-production"></a>開発と運用における .NET および Docker イメージの最適化

Microsoft では開発者向けの Docker イメージをビルドするにあたり、次の主な 2 つのシナリオに重点を置きました。

- .NET アプリの "*開発*" およびビルドに使用されるイメージ。

- .NET アプリの "*実行*" に使用されるコマンド。

なぜ複数のイメージですか。 コンテナー化されたアプリケーションを開発、ビルド、実行する場合、通常は優先順位がそれぞれ異なります。 このような個々のタスク向けにさまざまなイメージを提供することによって、Microsoft は、アプリを開発、ビルド、および展開する個々のプロセスの最適化を支援しています。

### <a name="during-development-and-build"></a>開発中およびビルド中

開発中に重要な点は、変更を繰り返し処理する速さと、変更をデバッグする機能です。 コードを変更し、それをすばやく確認する機能に比べて、イメージのサイズはそれほど重要ではありません。 ツールおよび "ビルドエージェント コンテナー" の中には、開発およびビルド プロセス時に .NET の開発イメージ (*mcr.microsoft.com/dotnet/sdk:5.0*) を使用するものがあります。 Docker コンテナー内でビルドを行う場合は、アプリをコンパイルするために必要な要素が重要となります。 これには、コンパイラとその他の .NET 依存関係が含まれます。

この種のビルド イメージが重要な理由は何でしょうか。 このイメージが実稼働環境にデプロイされることはありません。 それは、実稼働イメージに配置するコンテンツをビルドする場合に使用するイメージです。 このイメージは、継続的インテグレーション (CI) 環境、または Docker マルチステージ ビルド使用時のビルド環境で使用されます。

### <a name="in-production"></a>実稼働環境

実稼働環境で重要な点は、実稼働 .NET イメージに基づいてコンテナーの展開および運用開始をいかに速く行えるかということです。 したがって、*mcr.microsoft.com/dotnet/aspnet:5.0* に基づくランタイムのみのイメージは、ネットワーク経由で Docker レジストリから Docker ホストまで迅速に送信できるように小さくなっています。 コンテンツは実行できる状態であるため、コンテナーの開始から結果の処理までを最速で行うことができます。 Docker モデルでは、ビルド コンテナーを使用するときに dotnet build または dotnet publish を実行する場合のように C\# コードからコンパイルを行う必要はありません。

この最適化されたイメージでは、アプリケーションを実行するために必要なバイナリとその他のコンテンツのみが配置されます。 たとえば、`dotnet publish` で作成されたコンテンツには、コンパイルされた .NET バイナリ、イメージ、.js、および .css ファイルのみが含まれます。 時間の経過と共に、事前に Just-In-Time (JIT) にコンパイルされた (実行時に発生する IL からネイティブへのコンパイル) パッケージ を含むイメージが表示されます。

.NET および ASP.NET Core イメージには複数のバージョンがありますが、これらはすべてで、基本レイヤーなどの 1 つまたは複数のレイヤーが共有されます。 そのため、イメージの格納に必要なディスク領域は小さくて済みます。カスタム イメージとその基本イメージ間のデルタのみで構成されます。 結果として、レジストリからイメージを迅速にプルすることができます。

Docker Hub の .NET イメージ リポジトリを探索すると、タグで分類またはマークされた複数のイメージ バージョンを見つかります。 これらのタグは、次の示すように、必要とするバージョンに応じて使用するものを特定するのに役立ちます。

| Image | コメント |
|-------|----------|
| mcr.microsoft.com/dotnet/aspnet:**5.0** | ASP.NET Core、ランタイムのみ、ASP.NET Core の最適化、Linux および Windows (マルチアーキテクチャ) |
| mcr.microsoft.com/dotnet/sdk:**5.0** | .NET 5、SDK 含む、Linux および Windows (マルチアーキテクチャ) |

> [!div class="step-by-step"]
> [前へ](net-container-os-targets.md)
> [次へ](../architect-microservice-container-applications/index.md)
