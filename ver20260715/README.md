# Handoff: OFFLINE GATHERING 2026 ／ 奥日光しおり

> **最終更新**: 2026-07-15（部屋割りリンクボタン追加 反映版）
> **対象デザインファイル**: `index.html`（単一HTMLに全ページ／CSS／JSを内包）
> **状態**: 高忠実度モックアップ・実運用直前フェーズ（社内配布用しおり）

---

## Overview

「OFFLINE GATHERING 2026 ／ 奥日光編」は、グローバルエージェンツの社内オフサイト（**1泊2日／2026年7月16日(木) - 17日(金)、UNWIND HOTEL & BAR 奥日光**）向けの **モバイル向け旅のしおり Webページ** です。

参加者が事前確認・当日携行できる **ホーム＋7サブページのSPA構成のしおり** で、以下を含みます：

- 旅のテーマ（"New Face(s)"）
- 旅の概要（日程・場所・参加人数・会社負担範囲）
- ホームからのメニューナビゲーション（01〜07）
- 2日間のスケジュール（東京組／地方組の分岐タイムライン）
- DAY1 アクティビティ（足尾銅山 → 東照宮 → 夕食 → ゲーム → 二次会 → **23:00 星を見に行く**）
- DAY2 アクティビティ一覧（バス着順の4プラン：A→B→C→D）＋ **13:50 集合の移動方法分岐**
- 移動方法（**HOTEL GRAPHY 渋谷 集合場所ハイライト付き**）
- 旅の準備（持ち物・天気・昼食・宿泊）、注意事項、LINE案内、幹事＆スタッフ紹介
- 動画ギフト（サブページ）

---

## About the Design Files

このバンドルに含まれる `index.html` は **HTMLで作成されたデザインリファレンス（プロトタイプ）** です。意図した見た目・情報構造・インタラクションを示すためのものであり、そのまま本番投入するコードではありません。

開発者の作業は、**このHTMLデザインを、対象コードベースの既存環境（React／Vue／Next.js／Astro／SwiftUI等）で、その環境のパターンとライブラリを使って再現すること** です。専用の環境がまだ無い場合は、プロジェクトに最適なフレームワーク（本用途なら軽量な静的サイト向け：**Next.js／Astro／Nuxt** などが有力）を選定して実装してください。

デザインは日本語コンテンツ・モバイルファースト（`max-width: 480px` のカラム）・**SPA的なページ切替**（`showPage()` で `.page` を出し分け、ハッシュURL同期）前提です。

---

## Fidelity

**High-fidelity（ハイファイ）** です。

- 最終的な配色・タイポグラフィ・余白・角丸・シャドウ・アニメーションまで決定済み。
- 本HTMLに書かれた具体的な値（hex, px, font-family, line-height, transition）を **そのまま採用してください**。
- 挙動（ページ切替、アコーディオン、タブ切替、リビール・オン・スクロール、タイムラインの詳細ポップアップ）も再現対象です。

---

## Recent Updates（直近の変更点・実装で必ず反映）

以下は最終合意された最新スケジュールです。実装時、必ず本README準拠 or 最新 `index.html` から値を取得してください。

### 2026-07-15 追加分

- **部屋割り表への外部リンクボタンを追加**
  - 場所：「旅の準備」ページ 04-D Stay セクション末尾（`<section id="sec-hotel">` 内、`.check-note`（相部屋について）の直下）
  - 実装クラス：`.room-assign-link`（新設）
    - 構造：`.ral-icon`（グリッドSVG）＋ `.ral-text`（`.ral-label` / `.ral-title` / `.ral-sub`）＋ `.ral-arrow`（外部リンク矢印SVG）
    - 背景：`linear-gradient(135deg, var(--green) 0%, var(--green-deep) 100%)` + 右上に琥珀色 radial-gradient のグロー装飾（`::before`）
    - 影：`box-shadow: 0 8px 20px -12px rgba(30,69,48,.55)`、角丸 `12px`、padding `16px 18px`
    - アイコンボックス：44×44px、`background: rgba(255,255,255,.14)`、`border: 1px solid rgba(255,255,255,.22)`、アイコン色 `var(--amber-soft)`
    - ラベル：`Room Assignment`（`Outfit`, 10px, letter-spacing .22em, `--amber-soft`）
    - タイトル：`部屋割り表を確認する`（`Zen Maru Gothic 900`, 15px, `#fff`）
    - サブ：`Google スプレッドシートで開きます`（11.5px, `rgba(255,248,240,.7)`）
  - リンク先：`https://docs.google.com/spreadsheets/d/1OKXxcSesCf6UQY0yzbLz8CmJ1PmDZkHAz7jfEEP-xmU/edit?usp=sharing`
  - 属性：`target="_blank"` `rel="noopener"`
