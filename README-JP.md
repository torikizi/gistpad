# GistPad 📘

## このドキュメントについて

これは GistPad の README を DeepL Pro と ChatGPT を使用して日本語化したものです。

全体の翻訳は DeepL Pro を使用し、一部の文章は ChatGPT と人力で整えています。

## 翻訳のベースとしたもの

master ブランチを fork して使用しています。

README.md はこのバージョンをベースとして日本語訳を行いました。

https://github.com/lostintangent/gistpad/commit/31709e3b297fcb476a135702d1d27e2ff9e40641

## GistPad とは
GistPadは、GitHubの[Gists](https://gist.github.com/)やリポジトリを、お気に入りのエディタで快適に編集できるVisual Studio Codeの拡張機能です。Gistやリポジトリを開いたり、作成したり、削除したり、フォークしたり、スターをつけたりすることができ、クローンやプッシュ、プルすることなく、**あたかもローカル**のようにシームレスにファイルの編集を開始することができます。コードスニペット、よく使う設定・スクリプト、プログラミング関連のメモ、[ナレッジベース](#wiki)、[インタラクティブサンプル](#codeswing)を構築して参照できる、あなただけの開発者ライブラリーのようなものです。

<img src="https://user-images.githubusercontent.com/116461/69910156-96274b80-13fe-11ea-9be4-d801f4e9c377.gif" width="750px" />

## 目次

- **[スタートアップ](#getting-started)**。
- **[Gist マネジメント](#gist-management)**。
  - [仕分け・グループ化](#仕分け・グループ化)
  - [ファイルとディレクトリ](#files-and-directories)
  - [Gist コメント](#gist-commenting)
  - [画像の貼り付け](#pasting-images)
  - [フォローユーザー](#following-users)
  - [リポジトリへの書き出し](#exporting-to-repositories)
  - [スクラッチノート](#scratch-notes)
  - [ショーケース](#showcase)
  - [Gist ログ](#gistlog)
- **[リポジトリ管理](#repositories)**。
  - [ブランチ](#branches)
  - [ウィキ](#wikis)
- [コードスイング](#codeswing)*2
- [コントリビュートコマンド](#contributed-commands-file-explorer)**。
- [設定](#configuration-settings)**．

## Getting Started

1. まず、マーケットプレイスからこの拡張機能をインストールし、その後 `Developer: Reload Window` を実行します。

2. `GistPad`タブを開きます（アクティビティバーのノートブックアイコンを探してください）。そこから、ID / URL で gist または GitHub リポジトリを開くか、GitHub アカウントでサインインして [gists](#gist-management) や [repositories](#repositories) を管理できます。サインインするには、「Sign In」ボタンをクリックし、提供されるフローに従ってGitHubアカウントで認証します。

[gist](#gist-management)、[repositories](#repositories)、[wiki](#wiki)、[runnable code samples](#codeswing) を作成・編集することができます。そして、あなたの知識管理体験をさらに素晴らしいものにするために、私たちがどのようにできるかを教えてください！🙌

## Gist マネジメント

新しい gist を作成するには、`GistPad` タブで `Gists` ツリーを開き、ツールバーの `+` アイコンをクリックするだけです。説明文とシードファイルを指定します（[ディレクトリ](#files-and-directories)もサポートしています！）。さらに、ローカルファイルやスニペットを `Explorer` ツリーで右クリックするか、エディタウィンドウ/タブを右クリックして `Copy File to Gist`, `Add Selection to Gist`, `Paste Gist File Contents` ([詳細](#contributed-commands-editor)) を選択すれば、Gistを作成できます。

<img width="250px" src="https://user-images.githubusercontent.com/116461/69903980-98819b00-1355-11ea-913b-c51981891bcd.png" />

> あるいは、`GistPad： New Gist` と `GistPad： New Secret Gist` コマンドを実行します。

ここから、gist を展開し、目的のファイルをクリックすることで、gist を編集することができます。また、ツリー上で右クリックし、目的のコマンドを選択することで、gist を開いたり、名前を変更したり、削除したりすることができます。

### ソートとグループ化

デフォルトでは、`Gists` ツリーは gist を更新時間順にソートしており、最近使用した gist に集中することができます。アルファベット順に並べたい場合は、`Gists` ツリーのツールバーにある `Sort toggle ボタン`をクリックしてください。

<img width="200px" src="https://user-images.githubusercontent.com/116461/75098896-65276480-5570-11ea-9880-a76347a15f73.png" />

デフォルトでは、Gists はフラットなリストとして表示されます。もし、種類ごとにグループ化したい場合は、`Gists` ツリーのツールバーにある `group toggle ボタン`をクリックしてください。

 <img width="200px" src="https://user-images.githubusercontent.com/116461/75098775-3fe62680-556f-11ea-8253-3198b00837e1.png" />

#### Gist タイプ

グループ化が有効な場合、gist は以下の組み込みタイプにグループ化されます：

- **note** - `.txt`、`.md` / `.markdown`、`.adoc` ファイルのみで構成される Gist。
- **notebook** - Jupyter Notebook ファイル(`.ipynb`)で構成される Gist です。
- **code-swing** - `codeswing.json` ファイルと `index.html` ファイルのどちらかを含む Gist です。スイングについて詳しくは[こちら](#codeswing)を参照してください。
- **code-swing-template** - `codeswing.json` ファイルに `template` プロパティが `true` に設定されているスイング。スイングテンプレートについて詳しくは[こちら](#user-templates)を参照してください。
- **code-swing-tutorial** - `codeswing.json` ファイルに `tutorial` プロパティが指定されているスイングです。チュートリアルについて詳しくは [こちら](#tutorials)を参照してください。
- **code-tour** - `main.tour` ファイルを含み、 [CodeTour](#codetour) をエクスポートして作成された Gist です。
- **diagram** - `.drawio` ファイルを含む Gist です。
- **flash-code** - `.deck` ファイルを含む Gist です。
- **code-snippet** - 上記のどのタイプにも当てはまらない Gist です。

独自のタイプで gist をグループ化したい場合は、gist の説明文の最後に `#tag` または `#tag-name` という形式でタグを追加してください。グループ化を有効にすると、gist は前述のタイプだけでなく、カスタムタグでもグループ化されます。タグのグループは `#` アイコンで識別できます。

<img width="200px" src="https://user-images.githubusercontent.com/116461/75264671-9c7e5700-57a4-11ea-9bee-eb61cfb9d2f0.png" />

### ファイルとディレクトリ

`New Gist` または `New Secret Gist` コマンドで gist を作成する際に、カンマ区切りのファイル名のリストを指定して、Gistを初期化することができます。さらに、ファイル名に `/` を追加することで、gist 内のサブディレクトリにファイルを追加することもできます

例えば、新しい gist を作成し、`reminders.txt,todos/personal.txt,todos/work.txt` と指定すると、gist のルートに `reminders.txt` ファイル、`todos` というディレクトリに `personal.txt` と `reminders.txt` というファイルが入っています。

<img width="200px" src="https://user-images.githubusercontent.com/116461/74593846-7b6b7880-4fe4-11ea-9bf8-722bf7887ef1.png" />

ファイルを右クリックして `Add New File(s)` または `Upload File(s)` を選択すれば、いつでもエクスプローラから新しいファイルを gist やディレクトリに追加することができます。ディレクトリも同様に、ツリー上で右クリックして適切なコマンドを選択することで、名前を変更したり削除したりすることができます。ファイルをあるディレクトリから別のディレクトリに移動したい場合は、ファイルを右クリックして `Rename File` を選択し、そのファイルがあるディレクトリ名を編集するだけです。とても簡単です！

### Gistのコメント

Gist のコメントは、エディタ内で、開いている Gist ファイルの下部に表示されます。gist が複数のファイルを含んでいる場合、コメントスレッドはそれらすべてのファイルの下部に表示されます（複製され、同期されます）。

<img src="https://user-images.githubusercontent.com/116461/70118599-42467d80-161d-11ea-85eb-7f4cc6e4006b.gif" width="700px" />

認証されていない場合、既存のコメントを閲覧することはできますが、返信することはできません。認証されている場合は、コメントの追加・返信、自分のコメントの編集・削除が可能です。gist のコメントスレッドの表示方法を制御するには、`GistPad > Comments： Show Thread` の設定を参照してください。

### 画像の貼り付け

画像アセットを含む Markdown や HTML/Pug ファイルを簡単にオーサリングできるように、画像をクリップボードにコピーし（例：スクリーンショットを撮る、ブラウザで `Copy Image` をクリックするなど）、エディタを右クリックして `Paste Image` を選択、または `ctrl + shift + v` _(Windows/Linux)_, `cmd + shift + v` _(macOS)_ で gist ファイルに直接ペーストできるようにしました。

![paste-image](https://user-images.githubusercontent.com/1478800/70382701-9a7ac980-1914-11ea-9fb0-6e55424e2e54.gif)

デフォルトでは、画像を gist ファイルに貼り付けると、その画像は `.png` として gist にアップロードされ、ドキュメントから適切な参照が追加されます（例：`<img />` を挿入する）。しかし、この動作は `GistPad > Images.Pasteフォーマット` や `GistPad > Images.Pasteフォーマット` を使用することで変更することができます： 貼り付け形式`や`GistPad > Images: Paste Format`、`GistPad > Images： 貼り付けの種類`を設定することで変更できます。詳しくは、以下の[設定](#configuration-settings)の項を参照してください。

デフォルトでは、画像を貼り付けると、gist内の`images`というディレクトリにアップロードされます。しかし、これを変更したい場合(例えば、代わりに `assets` にアップロードしたい場合)、`GistPad > Images： ディレクトリ名`を設定します。

### ユーザーのフォロー

GitHub Gists では他のユーザーの gist にスターをつけることができ、そうすると `Gists` ツリーの `Starred Gists` ノードの下にそれらが表示されます。しかし、GitHub ユーザーをフォローして、そのユーザーの現在と未来のすべての gist を簡単に閲覧したい場合は (いちいちスターをつける必要はありません!)、`GistPad.Follow User` を実行して、フォローしたい GitHub ユーザー名を指定します。 これを行うと、 Gistsツリーに新しいノードが表示され、そのユーザーが公開するすべてのパブリック Gist が表示され、他の Gist と同様に open/fork/clone/star を実行することができます。

<img width="252" src="https://user-images.githubusercontent.com/116461/69890797-c03e1800-12ef-11ea-85be-7d6fe2c8c7ef.png" />

### リポジトリへの書き出し

ある時点で、あなたのコードやノートは Gist が提供する機能セットを使い果たすかもしれません（例えば、他の開発者とコンテンツのコラボレーションを開始したい場合など）。そのような場合、gist を右クリックして、`Export to Repository` コマンドを選択するだけで、gist の内容を含む新しい GitHub リポジトリを作成することができます。作成されたリポジトリは、エクスポートされた gist の公開/非公開の状態に応じて、公開または非公開になります。

### スクラッチノート

GistPadでは、新しいことを学ぶにつれて、一時的なメモを簡単に取ることができるように、`Gists` ツリー内の `Scratch Notes` ノードの下にある `New scratch note...` コマンド（または `GistPad: New Scratch Note` コマンドを実行して)をクリックすることで、「スクラッチノート」を作成できます。スクラッチノートは、作成時刻がデフォルトで名前になっているテキストドキュメントです。

スクラッチノートは、デフォルトでは Markdown ドキュメントですが、`GistPad > Scratch Notes.File Extension` の設定をカスタマイズすることで、この動作を変更できます（例：テキスト/AsciiDocなどのファイルを作成）。さらに、スクラッチノートは一日ごとに作成されますが、`GistPad>Scratch Notes: Directory Format` および `GistPad>Scratch Notes: File Format` 設定を変更することで、これをカスタマイズすることができます。

スクラッチノートが `Your Gists` ノードの `Notes` と区別できるようにするために、スクラッチノートは `Gists` ツリーの最上位にある `Scratch Notes` ノードの子として表示されます。これにより、未解決のスクラッチノートを簡単に表示できるため、定期的に確認し、意味のあるコンテンツをより適切な場所（例：新しい Gist または既存の Gist ）に移動することができます。

<img width="200px" src="https://user-images.githubusercontent.com/116461/75699016-908f0b00-5c64-11ea-95d9-e8c8faf93738.png" />

必要なだけスクラッチノートを作成することができます。作業が終わったら、ツリー内の `Scratch Notes` ノードを右クリックし、 `Clear Scratch Notes` を選択することで、個々のノートを削除したり、すべてのノートをクリアしたりすることができます。

> スクラッチノートとは、あなたの代わりに "特別な "秘密の Gist で管理されているファイルです。このように、あなたはノートの短命性に集中することができ、gist の作成/削除を気にすることなくメモをとることができます。

### ショーケース

gists と [code swings](#codeswing) で何ができるかを確認し、コミュニティ内で開発された素晴らしいものに追いつくには、`GistPad` タブの `Showcase` ビューをチェックしてください。これは、Gist のさまざまな使用例を強調するためのカテゴリのリストであり、例とともに表示されます。Gist の `Open` ボタンをクリックすると、その Gist を探索することができ、Gist を展開するとそのファイルの内容を見ることができます。もし、紹介する価値のある gist があれば、issue を発行し、私たちに知らせてください。ショーケースは定期的に更新し、新しいものや面白いものにスポットを当てていきますので、どうぞお楽しみに！

<img width="250px" src="https://user-images.githubusercontent.com/116461/74891549-2c9f4500-533c-11ea-9bbb-c5907d41a589.png" />

### GistLog

Gist を使ってコードスニペットやファイルを共有するだけでなく、[GistLog](https://gistlog.co) を使ってミニブログを作成することができます。ブログを始めるには、`GistPad.New GistLog` コマンドを実行するだけで、新しいブログが作成されます。このコマンドを実行すると、`blog.md` と `gistlog.yml` という 2 つのファイルを含む新しい gist が作成されます。

![GistLog](https://user-images.githubusercontent.com/116461/70856110-fdc3a900-1e8a-11ea-8e26-2c3917e11db0.gif)

`blog.md` が編集用に開かれ、投稿を公開する準備ができたら、`gistlog.yml` を開いて、 `published` プロパティを `true` に設定してください。その後、gist を右クリックして、`Open Gist in GistLog` メニューを選択してください。これにより、投稿の URL が開かれ、共有することができます。

GistLog で個々の投稿を見ることができるだけでなく、 `Your Gists` ツリーノードを右クリックして、 `Open Feed in GistLog` メニューを選択すると、自分のフィード全体を開くこともできます。これにより、公開された GistLog の投稿を表示する GistLog ランディングページが起動します。

## リポジトリ

GistPad では何もローカルにクローンする必要がなく、GitHub リポジトリを作成・編集することができます。まずは、`GistPad:Open Repository` コマンドを実行し、管理を開始したいリポジトリの名前を指定/選択します。新しいリポジトリを作成したい場合は、 `Create new repo` または `Create new private repo` オプションを選択し、リポジトリの名前を指定します。

このコマンドを実行すると、 `GistPad` タブに新しい `Repositories` ツリーが表示され、選択したリポジトリが表示されます。ここから、ファイルの追加、アップロード、編集、削除、名前の変更ができ、裏では、あなたの編集がそれぞれのリポジトリのコミットに変換されます。GistPad は自動的に GitHub とデータを同期させるので、プッシュやプルについて考える必要がありません。あなたはただ編集に集中することができます。🚀

<img width="250px" src="https://user-images.githubusercontent.com/116461/87234682-46dbcd00-c388-11ea-9c57-6ce0e8c3105a.png" />

> 注意：リポジトリを少なくとも1つ管理している場合、`Repositories` ツリーのツールバーにある `+` アイコンをクリックして、新しいリポジトリを作成/管理することができます。

### ディレクトリ

新しいディレクトリを作成するには、単に新しいファイルを追加し、指定したファイルのパスにディレクトリ名を含めるだけです（例：`foo/bar/baz.md`）。GistPad は、ファイル作成プロセスの一部として、必要なディレクトリを作成します。さらに、ファイルをあるディレクトリから別のディレクトリに移動したい場合は、 `Repositories` ツリーでファイルを右クリックし、 `Rename File` を選択し、filepath に新しいディレクトリ名を指定するだけです。

### リポジトリのテンプレート

「ゼロから」新しいリポジトリを作成するだけでなく、[テンプレート](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/creating-a-repository-from-a-template)からリポジトリを作成することもできます。これを行うには、`GistPad：Open Repository` コマンドを実行し、 `Create new repo from template` または `Create new private repo from template` オプションを選択してください。選択できるよく知られたリポジトリテンプレートが表示されますが、任意のリポジトリテンプレートの名前を指定することもできます。

### ブランチ

デフォルトでは、リポジトリを作成/管理するとき、GistPad は `master` ブランチを編集することを想定しています。ただし、リポジトリを管理する場合、指定したリポジトリ名に `#<branch>` を追加することで、別のブランチを指定することができます（例： `vsls-contrib/gistpad#featureA` ）。非マスターブランチを管理している場合、`Repositories` ツリーのリポジトリノードにはブランチ名が表示されます。

いつでもブランチを切り替えたい場合は、`Repositories` ツリーのリポジトリノードを右クリックして、`Switch Branch` を選択してください。これにより、リポジトリのリモートブランチの1つを選択できるだけでなく、新しいブランチを作成することもできます。ブランチを終了する場合は、単にリポジトリを右クリックして、`Delete Branch` または `Merge Branch` を選択してください。後者は `master` に対して `スカッシュマージ` を実行します。ブランチを使用すると、変更セットを `バッチ処理` して、1回のコミットで適用することができます。

### 画像の貼り付け

gist と同様に、画像をクリップボードにコピーし（例：スクリーンショットを撮る、ブラウザで `Copy Image` をクリックするなど）、エディタを右クリックして `Paste Image` を選択するか、以下のキーボードショートカットのいずれかを使ってマークダウンファイルに直接ペーストすることができます： `ctrl+shift+v`（Windows/Linux）_,`cmd+shift+v`（macOS）_。

デフォルトでは、リポジトリファイルに画像を貼り付けると、適切な参照がドキュメントに追加され、`.png` としてリポジトリにアップロードされます。（例： `[title](url)` リンク）。ただし、この動作は、`GistPad > Images: Paste Format` および `GistPad > Images: Paste Type` を設定することで変更できます。詳しくは後述の[設定](#configuration-settings) の項を参照してください。なお、画像を貼り付けると、gist内の `images` というディレクトリにアップロードされます。これを変更したい場合(例えば、代わりに`assets`にしたい場合)は、`GistPad > Images： Directory Name` の設定を行います。

### ウィキ

デフォルトでは、GitHub  リポジトリを作成/管理すると、GistPad  はリモートからアクセスできる「ファイルシステム」のように編集できるようになります。しかし、そのリポジトリを  Roam/Obsidianのような、双方向にリンクされたマークダウンページからなる  Wiki  として使いたい場合は、以下のいずれかの方法で Wiki であることを示すことができます。

1. リポジトリの名前に `wiki` を含める（例：`lostintangent/gistpad-wiki`）
2. リポジトリ自体に `gistpad.json` または `.vscode/gistpad.json` ファイルを追加する

<img width="250px" src="https://user-images.githubusercontent.com/116461/87234704-83a7c400-c388-11ea-90a8-2a660bef4dc5.png" />

> 注意：Foam との互換性のために、GistPad は `.vscode/foam.json` ファイルを含む場合、リポジトリを wiki として認識します。

#### ページ

Wiki は「ページ」で構成されており、マークダウンファイルはファイル名ではなく、`#見出し` で識別されます。そのため、Wiki に新しいページを追加する場合、ファイルパスではなく、タイトルや見出し（例： `Todo List` ）を与えるだけでよいのです。裏では、GistPad が新しいマークダウンファイルを作成し、指定されたタイトルを使って、ファイル名と `#見出し` をあらかじめ入力します。

さらに、新しい Wiki ページを簡単に追加するために、`GistPad.Add Wiki Page` コマンドを実行するか、ステータスバーのノートブックアイコンをクリックしてください。

<img width="75px" src="https://user-images.githubusercontent.com/116461/100490918-7c354d00-30d4-11eb-97d1-28035258656b.png" />

> 注意： Wiki はリポジトリの上に「ページ」という抽象化レイヤーを追加しますが、裏ではまだリポジトリです。そのため、任意の[ファイルやディレクトリ](#files-and-directories)  を Wiki  に追加したい場合は、ツリーのそのノードを右クリックして、`Add New File`  を選択します。

#### デイリーページ

GistPad では、トピック指向のページを作成できることに加え、いつでも「今日のページ」を開くことができるので、日々の進捗や日記を簡単に記録することができます。今日のページを開くには、`Repositories` ツリーのリポジトリノードの右側にあるカレンダーアイコンをクリックします。すると新しいページが開き、現在の日付に基づいたタイトル（例：`June 24, 2020`）が付けられ、`Daily` という名前のディレクトリに配置されます。このページが存在しない場合は、GistPad が作成し、そうでない場合は、既存のページを開くことになります。

<img width="800px" src="https://user-images.githubusercontent.com/116461/87234721-b356cc00-c388-11ea-946a-e7f9c92258a6.png" />

さらに、「今日のページ」を簡単に開くには、 `GistPad： Open Today Page` コマンドを実行するか、ステータスバーのカレンダーアイコンをクリックします。

<img width="75px" src="https://user-images.githubusercontent.com/116461/100490937-a981fb00-30d4-11eb-9e69-e7ab9b9bab61.png" />

> デイリーページが保存されるディレクトリ名を変更したい場合は、 `GistPad>Wikis>Daily.Directory Name` を設定を変更できます。さらにタイトル形式を変更したい場合は、 `GistPad > Wikis > Daily： Title Format` の設定を行います。

#### リンク

ページ間のつながりを作るために、`[[links]]` をページに追加することができます。links を入力すると、GistPad は既存のすべてのページ名の補完リストを表示します。さらに、新しいトピック/ページのタイトルを入力すると、GistPad が自動的にそのページを作成します。

ページに `[[links]]` が含まれている場合、それらはシンタックスハイライトされ、その上にカーソルを置くと、参照したページの文脈を素早く見ることができます。さらに、そのページに直接ジャンプするために、リンクを `cmd+click` することができます。もしそのページがまだ終了していなければ、`cmd+クリック` で自動的にページが作成され、それを開くことができます。このワークフローにより、ウィキ内のページ群のオーサリングとナビゲーションを簡単に行うことができます。

<img width="800px" src="https://user-images.githubusercontent.com/116461/87234714-96ba9400-c388-11ea-92c3-544d9a3bb633.png" />

#### バックリンク

あるページに `[[links]]` を追加すると、参照先のページは自動的に「バックリンク」を検出し、そのページの子ノードとして `Repositories` ツリーに表示します。これにより、`[[links]]`を双方向にナビゲートすることができ、あなたの Wiki が情報の「ネットワーク」を形成することができます。それぞれのバックリンクは参照先のプレビューを表示し、クリックすると選択したページを参照しているページの場所に自動的に移動します。

さらに、バックリンクを含むページを開くと、バックリンクのセットは、バックリンクのラインプレビューを含めてページの下部に表示されます。これにより、実際にはコンテンツそのものを含まない、同じ Wiki 内のページ間のつながりを見るための単なる「トピックアグリゲーター」としてのページを持つことが可能になります。

#### ファイルの埋め込み

ページへのリンクを追加するだけでなく、他のページの内容をノートに直接埋め込んで、簡単に一緒に読むことができるようにすることもあります。これを行うには、 `![[link]]` 構文を使用することができます。埋め込みリンクを使用すると、マークダウンプレビューを表示したときに、ターゲットページのコンテンツがノート内に表示されます。

## コードスイング

Web アプリケーションを構築していて、HTML、CSS、JavaScript（または [ Sass/SCSS、Less、Pug、TypeScript](#additional-language-support)) を試すために素早くプレイグラウンド環境を作りたい場合、VSCode に統合して、CodePen 的な Web 体験をするために [CodeSwing extension] (https://aka.ms/codeswing) をインストールすることができます。GistPad は CodeSwing との統合を提供しているので、インストールしたら、`GistPad` ツリーの `Your Gists` ノードを右クリックして、 `New CodeSwing` または `New Secret CodeSwing` を選択することができます。これにより、選択したテンプレートフィールドをシードした新しい gist が作成され、ライブプレビューの Webview が提供されるため、コードを反復して視覚的にその挙動を確認することができます。

これは、使用する予定のライブラリや言語（ React.js や Vue.js など）を使って、素早く始めるための方法です。スイングは Gist によってバックアップされているため、あなたの変更は保存され、友人と共有することができます。さらに、使いたい他のスイングが見つかったら、それをフォークして自分のスイングを作るだけです。そうすれば、Gist をスイング環境の「テンプレート」として使うことができ、他の Gist と同じように他の人と共同作業することができます。スイングが終わったら、プレビューウィンドウを閉じるだけで、他のすべてのドキュメントが自動的に閉じられます。不要になったスイングは、他の gist と同じように削除してください👍。

## コントリビュートコマンド（ファイルエクスプローラー）

GistPad は `Gists` ビューに加えて、`Explorer` ファイルツリーのコンテキストメニューに `Copy File to Gist` コマンドを提供し、新規または既存の Gist にローカルファイルを簡単に追加することができます。

<img width="260px" src="https://user-images.githubusercontent.com/116461/69831695-58001100-11df-11ea-997e-fc8020556348.png" />

## コントリビュートコマンド（編集）

`Explorer` のファイルツリーコマンドに加え、GistPad はエディタのコンテキストメニューに以下のコマンドを提供します

- `Add Selection to Gist` - ドキュメント全体ではなく、コードのスニペットや選択部分を Gist に追加することができます

- `Paste Gist File` - Gist ファイルの内容をアクティブなエディタに貼り付けることができるようになります

- `Paste Image` - マークダウン、HTML、Pugファイルにクリップボードから画像を貼り付けることができます。このコマンドは自動的に画像をアップロードし、その画像への参照を追加します

<img width="250px" src="https://user-images.githubusercontent.com/116461/69903980-98819b00-1355-11ea-913b-c51981891bcd.png" />

`Copy File to Gist` コマンドは、エディタタブのコンテキストメニューからも利用可能です。

## コントリビュートコマンド（エディタのタイトルバー）

エディタのコンテキストメニューに追加されたコマンドに加えて、GistPad はエディタのタイトルバーメニュー（エディタウィンドウの右上にある `...` をクリック）にも以下のコマンドを提供しています

- `Rename File` - 現在のファイルの名前を変更することができます

## コントリビュートコマンド(コマンドパレット)

この拡張機能では、`Gists` ビューに加えて、以下のコマンドも提供します

- GistPad： Delete Gist` - Gist の一つを削除することができます。Gist のワークスペースを開いている場合は、それを削除してからフォルダを閉じます。

- `GistPad： Follow User` - 他の GitHub ユーザーをフォローすることで、`Gists` ビューからそのユーザーの Gists をブラウザ/アクセス/フォークすることができます。

- `GistPad： Fork Gist` - 現在開いている Gist をフォークし、仮想ワークスペースとして開くことができます。

- `GistPad： Open Gist` - Gist のリストを表示し（サインインしている場合）、選択した Gist のファイルを開く。また、URL、`username/id`、ID で Gist を指定することができ、サインインしている必要はありません。

- `GistPad： Open Gist as Workspace` - `GistPad: Open Gist as Workspace` と同じ動作です。 `GistPad: Open Gist` コマンドと同じ動作ですが、選択した Gist を "loose files" ではなく、ワークスペースとして開きます。

- `GistPad： New Gist` - 新しい [public Gist](https://help.github.com/en/enterprise/2.13/user/articles/about-gists#public-gists) を作成し、その関連ファイルを開きます。Gistに複数のファイルを追加したい場合は、カンマで区切ったファイル名を指定できます（例：`foo.txt, bar.js` ）。

- `GistPad： New Scratch Note` - 新しい "スクラッチノート" を作成します。スクラッチノートとは、`GistPad > Scratch Notes: Extension` と `Gist > Scratch Notes: Format` 設定から派生したファイル名を持つファイルです。

- `GistPad： New Secret Gist` - `GistPad.Gist (Public)` コマンドと同じ動作です。 `New Gist (Public)` コマンドと同じ動作ですが、[secret Gist](https://help.github.com/en/enterprise/2.13/user/articles/about-gists#secret-gists) が作成されます。

- `GistPad： New CodeSwing` - 新しい [CodeSwing](#CodeSwing) を作成します。

- `GistPad： New GistLog` - [GistLog](#gistlog)を作成します。

- `GistPad： Refresh Gists` - gist データをリフレッシュし、`Gists` ツリーを再読み込みします。

- `GistPad： Sign In` - GitHub アカウントでサインインし、Gist を表示/編集/削除します。

- `GistPad： Starred Gists` - スター付きの Gists を一覧表示し、選択した Gists のファイルを開きます。

- `GistPad： Paste Gist File` - アクティブなエディタに Gist ファイルの内容を貼り付けることができます。

## コンフィギュレーション設定

- `Gistpad： Tree Icons` - gists ツリーに gist タイプのアイコンを表示するかどうかを指定します。

- `GistPad > Comments： Show Thread` - gist ファイルを開いたときに、コメントスレッド UI を表示するタイミングを指定します。以下の値のいずれかに設定できます

  - `always`： gist ファイルを開いたときに常にコメントスレッドを表示します。必要に応じて、手動で折りたたむことができます。
  - `never` ： gist ファイルを開いたときに、コメントスレッドを自動的に開かない。必要に応じて手動で展開することができます。
  - `whenNotEmpty` _(default)_： gist ファイルに実際にコメントがある場合に、自動的にコメントスレッドを表示します。それ以外の場合は、折りたたんだままにしておきます。

- `Gistpad > Images: Paste Format`： 画像を gist ファイルに貼り付ける際に使用するマークアップ形式を指定します。以下の値のいずれかを設定します

  - `markdown` _(デフォルト)_： マークダウン形式(例: `![image](link)`): 画像の参照をマークダウン形式で貼り付けます。
  - `html`： `HTML` 形式で画像を貼り付けます (例: `<img src="link" />`). なお、HTMLファイルに画像を貼り付ける場合、設定に関係なく常にこの形式が使用されます。

- `Gistpad > Images: Paste Type` ： 画像を gist ファイルに貼り付ける際に使用する方式を指定します。以下の値のいずれかに設定できます

  - `file` _(デフォルト)_： 貼り付けられた画像は `.png` として gist にアップロードされ、貼り付けられたファイルへの参照が追加されます。
  - `base64`： 貼り付けられた画像は base64 エンコードされ、gist ファイルに埋め込まれます。

- `Gistpad > Images: Upload Directory Name` ： 画像をアップロードするディレクトリの名前を指定します。デフォルトは `images` です。

- `GistPad > Scratch Notes: Directory Format` - 新しいスクラッチノートのディレクトリを生成するときに使用する [moment.js](https://momentjs.com/) フォーマット文字列を指定します。デフォルトは `LL` (例: `March 6, 2020`) です。

- `GistPad > Scratch Notes: File Extension` - 新しいスクラッチノートを生成するときに使用するファイル拡張子を指定します。デフォルトは `.md` です。

- `GistPad > Scratch Notes: File Format` - 新しいスクラッチノートを生成するときに使用する [moment.js](https://momentjs.com/) フォーマット文字列を指定します。デフォルトは `LT` (例: `2:52 PM`) です。

- `GistPad > Scratch Notes: Show` - gists ツリービューにスクラッチノートノードを表示するかどうかを指定します。デフォルトは `true` です。

- `GistPad > Showcase URL` - ショーケースのエントリーを表示する際に使用する URL を指定します。これにより、チームや教室などが独自のショーケースを作成し、チーム内で共有することができます。

- `GistPad > Tracing > Enable Output Channel` - 有効にすると、VSCode 起動時に出力トレースチャンネルが作成されます。
