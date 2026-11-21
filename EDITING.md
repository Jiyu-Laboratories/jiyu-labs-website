# ウェブサイト編集ガイド（jiyu-labs.com）

このサイトは **GitHub 上のファイルを編集するだけ** で更新できます。
ターミナルやプログラムのインストールは不要です。ブラウザだけで完結します。

> 💡 変更を保存（Commit）すると、**約1〜2分後** に https://jiyu-labs.com に自動で反映されます。

---

## 1. どのファイルを編集すればいい？

| 変更したい内容 | 編集するファイル |
|---|---|
| ヘッダーの会社名・キャッチコピー・検索結果の説明文 | `_config.yml` |
| Services（見出し・説明文） | `_sections/01-services.md` |
| Services の各カード（3つのサービス） | `_services/` フォルダ内の各ファイル |
| Story | `_sections/02-story.md` |
| About（Mission / Vision） | `_sections/03-about.md` |
| Achievements（受賞・講演・メディア掲載） | `_sections/04-achievements.md` |
| Company（所在地・代表者） | `_sections/05-company.md` |
| Security Policy | `_sections/06-security-policy.md` |
| Contact（お問い合わせフォームのURL） | `_sections/07-contact.md` |
| 画像 | `assets/images/` フォルダ |

⚠️ `_layouts`、`_includes`、`assets/css` フォルダはデザインの仕組みです。通常は触らないでください。

---

## 2. 文章を編集する手順

1. GitHub でリポジトリを開く：https://github.com/Jiyu-Laboratories/jiyu-labs-website
2. 編集したいファイルをクリックして開く（例：`_sections` → `02-story.md`）
3. 右上の **鉛筆アイコン ✏️（Edit this file）** をクリック
4. 文章を編集する
5. 右上の緑色の **「Commit changes...」** ボタンをクリック
6. 「Commit message」に変更内容を簡単に書く（例：「Storyの誤字を修正」）
7. **「Commit changes」** をクリックして保存

✅ 1〜2分後にサイトに反映されます。反映されない場合は、ブラウザを再読み込み（Ctrl+Shift+R / Mac は Cmd+Shift+R）してください。

### ファイルの構成（上部の「---」で囲まれた部分）

各ファイルの一番上にある `---` と `---` で囲まれた部分は **設定（見出しなど）** です。

```yaml
---
order: 2                 # 表示順（小さい数字が上）
anchor: story            # ページ内リンク用のID（変更しないでください）
nav: Story               # ヘッダーメニューに表示する名前
label: 原体験と軌跡        # タイトル上の小さな日本語
title: Story             # 大きなタイトル
subtitle: |              # タイトル下の説明文（「|」の下は改行がそのまま反映）
  自分自身が、研究をしていて、
  大変だったことを解決するべく起業しました
background: gray         # 背景色：white（白）または gray（グレー）
---
```

**注意点**
- `title:` のように、**コロン「:」の後には半角スペース** が必要です。
- `|` を使った行の下は、**半角スペース2つで字下げ** してください。
- `#` から後ろはメモ（コメント）なので、サイトには表示されません。

`---` の下が **本文** です。普通に文章を書けば、そのまま表示されます。

---

## 3. 本文の書き方（Markdown の基本）

| 書き方 | 表示 |
|---|---|
| `## 見出し` | 大きめの見出し |
| `### 小見出し` | 小さめの見出し |
| `**太字**` | **太字** |
| `- 項目` | 「・」付きの箇条書き |
| `<https://example.com>` | クリックできるリンク（URLそのまま表示） |
| `[リンク文字](https://example.com)` | 文字にリンクを付ける |
| 空行（何もない行） | 段落の区切り |
| 改行 | そのまま改行として表示 |

---

## 4. よくある作業

### Achievements に新しい実績を追加する

`_sections/04-achievements.md` を開き、該当する見出し（`## 受賞・採択`、`## 講演など`、`## メディア掲載`）の下に、`- ` で始まる行を追加します。

```markdown
## 講演など

- ○○大学の授業「△△」にて講演, 2026-12.
- 東京科学大学（旧・東京工業大学）の授業「技術経営IV」にて講演, 2025-01.
```

URL を付ける場合は `<` と `>` で囲みます：`<https://example.com/news>`

### Services のカードを編集・追加・削除する

- **編集**：`_services/` フォルダ内のファイルを開いて編集します。
  - `title`：サービス名
  - `target`：想定顧客（「想定顧客：」は自動で付きます）
  - `image`：画像のパス（例：`/assets/images/service-analysis.webp`）
  - `button_text`：ボタンの文字（2行で書けます）
  - `button_url`：ボタンのリンク先
- **追加**：既存のファイルを開き、内容をコピー → `_services` フォルダで **「Add file」→「Create new file」** → ファイル名を `04-new-service.md` のようにして貼り付け、内容を書き換えます。
- **並び順**：`order:` の数字を変更します（小さい数字が左）。
- **一時的に非表示**：設定に `hidden: true` を追加します。
- **削除**：ファイルを開き、右上の「…」メニュー →「Delete file」。

### 画像を差し替える・追加する

1. `assets/images` フォルダを開く
2. **「Add file」→「Upload files」** をクリック
3. 画像をドラッグ＆ドロップして **「Commit changes」**
4. 使いたいファイルの `image:` を新しい画像のパスに変更する
   例：`image: /assets/images/new-photo.jpg`

💡 画像は横長（3:2 程度）、幅 1000〜1600px、1MB 以下がおすすめです。ファイル名は **半角英数字とハイフン** にしてください（日本語・スペースは避ける）。

### お問い合わせフォームの URL を設定する

`_sections/07-contact.md` の `form_url:` に Google フォームの URL を貼り付けます。

```yaml
form_url: "https://docs.google.com/forms/d/e/xxxxxxxx/viewform"
embed_form: false   # true にするとページ内にフォームを埋め込み表示
```

### セクションを一時的に非表示にする

該当ファイルの設定部分に `hidden: true` を追加します。元に戻すときは行を削除します。

---

## 5. 反映を確認する・困ったとき

- **反映状況の確認**：リポジトリ上部の **「Actions」** タブを開くと、更新の処理状況が見られます。
  - 🟡 黄色：処理中（1〜2分待つ）
  - ✅ 緑：完了（サイトに反映済み）
  - ❌ 赤：エラー（設定部分の書き方が間違っている可能性があります。「:」の後のスペースや、字下げを確認してください）
- **元に戻したいとき**：ファイルを開き、右上の **「History」** から過去の内容を確認できます。直前の内容をコピーして貼り直し、Commit すれば元に戻せます。
- わからない場合は、Cristian に連絡してください。