- **「相部屋について」の文言更新**
  - 旧：`詳細は後日ご案内します。`
  - 新：`下記の部屋割り表よりご確認ください。`

### 2026-07-14 追加分

- **DAY2 Aプラン（戦場ヶ原トレッキング）に「服装・持ち物」注意事項カードを追加**
  - 場所：「Activities」ページ DAY2 セクション Aプランのアクティビティカード内
  - 実装クラス：`.activity-card .ac-notice`（新設）
    - `.ac-notice-head`（`Note` amber pill ＋ 見出し「服装・持ち物について」）
    - `.ac-notice-list`（琥珀ドット付きの6項目）
    - `.ac-notice-foot`（緑ベース薄背景の補足文）
  - 記載内容（原文）：
    1. **レインウェア**：「上下セット」がおすすめです。
    2. **靴**：歩きやすい靴（**防水性のあるもの**がおすすめ）。
    3. **バッグ**：両手が空くリュックやナップザック。
    4. **飲み物（500〜1000ml）**：コース途中に売店はありません。スタート地点（**湯滝のお茶屋さん**）で必ず準備を！
    5. **防寒着**：予想気温 **13〜19℃**（思ったより寒いです！）。体温調節しやすい上着を。
    6. **日焼け対策**：晴れると日差しが強いため、日焼け止めはお忘れなく。
    - 補足文：`※本格的な登山装備でなくても大丈夫です。動きやすさ・体温調節・両手をあけることを意識してご準備ください。`
- **フリーワイン（DAY1 17:00）会場を「ロビー」で確定**
  - 詳細タイムライン `day1[]` 17:00 の `detail` から「※施工の進捗状況により、ホールまたはダイニングに変更になる可能性あり。」の注釈を削除
  - 表記：`◆ 会場：ロビー`

### DAY1（7/16 木）東京組
- **06:45** HOTEL GRAPHY 渋谷 集合（旧: 07:30 集合）
- **07:15** バス出発（旧: 07:45）
- 集合場所詳細： **入口に向かって左、「89」の柱がある駐車場**（屋外・屋根あり）
  - 対応するストリートビュー画像を `assets/meetup-hotel-graphy.png` に同梱
  - 「移動」ページ 東京組カード DAY1 内に `.tc-meetup` として画像＋説明を掲載

### DAY1 二次会（21:30 - 24:00）
- **23:00 星を見に行く** ✨ 希望者で奥日光の夜空を鑑賞する項目を追加
  - アクティビティカードでは `.ac-sublist` の小項目として表示
  - 詳細タイムライン（`day1[]`）ポップアップにも同項目を追記

### DAY2（7/17 金）
- 朝食（07:00）ブロックに **「できるだけ朝食前にチェックアウト」** の注意書きを追加
- **退館式 08:25**（旧: 08:30）
- **全員バス乗車 → 各アクティビティへ 08:45**
- Dプラン（mekke ワークショップ）の方は **公共バスで移動**：**8:37 湯元温泉（バス停）出発**
- **13:50 日光駅周辺 集合** — アクティビティにより移動方法が分岐：
  - 🚌 **団体バス**：A（戦場ヶ原）／ B（中禅寺湖SUP）
  - 🚶 **直接日光駅へ**：C（東照宮）／ D（mekke ワークショップ）
