---
lab:
  title: Azure Storage を調べる
  module: Explore Azure Storage for non-relational data
---

# Azure Storage を調べる

この演習では、Azure Storage アカウントをプロビジョニングし、それを使用してデータを格納するさまざまな方法を検討します。

※Skillable上の"DP-900T00-A Microsoft Azure Data Fundamentals [Cloud Slice Provided] JAPANESE, Learning Path 03 (CSS)"ラボで実施

このラボは完了するまで、約 **20** 分かかります。

## Azure Storage アカウントをプロビジョニングする

Azure Storage を使用する際の最初の手順は、Azure サブスクリプションに Azure Storage アカウントをプロビジョニングすることです。

1. まだサインインしていない場合は、[Azure portal](https://portal.azure.com?azure-portal=true) にサインインします。
1. Azure portalで**"ストレージ アカウント"**を検索します。  **[ストレージ アカウント]** ページで、**[作成]** を選択します。
1. **[ストレージ アカウントの作成]** ページで、次の値を入力します。
    - **サブスクリプション**: 既定のサブスクリプションを使用（選択済み）
    - **リソース グループ**: **ResourceGroup1**（作成済み）
    - **ストレージ アカウント名**: **小文字と数字を使用して、グローバルに一意な名前を設定**
    - **リージョン**: **(US) East US**
    - **パフォーマンス**: **Standard**
    - **冗長性**: **"ローカル冗長ストレージ (LRS)"**

1. **[次へ: 詳細設定]** を選択し、詳細な構成オプションを表示します。デフォルトの設定を維持して、 **[次へ: ネットワーク]** を選択して、ストレージ アカウントのネットワーク オプションを表示します。こちらもデフォルトのまま次へ進めます。
1. **[次へ: データ保護]** を選択し、次に **[回復]** セクションで **[論理的な削除を有効にする]** オプションを**選択解除（チェックを外す）**します。 これらのオプションでは、後の回復のために削除されたファイルが保持されますが、後で階層型名前空間を有効にするときに問題が発生する可能性があります。
1.  **[レビュー]** をクリックし、確認ページで選択内容が検証されるのを待ち、 **[作成]** を選択して Azure Storage アカウントを作成します。
1. デプロイが完了するまで待ちます。 次に、デプロイされたリソースに移動します。

## BLOB ストレージを探索する

新しい Azure Storage アカウントを作成したので、BLOB データ用のコンテナーを作成できます。

1. [このリンク(product1.json)](https://aka.ms/product1.json?azure-portal=true)を**右クリック**して**名前をつけて保存**し、 JSONファイルをダウンロードします (後の手順で使用します)。

    *JSON ファイルがブラウザーに表示される場合は、ページを **product1.json** として保存します。*

1. ストレージ アカウントのページの左側にある **[データ ストレージ]** セクションで、**[コンテナー]** を選択します。
1. **[コンテナー]** ページで **[&#65291; コンテナー]** を選択し、匿名 アクセス レベルが **[プライベート (匿名アクセスはありません)]** の **data** という名前の新しいコンテナーを作成します。
1. **data** コンテナーが作成された後、それが **[コンテナー]** ページに一覧表示されているのを確認します。
1. 左側のペインの上部のセクションで、 **[ストレージ ブラウザー]** を選択します。 このページには、ストレージ アカウント内のデータを処理するために使用できるブラウザーベースのインターフェイスが表示されます。
1. [ストレージ ブラウザー] ページで **[BLOB コンテナー]** を選択し、**data** コンテナーが一覧表示されていることを確認します。
1. **data** コンテナーを選択し、中身が空であることを確認してください。
1. **[&#65291; ディレクトリの追加]** を選択し、**products** という名前の新しいディレクトリを作成します。
1. ストレージ ブラウザーで、作成した **products** フォルダーの内容が現在のビューに表示されていることを確認します。ページの上部にある "階層リンク" に **BLOB コンテナー > data > products** のパスが反映されているのを確認します。
1. 階層リンクで、**data** を選択して **data** コンテナーに切り替えます。**products** という名前のフォルダーは含まれてないので注意してください。

    BLOB ストレージ内のフォルダーは仮想であり、BLOB のパスの一部としてのみ存在します。 **products** フォルダーには BLOB が含まれていなかったので、実際に存在しません。

1. **[&#10514; アップロード]** ボタンを使用して、 **[BLOB のアップロード]** パネルを開きます。
1. **[BLOB のアップロード]** パネルで、以前にローカル コンピューターに保存した **product1.json** ファイルを選択します。 次に、**[詳細設定]** セクションを展開して、 **[アップロード先のフォルダー]** ボックスに **product_data** と入力し、**[アップロード]** ボタンを選択します。
1. **[BLOB アップロード]** パネルが開いている場合は閉じ、データ コンテナーに **product_data 仮想フォルダー** が作成されたことを確認します。
1. **product_data** フォルダーを選択し、アップロードした **product1.json** BLOB が含まれているか確認します。
1. 左側の **[データ ストレージ]** セクションで、**[コンテナー]** を選択します。
1. **data** コンテナーを開き、作成した **product_data** が一覧表示されていることを確認します。
1. フォルダーの右端の **[&#x2027;&#x2027;&#x2027;]** アイコンを選択します。オプションが表示されないことにご注意ください。 フラット型名前空間 BLOB コンテナー内のフォルダーは仮想であり、管理できません。
1. **data** ページの右上にある **X** アイコンを使用してページを閉じ、**[コンテナー]** ページに戻ります。

## Azure Data Lake Storage Gen2 を確認する

Azure Data Lake Store Gen2 のサポートを使用すると、階層フォルダーを使用して BLOB へのアクセスを整理および管理できます。 また、Azure BLOB ストレージを使用して、一般的なビッグ データ分析プラットフォーム用の分散ファイル システムをホストできます。

1.  [このリンク(product2.json)](https://aka.ms/product2.json?azure-portal=true)を**右クリック**して**名前をつけて保存**し、 JSONファイルをダウンロードします (以前のファイルとは別のもので、後の手順で使用します)。
1. ストレージ アカウントのページの左側にある **[設定]** セクションまで下にスクロールし、 **[Data Lake Gen2 のアップグレード]** を選択します。
1. **[Data Lake Gen2 のアップグレード]** ページで、階層型名前空間を有効にし、Azure Data Lake Storage Gen 2 をサポートするようにストレージ アカウントをアップグレードする各手順を展開して完了します。 これには時間がかかる場合があります。
1. アップグレードが完了したら、左側のペインの上部セクションで **[ストレージ ブラウザー]** を選択し、**data** BLOB コンテナーのルートに戻ります。これには引き続き **product_data** フォルダーが含まれます。
1. **product_data** フォルダーを選択し、前にアップロードした **product1.json** ファイルがまだ含まれているか確認します。
1. **[&#10514; アップロード]** ボタンを使用して、 **[BLOB のアップロード]** パネルを開きます。
1. **[BLOB のアップロード]** パネルで、ローカル コンピューターに保存した **product2.json** ファイルを選択します。 次に、**[アップロード]** ボタンを選択します。
1. **[BLOB のアップロード]** パネルが開いている場合は閉じ、**product_data** フォルダーに **product2.json** ファイルが含まれているのを確認します。
1. 左側の **[データ ストレージ]** セクションで、**[コンテナー]** を選択します。
1. **data** コンテナーを開き、作成した **product_data** が一覧表示されていることを確認します。
1. フォルダーの右側にある **[&#x2027;&#x2027;&#x2027;]** アイコンを選択し、階層型名前空間を有効にすると、フォルダー レベルで構成タスクを実行できることにご注意ください。これにはフォルダー名の変更やアクセス許可の設定を含みます。
1. **data** ページの右上にある **X** アイコンを使用してページを閉じ、**[コンテナー]** ページに戻ります。

## Azure Files について調べる

Azure Files は、クラウドベースのファイル共有を作成する方法を提供します。

1. ストレージ コンテナーの Azure portal ページの左側にある **[データ ストレージ]** セクションで、**[ファイル共有]** を選択します。
1. [ファイル共有] ページで **[&#65291; ファイル共有]** を選択し、**files** という名前の新しいファイル共有を追加します。レベルは**[トランザクションが最適化されました]**を使用します。 
1. **[次へ: バックアップ]**を選択し、**[バックアップの有効化]**を**無効化（チェックを外す）**します。通常のシチュエーションでは有効化することをおすすめしますが、本ラボのポリシー上オフに設定します。
1. **[確認および作成]**を選択し、検証が完了したら**[作成]**をクリックします。
1. **[ファイル共有]** で、新しい **files** ファイル共有を開きます。
1. ページの上部で、**[接続]** を選択します。 次に、**[接続]** ペインに、クライアント コンピューターから共有フォルダーに接続するために実行できるスクリプトを含む一般的なオペレーティング システム (Windows、Linux、macOS) のタブがあることを確認してください。
1. **[接続]** ペインを閉じ、次に **files** ファイル ページを閉じて、Azure ストレージ アカウントの **[ファイル共有]** ページに戻ります。

## Azure Tables を確認する

Azure テーブルは、データ値の格納を必要としても、リレーショナル データベースの完全な機能と構造を必要としないアプリケーションに、キーと値ストアを提供します。

1. ストレージ コンテナーのページの左側にある **[データ ストレージ]** セクションで、**[テーブル]** を選択します。
1. **[テーブル]** ページで、 **[&#65291; テーブル]** を選択し、**products** という名前の新しいテーブルを作成します。
1. **products** テーブルが作成されたら、左側のペインの上部にある **[ストレージ ブラウザー]** を選択します。
1. ストレージ エクスプローラーで、**[テーブル]** を選択し、**products** テーブルが表示されていることを確認します。
1. **products** テーブルを選択します。
1. **product** ページで、 **[&#65291; エンティティの追加]** を選択します。
1. **[エンティティの追加]** パネルで、次のキー値を入力します。
    - **PartitionKey**: 1
    - **RowKey**: 1
1. **[プロパティの追加]** を選択し、次の値を使用して新しいプロパティを作成します。

    |プロパティ名 | Type | 値 |
    | ------------ | ---- | ----- |
    | Name | String | ウィジェット |

1. 次の値を持つ 2 番目のプロパティを追加します。

    |プロパティ名 | Type | 値 |
    | ------------ | ---- | ----- |
    | Price | Double | 2.99 |

1. **[挿入]** を選択して、新しいエンティティの行をテーブルに挿入します。
1. ストレージ ブラウザーで、**products** テーブルに行が追加されていること、および行が最後に変更された日時を示す **Timestamp** 列が作成されていることを確認します。
1. 次のプロパティを使用して、**products** テーブルに別のエンティティを追加します。

    |プロパティ名 | Type | 値 |
    | ------------ | ---- | ----- |
    | PartitionKey | String | 1 |
    | RowKey | String | 2 |
    | Name | String | Knickknack |
    | Price | Double | 1.99 |
    | Discontinued | Boolean | true |

1. 新しいエンティティを挿入した後、生産が中止された(Discontinued)製品を含む行がテーブルに表示されていることを確認します。

    ストレージ ブラウザーのインターフェイスを使用して、テーブルにデータを手動で入力しました。 実際のシナリオでは、アプリケーション開発者は Azure Storage Table API を使用して、テーブルに対して値の読み取りと書き込みを行うアプリケーションを作成できます。これにより、NoSQL ストレージのコスト効率と拡張性に優れたソリューションになります。
