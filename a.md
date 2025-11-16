# はじめに

エンジニアには、QiitaやZennのように技術的な内容を記事としてまとめ、公開する文化があります。  
エンジニアでなくとも、noteのように日々の気づきや本質的な内容を記事として公開し、お金に換えていける時代となりました。  
そんな記事を書いてインターネットに公開することがアドバンテージとなる時代、どのように記事を作成していけばいいのでしょうか。

本書では日々小さく思いつくアイディアの源泉を溜め、膨らませるためのメモ管理術について掘り下げていきます。  
そのメモ管理術がZettelkasten（ツェッテルカステン）です。  
知識管理の手法で、小さなメモ（これはNoteと表現されます）をたくさん作成。それらを紐付け、まとめ、大きな文献を作成していく手法になります。  
もともとはニコラス・ルーマンという社会学者が使っていた知的生産の手法でした。この人はZettelkastenを構築しており、約50冊の本と約550の寄稿を執筆したとされています。(wikipedia参照)

2025年、生成AIの発展につれてObsidian、Notionが注目されるにあたり、Zettelkastenにもスポットライトがあたりました。  
第二の脳として機能するだけでなく、文章として残るため生成AIのコンテキストとしても機能するためです。

今回はそんなZettelkastenをNotionでシステム構築する手法を紹介します。

## Zettelkastenについて

Noteは下記表のようにレベルを分け、Noteを相互リンクさせます。  
各Noteにはタグなどのメタ情報を付与し管理しやすくします。

| レベル | 説明 |
| --- | --- |
| アイディアノート | 思いつきのメモや記事をスクラップするノートです。<br/>他インターネット記事では思いつきのメモを一時メモ、記事のスクラップを文献メモで分けられています。<br/>私は分けない方が使いやすかったためアイディアノートとしてまとめています。 |
| パーマネントノート | アイディアノートをまとめて文書化をここで行います。<br/>記事の「章」に当たるものとして、アイディアをまとめます。 |
| ストラクチャーノート | パーマネントノートをまとめて文書化します。<br/>これが記事の内容となります。 |

## notionについて

クロスプラットフォームな高機能ドキュメントツールです。  
基本的には無料で使えますが、AIを使ったり他のアカウントとコラボレーションしたりするには有償プランの契約が必要となります。  
今回は無料で行える機能を用いてZettelkastenの構築が可能です。

「ページ」と「ブロック」という単位で管理され、ページはブロックの集合体となります。  
「ページ」はその通りページであり、ブロックというのは各文やテーブル、メディアといったコンテンツ一つ一つになります。  
Notionはマークダウンにある基本機能にとどまらず、データベースを作成しそこからチャートを作成したり、簡単なオートメーションを組んで操作の自動化をしたりもできます。  
本書ではNotionのデータベース機能を用いてシステムを構築します。

# 作り方

## データベースを構築する

Notionのデータベース(以降DB)は、DBそのものもDBのレコードもページとして作成されます。  
DBは各ノート層+これらにつけるタグを入れるDBの、4つDBを作成します。  
DBはいずれも「データベース: フルページ」で作成します。

### コールアウト

Notionはページ内にページを作成して階層化します。  
今回はDBを4つDBを作成する必要があるため、ページを作成しまとめる箇所を最初に作っておくとページが綺麗になります。  
「コールアウト」を用いてDBのページをまとめておく部分をページ上に作成しましょう。

![callout-command.png](./assets/callout-command.png)

<table>
  <tr>
    <td><img src="./assets/callout-icon.png" alt="callout-icon.png"></td>
    <td><img src="./assets/callout-title.png" alt="callout-title.png"></td>
  </tr>
</table>

### Tag DB

まずはメタ情報となるタグを格納するDBを作成します。  
DBは「データベース: フルページ」で作成します。

![tag-database-command.png](./assets/tag-database-command.png)

下記のようになります。

<table>
  <tr>
    <td><img src="./assets/tag-db-page-empty.png" alt="tag-db-page-empty.png"></td>
    <td><img src="./assets/tag-db-page-block.png" alt="tag-db-page-block.png"></td>
  </tr>
