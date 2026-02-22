# Claude Codeで初めてのOSSコントリビューション体験記

## はじめに

GitHub初心者がOSSに初めてコントリビュートする定番リポジトリ「first-contributions」に、Claude Codeを使ってチャレンジしてみました。途中でハマったポイントも含めて、手順をまとめます。

## first-contributionsとは

[first-contributions](https://github.com/firstcontributions/first-contributions) は、OSSへの初めてのコントリビューションを体験するためのプロジェクトです。`Contributors.md` に自分の名前を追加してPull Requestを出す、というシンプルな手順でGitHub上でのコントリビューションの流れを学べます。

## 実際の手順

### 1. フォーク

まず、本家リポジトリ `firstcontributions/first-contributions` を自分のアカウントにフォークします。

### 2. クローン

フォークしたリポジトリをローカルにクローンします。

```bash
git clone https://github.com/hang-up33/first-contributions.git
cd first-contributions
```

### 3. ブランチ作成

作業用のブランチを作成します。

```bash
git switch -c add-hang-up
```

### 4. Contributors.mdに名前を追加

`Contributors.md` をエディタで開き、自分の名前を追記します。

### 5. コミット & プッシュ

変更をステージングしてコミットし、リモートにプッシュします。

```bash
git add Contributors.md
git commit -m "Add hang-up to Contributors list"
git push -u origin add-hang-up
```

### 6. プルリクエスト作成

ここが一番のポイントでした。

## ハマったポイント：PRの向き先に注意！

Claude Codeからプルリクエストを作成したところ、**自分のフォーク（`hang-up33/first-contributions`）に対してPRが作られてしまいました**。

本来は本家リポジトリ（`firstcontributions/first-contributions`）に対してPRを出す必要があります。自分のフォークにPRを出しても、本家にはマージされません。

### 解決方法

GitHubのCompare画面を使って、手動でフォーク元を指定してPRを作成しました。

```
https://github.com/firstcontributions/first-contributions/compare/main...hang-up33:first-contributions:main
```

このURLにアクセスすると、以下の比較ができます：

- **base repository**: `firstcontributions/first-contributions` （本家）の `main`
- **head repository**: `hang-up33/first-contributions` （自分のフォーク）の `main`

ここから「Create pull request」を押すことで、正しく本家に対してPRを作成できました。

結果、**auto mergeされて無事コントリビューション完了**です！

## Claude Codeを使ってみた感想

### 良かった点

- Contributors.mdへの名前追加、コミット、プッシュなど基本的なGit操作はスムーズに進められた
- ハマった時に原因の特定と解決策の提示が早かった

### 注意点

- **PRの向き先はしっかり確認する**。CLIからPRを作成する場合、フォーク先ではなく自分のリポジトリに向いてしまうことがある
- 最終的にGitHubのWeb UIで確認・操作するのが確実

## まとめ

| ステップ | 内容 |
|---------|------|
| フォーク | 本家リポジトリを自分のアカウントにフォーク |
| クローン | ローカルにクローン |
| ブランチ作成 | 作業用ブランチを切る |
| 編集 | Contributors.mdに名前を追加 |
| コミット & プッシュ | 変更をコミットしてプッシュ |
| PR作成 | **本家リポジトリに対して**プルリクエストを作成 |

一番大事なのは、**PRの向き先が本家リポジトリになっているか確認すること**です。特にCLIツールからPRを作成する場合は要注意です。

初めてのOSSコントリビューション、ぜひ挑戦してみてください！
