# 企業研究エンジン 🔍

就活の企業研究を自動化するWebアプリ。Claude API + Web検索 + PDF読み込みで、志望企業の研究レポートを自動生成。

## 機能

- **自動企業調査** — 企業名と志望職種を入力するだけで、9セクションの研究レポートを自動生成
- **Web検索対応** — Claude APIのWeb検索機能で最新の業績・ニュースを反映
- **PDF深掘り分析** — 財報・中期経営計画のPDFをアップロードすると、具体的な数字に基づく逆質問や分析を追加
- **HTMLエクスポート** — 生成したレポートをHTMLファイルとしてダウンロード
- **履歴管理** — 過去の調査結果をブラウザに保存

## 生成されるレポートの構成

| # | セクション | 内容 |
|---|----------|------|
| 01 | 企業概要 | 理念・ビジョン・コア技術・基本情報 |
| 02 | 社会貢献 | 志望理由の「大きな軸」に使えるポイント |
| 03 | 事業領域・製品ライン | 全セグメントの製品・市場ポジション・技術解説 |
| 04 | 最新財務データ | 売上・利益・地域別構成・株主還元 |
| 05 | 中期経営計画 | 目標と達成状況・成長戦略 |
| 06 | 志望理由テンプレ | 大きな軸 + 企業選びポイント2つ |
| 07 | 逆質問案 | 中計・財務ベース5問 + キャリア4問 |
| 08 | 技術知識 | 面接で聞かれそうな用語の平易な解説 |
| 09 | 数字まとめ | 面接で使える重要数字10個以上 |

## セットアップ

### 1. Claude API Keyの取得

1. [Anthropic Console](https://console.anthropic.com) でアカウント作成
2. API Keys → Create Key でキーを発行
3. Settings → Spending Limit で月額上限を設定（推奨: $10）

### 2. デプロイ（GitHub Pages）

```bash
git clone https://github.com/JulienSorel2000/kigyo-research-engine.git
cd kigyo-research-engine
# GitHub Pages は Settings → Pages → Source: main で有効化
```

### 3. 使い方

1. アプリの「設定」タブで API Key を入力
2. 「新規調査」で企業名・志望職種を入力
3. 「企業調査を開始」をクリック
4. （オプション）PDF をアップロードして深掘り分析

## 技術スタック

- React 18（CDN、ビルド不要）
- Claude API（claude-sonnet-4-20250514 + web_search）
- Marked.js（Markdown → HTML）
- GitHub Pages（ホスティング）
- LocalStorage（API Key・履歴の保存）

## セキュリティ

- API Key はブラウザの LocalStorage に保存され、Anthropic API への直接リクエストにのみ使用
- サーバーサイドは一切なし（純粋な静的サイト）
- 個人利用を想定しているため、API Key の露出リスクは Spending Limit で管理

## ライセンス

MIT
