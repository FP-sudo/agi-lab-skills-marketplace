# Content Autopilot

129-skill self-evolving content OS for Claude Code — note, X, Instagram, LinkedIn, YouTube, and more.

**1行で**: コンテンツクリエイターの「作る→分析→改善→再活用→成長」を全自動化するプラグイン。

## Install

```bash
/plugin marketplace add fp-sudo/agi-lab-skills-marketplace
/plugin install content-autopilot@agi-lab-skills
```

## Quick Start

```bash
/setup-profile      # 初回セットアップ（7つの質問に答える）
/daily-autopilot    # トレンド調査 → トピック選定 → コンテンツ生成 → 履歴記録まで全自動
```

## 何ができるか

`/daily-autopilot` を実行すると:

1. **トレンド調査** — WebSearchで最新トピックを3-4件提案（重複排除済み）
2. **トピック選定** — ファネルバランス（TOFU/MOFU/BOFU）を考慮して推奨
3. **コンテンツ生成** — note記事 + X thread + Instagram caption を一括生成
4. **タイトル最適化** — ベストセラータイトルロジック（9カテゴリ）でA/Bテスト用タイトル記録
5. **品質チェック** — 公開前チェックリスト + ブランドボイス一貫性
6. **履歴記録** — content-history.jsonに自動追記（分析の基盤データ）

**出力**: `~/Desktop/content-autopilot-output/` に保存

## 入力と出力の例

### `/daily-autopilot`

入力: コマンドを実行するだけ（profile.jsonから自動読み込み）

出力:
```
~/Desktop/content-autopilot-output/
  note_2026-03-21.md           # note記事（2,000-5,000文字）
  x_2026-03-21.md              # Xスレッド（5-7ツイート）
  instagram_2026-03-21.md      # Instagramキャプション + 30ハッシュタグ
```

### `/analytics`

入力: コマンドを実行するだけ

出力:
```
Content Analytics Dashboard
  Posting: 45 posts | 6.2/week | 12-day streak
  Funnel: TOFU 52% / MOFU 30% / BOFU 18%
  Top logic: Numbers (40%) + Paradox (25%)
  Recommendations: 3 specific action items
```

### `/suggest "Instagramを伸ばしたい"`

入力: やりたいことを自然言語で

出力:
```
Recommended skill chain:
  1. /growth-hack instagram — 成長戦術
  2. /hashtag "topic" — 最適30タグ
  3. /carousel templates — カルーセル構造
  4. /reels "topic" — Reels台本
```

## 主要コマンド（129スキルから厳選）

| コマンド | 何をするか |
|---------|-----------|
| `/setup-profile` | 初回セットアップ（テーマ、読者、スタイル、ファネル設定） |
| `/daily-autopilot` | トレンド→選定→生成→記録のフルパイプライン |
| `/batch 7` | 1週間分を一括生成 |
| `/analytics` | コンテンツ分析ダッシュボード |
| `/advisor` | 今何をすべきか全データから推奨 |
| `/suggest "..."` | 自然言語→最適スキルチェーン |
| `/grade` | 公開前品質スコア（0-100） |
| `/dna` | 自分のコンテンツ成功パターン発見 |
| `/trend-scout` | トレンドリサーチ + 3-4トピック提案 |
| `/repurpose` | プラットフォーム間コンテンツ変換 |
| `/competitor-scout` | 競合分析 + ギャップ発見 |
| `/series 7` | 7日コンテンツシリーズ設計 |
| `/launch` | 14日ローンチキャンペーン |
| `/monetize` | 収益ダッシュボード |
| `/energy low` | 疲れた日の軽量タスク推奨 |

全129スキルの詳細は [plugins/content-autopilot/](./plugins/content-autopilot/) を参照。

## 11レイヤー構成

| Layer | Skills | What |
|-------|--------|------|
| Creation | 20 | 8プラットフォーム + 多形式 |
| Optimization | 18 | SEO, CTA, アルゴリズム, 説得, ナラティブ |
| Analysis | 16 | DNA, 予測, ベンチマーク, ROI, シミュレーション |
| Distribution | 10 | カレンダー, バッチ, リサイクル, 保険 |
| Growth | 12 | 競合, コラボ, チャレンジ, パートナーシップ |
| Monetization | 10 | ファネル, 価格, ローンチ, 講座, 出版 |
| Strategy | 15 | アイデンティティ, 裁定取引, セレンディピティ |
| Precision | 10 | ファクトチェック, 一貫性, アクセシビリティ |
| Feedback | 10 | パフォーマンス, A/B, ポストモーテム |
| Self-Evolution | 8 | メタ学習, 異常検知, 精度レポート |
| Human | 10 | エネルギー, 気分, マイルストーン |

## Capability Levels

| Level | Requirements | Features |
|-------|-------------|----------|
| **Level 1** | Claude Code + WebSearch | テキストコンテンツ全て |
| **Level 2** | + gemini-image MCP | + 自動画像生成 |
| **Level 3** | + X API credentials | + X自動投稿 |

## Demo

(動画準備中)

## License

MIT