</table>

なくてもOKですが、タグもカテゴライズした方が便利なのでtags DBにプロパティを追加します。

<table>
  <tr>
    <td><img src="./assets/tag-db-propaty-select.png" alt="tag-db-propaty-select.png"></td>
    <td><img src="./assets/tag-db-propaty-category.png" alt="tag-db-propaty-category.png"></td>
  </tr>
</table>

レコードを追加する前にタグカテゴリを作成します。  
フォームに作成したいタグカテゴリ名を入力し、エンターを押すことで新規にタグカテゴリが作成されます。

![tag-category.png](./assets/tag-category.png)

レコードを追加します。  
右上の「新規」または、DB末尾の「新規ページ」をクリックすることで新規レコードが追加できます。

![tag-db-records.png](./assets/tag-db-records.png)

### Idea Note DB

アイディアノートを格納するDBを作ります。  
Tag DBで行ったのと同様に、DBを作成しましょう。  
「データベース: フルページ」で作成します。

![idea-database-command.png](./assets/idea-database-command.png)

下記のようになります。

<table>
  <tr>
    <td><img src="./assets/idea-db-page-empty.png" alt="idea-db-page-empty.png"></td>
    <td><img src="./assets/idea-db-page-block.png" alt="idea-db-page-block.png"></td>
  </tr>
</table>

Idea DBにプロパティを追加します。  
本書ではシンプルにTag DBとのリレーションのみを追加します。

1. リレーションプロパティの追加を選択

![idea-db-add-tag-db-relation.png](./assets/idea-db-add-tag-db-relation.png)

2. リレーション対象に、先ほど作成したTag DBを選択

![idea-db-relation-target-tag-db.png](./assets/idea-db-relation-target-tag-db.png)

3. 「リレーションを追加する」をクリック

![idea-db-add-relation-confirm.png](./assets/idea-db-add-relation-confirm.png)

Tag DBにはタグカテゴリも用意しているため、ロールアップ機能を用いてリレーションを貼ったタグのカテゴリもプロパティとして持たせます。

1. ロールアッププロパティの追加を選択

![idea-db-add-tag-db-rollup.png](./assets/idea-db-add-tag-db-rollup.png)

2. 「プロパティを編集」 > 「リレーション」 > 「tags」を選択

![idea-db-edit-rollup-propaty.png](./assets/idea-db-edit-rollup-propaty.png)

3. 「ターゲットプロパティ」に「カテゴリ」を選択

![idea-db-edit-rollup-target-tag-propaty.png](./assets/idea-db-edit-rollup-target-tag-propaty.png)

4. プロパティ名を「タグカテゴリに変更」

![idea-db-edit-rollup-colum-name.png](./assets/idea-db-edit-rollup-colum-name.png)

下記キャプチャのようになっていれば成功です。

![idea-db-complete-column-empty.png](./assets/idea-db-complete-column-empty.png)

### Permanent Note DB

パーマネントノートを格納するDBを作ります。  
やり方はここまでで記載しているため、手順のみ記載します。

1. 「データベース: フルページ」で「Permanent」DBを作成
2. データベースのプロパティを下記の通りに追加

| プロパティ名 | 種別 | DB先/プロパティ |
| --- | --- | --- |
| idea | リレーション | idea DB |
| tags | リレーション | tag DB |
| タグカテゴリ | ロールアップ | tag DB / カテゴリ |

下記キャプチャのようになっていれば成功です。

![permanent-db.png](./assets/permanent-db.png)

### Structure Note DB

ストラクチャーノートを格納するDBを作ります。

1. 「データベース: フルページ」で「Structure」DBを作成
2. データベースのプロパティを下記の通りに追加

| プロパティ名 | 種別 | DB先/プロパティ |
| --- | --- | --- |
| permanent | リレーション | permanent DB |
| tags | リレーション | tag DB |
| タグカテゴリ | ロールアップ | tag DB / カテゴリ |

下記キャプチャのようになっていれば成功です。

![structure-db.png](./assets/structure-db.png)

## インラインDBを表示させる

# 利用実例

# おわりに