- 上記分岐は
  - DAY2 アクティビティ一覧ページ末尾の `.reunite-card`
  - 「移動」ページ 東京組 DAY2 ブロック内の `.tc-reunite`
  - 詳細タイムライン（`day2[]`）の該当項目ポップアップ
  - 「移動」ページ 地方組 DAY2 タイムライン（13:50行）
  の**4カ所すべて**に反映済み。

---

## Screens / Views

このデザインは **ホーム1ページ ＋ サブページ7枚** の構成です。`.page[data-page=...]` を `showPage(name)` で `.active` を付け替えて出し分けます（ハッシュURLも同期）。

| # | data-page | サブページタイトル |
|---|---|---|
| — | `home` | ホーム（表紙・テーマ・概要・メニュー） |
| 01 | `schedule` | Schedule（2日間の詳細タイムライン） |
| 02 | `activities` | Activities（DAY1 + DAY2 アクティビティ一覧） |
| 03 | `transport` | How to get there（東京組／地方組の移動） |
| 04 | `prep` | Pack · Weather · Lunch · Stay |
| 05 | `info` | rules（注意事項・LINE案内） |
| 06 | `people` | Organizers & UNWIND Staff |
| 07 | `videogift` | Video Gift（動画ギフト） |

### 全体レイアウト

- モバイル1カラム、`max-width: 480px`、`margin: 0 auto`
- 背景：`--bg (#FFF8F0)` に紙のようなドットグレイン（`radial-gradient` を fixed で敷いたパターン、`mix-blend-mode: multiply`）
- 全体タイポ：
  - `Zen Maru Gothic` weight 400/500/700/900 … 本文和文（`--maru`）
  - `Outfit` weight 300-700 … 欧文・数値・ラベル（`--en`）
  - `Shippori Mincho` weight 500/700 … 一部見出し（`--serif`）

### セクション見出しの共通パターン
- `.sec-eyebrow` … 上部の小さなラベル：番号バッジ（`.num` amber）+ 英字ラベル（`Outfit`, `letter-spacing:.25em`）
- `.sec-title` … 大きな和文タイトル（`Zen Maru Gothic 900`, 24-28px）
- `.sec-lead` … 導入テキスト（14-15px, `--ink-2`）

### サブページ共通ヘッダー `.subpage-bar`
- 左：`← Home` ボタン（`.back-link`、`goHome()` を呼ぶ）
- 右：`.sp-title` … `01 · Schedule` などの現在ページ名

---

## Key Components 詳細

### 1. Meetup Card（HOTEL GRAPHY 渋谷 集合場所ハイライト）
場所：「移動」ページ 東京組カード DAY1 ブロック内
クラス： `.tc-meetup`

- 左に amber 4px ボーダー、ベースは `linear-gradient(180deg, #fffaf3 0%, #fff 100%)`
- 構成：
  1. `.tcm-head`：`Meetup` タグ（amber pill） + 📍 + `集合場所の詳細`
  2. `.tcm-figure`：ストリートビュー画像＋キャプション（赤枠内が集合スペース／右奥が HOTEL GRAPHY 入口）
     - 画像：`assets/meetup-hotel-graphy.png`
  3. `.tcm-body`：本文（`「89」の柱がある駐車場` を `.hi` クラスで amber 蛍光マーカー装飾）
  4. `.tcm-points`：3項目の注意ポイント（目印／館内ではなく屋外／雨天も同じ場所）
  5. `.tcm-map`：Google マップで開くボタン（緑塗り→ ホバーで `--green-deep`）

### 2. Reunite Card（DAY2 13:50 日光駅周辺 集合の移動方法分岐）
場所：「Activities」ページ DAY2 セクション末尾
クラス： `.reunite-card`

- 左に amber 4px ボーダー、白カード
- `.ru-head`：時刻バッジ（amber, `13:50 / MEET`）＋ 見出し `日光駅周辺 集合`
- `.ru-split`：`grid-template-columns: 1fr 1fr`（560px以下では1列に）
  - 左：`🚌 団体バス`（緑バッジ）／ A, B プラン
  - 右：`🚶 直接日光駅へ`（amber バッジ）／ C, D プラン
