# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 概要

架空の医療系ソフトウェア会社「合資会社 Briareus（ブリアレウス）」の1ページ・コーポレートサイト。主製品は診療予約サービス「Briareus」。ビルド・依存関係・テスト・リンタはなく、`index.html` 単体で完結する静的サイト。

ユーザーとのやり取り・コミットメッセージは日本語。

## 確認方法

ブラウザで `index.html` を直接開く（`open index.html`）。ビルド手順はない。

## 構成

- `index.html` — CSS（`<style>`）と JS（末尾の `<script>`）をすべてインラインで含む単一ファイル。外部リソースは Google Fonts（Zen Kaku Gothic Antique / BIZ UDPGothic / JetBrains Mono）のみ。
  - セクション: ヘッダー → ヒーロー（`<canvas id="ecg">` の心電図アニメーション付き）→ `#philosophy` → `#products` → `#quality` → `#company` → `#contact` → フッター。
  - `#contact-form` はデモ用。JS で入力検証するだけで送信はしない。
- `assets/images/IMG_0385.png` — ロゴ原画像。`assets/images/logo.jpg` はそれを正方形に切り抜き・縮小したもの。
- **ロゴは `index.html` 内に base64 データURI として埋め込まれている**（ヘッダーとヒーローの2箇所）。`assets/images` のファイルは参照されていない。ロゴを差し替える場合は `logo.jpg` を作り直し、両方の `data:image/jpeg;base64,...` を置き換えること。
- このため `index.html` は約230KBあり、大半が base64。全体を Read せず、grep や offset/limit で必要な箇所だけ読むこと。

## デザイン

黒×金の単一テーマ（ライト/ダーク切替なし）。色は `:root` の CSS 変数で定義されており、色を変更するときはここを編集する:
`--bg` #0B0B0B / `--surface` #141412 / `--ink` #EEE8D2 / `--muted` #A69E80 / `--line` #2C2A20 / `--accent` #C9B45C / `--accent-soft` #26220F / `--signal` #E6D38A

## 公開版との関係

このサイトは claude.ai の Artifact（https://claude.ai/artifact/98C4hAVdJXzkGJWJAQ9dA5）としても公開されている。リポジトリの `index.html` と Artifact は自動同期されないため、片方を変更したらもう片方にも反映すること。
