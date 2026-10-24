# 横浜ホテル比較レポート

2027年4月27日チェックイン・4月28日チェックアウト、大人2名・1室・1泊の比較レポート。調査日時は2026年10月22日です。既存のデザイン・料金・口コミ・出典・写真の権利表示を維持しています。

## 公開対象（この6ファイルだけ）

| ファイル | 用途 |
| --- | --- |
| `index.html` | 本体。CSS・JavaScript・写真3点・16施設のデータを内包 |
| `hotel_report.pdf` | 既存の「PDF版を開く」リンク用 |
| `research_data.json` | 既存の調査データダウンロード用 |
| `.nojekyll` | Jekyll処理を無効にして静的ファイルを配信 |
| `README.md` | この手順書（公開情報） |
| `.gitignore` | 上記以外をGit管理対象から除外する許可リスト |

`README.txt` と `.local-check/` はローカル専用です。PDF・JSONはリンク機能の維持に必要なため公開します。HTML単体でも閲覧・絞り込み・お気に入り比較・メモ保存が動作しますが、別ファイルのダウンロードにはPDF・JSONも必要です。

新しいライブラリ、フレームワーク、ビルド処理、APIキー、サーバー処理は不要です。株式分析プロジェクトのファイルは対象外です。

## GitHub Pagesで無料公開する手順（確認後に実施）

1. GitHub Freeで新しい **Public** リポジトリを作成します。例：`yokohama-stay-guide`。株式分析リポジトリを流用せず、既存のGit履歴も移植しません。
2. 上の6ファイルだけをリポジトリのルートに配置します。フォルダ全体をアップロードしないでください。ブラウザのアップロード操作には `.gitignore` の除外は適用されません。
3. Gitを使う場合は、この専用フォルダに `.git` がなく、親リポジトリを使っていないことを確認してから新規初期化します。以下は将来実行するための例で、準備作業では実行していません。

   ```powershell
   git init -b main
   git add -- index.html hotel_report.pdf research_data.json README.md .gitignore .nojekyll
   git diff --cached --name-only
   git diff --cached --check
   git commit -m "Prepare Yokohama hotel report for GitHub Pages"
   git remote add origin https://github.com/YOUR-ACCOUNT/yokohama-stay-guide.git
   git push -u origin main
   ```

   ステージされたファイルが6つだけであることを、commit・push前に確認します。`git add -f` は使用しません。`.gitignore` は既に追跡されたファイルや過去の履歴から情報を削除する機能ではありません。

4. リポジトリの **Settings → Pages → Build and deployment → Source** で **Deploy from a branch** を選択します。
5. **Branch: main / Folder: /(root)** を選び **Save**。ActionsのPagesデプロイが完了するまで待ちます。
6. Pagesの **Visit site** から `https://YOUR-ACCOUNT.github.io/yokohama-stay-guide/` を開きます。無料の標準URLを使い、有料ドメインは不要です。
7. 公開URLでも375px表示、価格帯、お気に入り、予約先、PDF・JSONのリンクを再確認します。ブラウザにより反映まで時間がかかります。

公式手順： [サイトの作成](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site)、[公開元の設定](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)。2026年10月24日確認。GitHub FreeではPublicリポジトリを使います。

## ローカル確認

`index.html` を通常のブラウザで直接開けます。ローカルファイルでの保存可否はブラウザ設定によります。お気に入りは端末・ブラウザ・オリジンごとのlocalStorage保存で、公開URLへ自動移行・同期しません。保存が拒否されてもページ内での比較は継続できます。

検証補助を使う場合は `node .local-check/server.cjs` を起動し、`http://localhost:8767/check` を開きます。375pxのiframe内で価格帯、最大5件のお気に入り、会員料金除外、検索、リンク整合性を検査します。この補助フォルダは公開しません。

## 公開前の注意

- HTMLに加えPDF・JSONの全内容、写真、宿泊予定日・人数・旅行条件も誰でも閲覧・ダウンロードできます。この旅行条件を公開してよいか最終確認してください。
- 予約料金・空室は常に変動します。調査値は更新していません。遷移先で日付・人数・部屋タイプ・税・手数料・キャンセル条件を確認してください。外部サイトの表示、アクセス制限、URL変更、在庫は保証できません。
- 写真3点の出典、著作者、CC BY-SA / CC0の表示を残してください。HTML全体に写真と同じライセンスを一括適用するものではありません。
- 衛生面の記述は調査時点の投稿・公表資料に基づくものです。現在の施設状況の断定ではありません。公開前に原文と表現をご自身でも確認してください。
- 認証情報のパターン検査、本文・URL・PDFメタデータ・添付の確認ではAPIキー、パスワード、個人のメールアドレス、ローカルユーザーパスは検出していません。機械検査で公開リスクを完全には保証できません。
- お気に入りのサーバー送信、解析タグ、外部ライブラリ読み込みはありません。予約先や出典を開くと外部サービスへ接続します。
- 公開用6ファイルとGit履歴を再確認し、バックアップ・検証ファイル・認証ファイルをアップロードしないでください。

リポジトリ作成・commit・push・公開操作はこの準備段階では行っていません。