- `.ru-plan`：プラン記号（A/B/C/D）を24×24pxの黒枠バッジで表示
- `.ru-foot`：`⚠ 集合場所は当日ご案内。時間厳守でお願いします。`

### 3. Transport Reunite Sub-Block（移動ページ・東京組 DAY2 内の簡易版）
クラス： `.tc-reunite`
- コンパクト版の分岐表示。緑左ボーダー、`13:50 集合` タグ＋2行のバッジ＋プラン内訳。

### 4. Activity Sub-list（`.ac-sublist`）
アクティビティカード内の補足リスト（例：二次会カードの「23:00 星を見に行く」、Dプランの「移動：公共バス／8:37 湯元温泉発」）。
- `background: rgba(42,92,64,.05)`、緑3px左ボーダー、`b` で緑の時刻数字を強調。

---

## Interactions & Behavior

### ページ切替
- `showPage(name, ev)` … `.page.active` を1枚だけに付け替え。`window.location.hash` を同期。
- `goHome()` … `showPage('home')` のショートカット。ハッシュ変更時は `hashchange` で同期。

### アコーディオン（`.acc`, `.acc-head`, `.acc-body`）
- クリックで `.open` トグル、`max-height` を JS で計測し高さアニメーション。
- 用途：注意事項、宿泊、天気の詳細など。

### タブ切替（`data-tab`, `data-panel`）
- 昼食候補（東照宮周辺／日光駅周辺）の切替、幹事／スタッフの切替に使用。
- クリックで `.active` を付け替え、対応する `[data-panel="key"]` を表示。

### 詳細タイムラインの popup（Schedule ページ）
- `day1[]` / `day2[]` の配列データを `renderSchedule()` で描画。
- 各アイテムに `detail`（HTML文字列）があり、`<details>` 相当の展開UIで表示。
- `key: true` の項目は amber 強調（重要ステップ）。
- `group: "tokyo" | "local"` で東京組／地方組の分岐セクション見出しを挿入。

### リビール・オン・スクロール（`.reveal`）
- IntersectionObserver で `.in-view` 付与、`opacity` + `translateY` トランジション。
- しきい値：`threshold: 0.12`、`rootMargin: '0px 0px -8% 0px'`。

---

## State Management

現状は **バニラJS + hashchange** で完結しており、フレームワーク化する場合は下記の状態を持てば十分：

| 状態 | 説明 |
|---|---|
| `currentPage` | `home` / `schedule` / `activities` / `transport` / `prep` / `info` / `people` / `videogift` |
| `peopleSubTab` | `organizers` / `staff`（people ページ内） |
| `lunchTab` | `toshogu` / `station`（prep ページの昼食候補） |
| `openAccordions: Set<string>` | 開いている accordion の id 集合 |

データ層は **静的**（`day1`, `day2` 配列と、ロケーション情報の配列）ですが、React／Vue化時は JSON へ切り出すのがクリーンです。

---

## Design Tokens

```css
:root{
  /* Base */
  --bg:        #FFF8F0;   /* 紙色ベース */
  --bg-2:      #F5EBD8;   /* 薄い紙色 */
  --bg-alt:    #E8E4D0;   /* さらに落とした紙色 */

  /* Brand */
  --green:      #2A5C40;  /* 主色（森／奥日光） */
  --green-deep: #1E4530;  /* 主色 濃 */
  --amber:      #D4854A;  /* アクセント（琥珀） */
  --amber-soft: #E8A876;  /* 琥珀 淡 */

  /* Ink（テキスト） */
  --ink:   #2C1A0E;
  --ink-2: #5C4838;
  --ink-3: #8A7560;

  /* Line */
  --line: #D9C9B2;

  /* Shadow */
  --paper-shadow: 0 1px 0 #E8DBC1, 0 12px 24px -16px rgba(44,26,14,.18);

  /* Fonts */
  --maru:  "Zen Maru Gothic", "Hiragino Maru Gothic ProN", "Hiragino Sans", "Yu Gothic", system-ui, sans-serif;
  --en:    "Outfit", "Inter", system-ui, sans-serif;
  --serif: "Shippori Mincho", "Yu Mincho", serif;
}
```

