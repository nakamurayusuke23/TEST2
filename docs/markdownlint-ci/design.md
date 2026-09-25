# markdownlint の CI

## 目的

リポジトリ内の Markdown の書式を、PR の時点で自動チェックする。

## 要件

- `main` への push と、`main` 向けの PR で実行する
- 全ての `*.md` を対象にする
- 日本語の文章で誤検知しやすいルールは無効にする
- やらないこと: 自動修正のコミット

## 仕様

- ツール: markdownlint-cli2（GitHub Action `DavidAnson/markdownlint-cli2-action`）
- 設定: `.markdownlint-cli2.jsonc`
  - MD013（1行の長さ）: 無効。日本語は長い行になりやすい
- 違反があればジョブを失敗させる

## 実装方針

- 追加: `.github/workflows/markdownlint.yml`、`.markdownlint-cli2.jsonc`
- 既存の Markdown に違反があれば、同じ PR で直す

## 未決事項

- ブランチ保護で必須チェックにするか
