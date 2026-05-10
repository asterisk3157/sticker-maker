# Repository rules for Claude

このファイルはこのリポジトリでClaude Codeセッションが開始されるときに読み込まれます。以下のルールは必ず守ってください。

## Git push policy

`git push` を実行する前に必ず:

1. `git status` を実行し、出力をユーザーに見せる
2. `git log -1 --oneline` で送信される最新のコミットを表示
3. 現在のブランチが意図した push 先と一致するか確認
4. `main` ブランチにいるときだけ `origin/main` への push を許可
5. **`main` 以外のブランチにいる場合は、ユーザーに確認を取るまで push しない**

## 禁止フラグ（明示的な指示がない限り使わない）

- `git push --force` / `git push --force-with-lease`
- `git push --all`
- 異なるリモート (`git push <other-remote>`) への push

ユーザーが明示的にこれらを要求した場合も、必ず意図を確認してから実行する。

## ブランチの取り扱い

- 確認なくブランチを削除しない
- `main` ブランチで rebase / 履歴書き換えをしない
- `git reset --hard` は明示的に指示された場合のみ
- 新規ブランチを作る場合、用途を明示してからユーザーに確認

## デプロイ環境

- `main` ブランチへの push は本番環境にデプロイされる: https://sticker-maker.shironoir.com
- 他ブランチへの push は Cloudflare Pages のプレビュー環境のみに反映される（本番には影響しない）

## アプリの基本方針

- 機能はクライアント完結（画像をサーバーへ送信しない）
- 専門用語は避け、初見ユーザーに優しいラベルを使う
- ブランド名（特定のコンビニ印刷サービス名）はアプリ内のラベルには出さない