### Spacing / Radius / Type Scale（実装で頻出する値）

- **カード padding**: `20px 22px` 〜 `24px 22px`
- **カード border-radius**: 10 / 12 / 14 / 18 / 20 px（用途で使い分け）
- **セクション間 margin**: `36-48px`
- **本文サイズ**: 13-15px、行間 `1.7-1.85`
- **見出し**: `.sec-title` 24-28px `Zen Maru Gothic 900`
- **数字・時刻**: `Outfit 600-700`、時計は 18-22px

---

## Assets

すべて `assets/` に同梱。

| ファイル | 用途 |
|---|---|
| `hero-banner.png` | ホーム ヒーロー背景（昼景） |
| `hero-night.png` | 予備／夜景バリエーション |
| `hero-logo.png` | ロゴ／ヒーロー装飾（サイズ大、必要に応じ最適化推奨） |
| `hotel-exterior.jpg` / `hotel-lounge.jpg` / `hotel-room.jpg` / `hotel-wine.jpg` | 宿泊情報カード用 |
| `illust-bus.png` | 移動ページ 東京組カードの装飾 |
| `illust-deer.png` / `illust-lake.png` / `illust-mountain.png` / `illust-onsen.png` / `illust-tree.png` | 各セクションの手描き風装飾 |
| `meetup-hotel-graphy.png` | **NEW** — HOTEL GRAPHY 渋谷 集合場所のストリートビュー画像（89の柱＋赤枠付き） |

**画像最適化**：`hero-logo.png`（約2.1MB）はモバイル配信前提で WebP化 or リサイズ推奨。

**フォント**：Google Fonts CDN からロード（`<link rel="preconnect">` 済み）。オフライン運用があるならセルフホストへ切替。

**アイコン**：SVG（インライン）のみ使用。外部アイコンフォントは不使用。

---

## Content / Copy に関する注意

- 日本語コンテンツで、**時刻表記は原則 `H:MM` (24h)**。カード表示は前ゼロ付き `HH:MM`、詳細タイムラインも同じ。
- 東京組と地方組の分岐は **随所で対称に扱う**（片方だけ更新しない）。
- LINE 案内、電話番号、Google Maps リンクなど外部リンクは `target="_blank" rel="noopener"` を維持。

---

## Files

このバンドルに含まれるファイル：

```
design_handoff_gathering_shiori_2026/
├── README.md                       ← このドキュメント
├── index.html                      ← デザインリファレンス本体（単一HTML）
└── assets/                         ← 画像アセット一式（上記表参照）
```

`index.html` は
- `<style>` に全CSS
- `<body>` にホーム＋7サブページ（`.page[data-page]`）
- `<script>` に `showPage()`, `renderSchedule()`, accordion / tab 制御, IntersectionObserver, `day1[]`/`day2[]` データ
がすべて含まれる single-file プロトタイプです。

コンポーネント分割の目安：

- `Hero`
- `PageShell`（`.subpage-bar` + 戻るボタン）
- `ScheduleTimeline`（`day1`, `day2` を受け取る）
- `ActivityCard`（DAY1／DAY2共通、`.ac-sublist`, `.ac-tags` 対応）
- `ReuniteCard`（DAY2 13:50 集合の分岐）
- `TransportCard`（東京組／地方組の DAY1/DAY2 タイムライン＋`MeetupCard`, `TransportReunite`）
- `MeetupCard`（`.tc-meetup`）
- `PrepAccordion` / `LunchTabs` / `PeopleTabs`
- `InfoAccordion`
- `VideoGiftForm`

---

## Deployment 向け覚え書き

- 静的ページなので **Vercel／Netlify／Cloudflare Pages** どこでもOK。
- 参加者への配布は URL 一本＋LINEで拡散予定。
- 認証は不要（社内共有だが URL 知る者のみアクセス）。
- 直リンクで各サブページに飛べるよう **ハッシュ URL（#schedule 等）** を必ず維持してください。

---

以上。実装中に不明点があれば `index.html` の該当セクションを grep して参照してください。CSSクラス名で検索すれば該当マークアップにたどり着けます。
