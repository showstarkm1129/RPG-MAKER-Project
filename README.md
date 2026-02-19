# RPG Maker MZ Projects

RPG Maker MZ (RMMZ) プロジェクトの Git リポジトリです。

## リポジトリ構成

```
RMMZ/
    .gitignore          ← 全プロジェクト共通の除外設定
    README.md           ← このファイル
    Test/               ← プロジェクト1
    Game2/              ← プロジェクト2（将来追加）
    ...
```

## 追跡ファイル（Git で管理するもの）

各プロジェクトフォルダ内の以下のファイルのみを追跡しています：

| パス | 内容 |
|---|---|
| `data/*.json` | ゲームデータ（マップ・アクター・アイテム・スキル等） |
| `js/plugins/*.js` | カスタムプラグイン |
| `js/plugins.js` | プラグイン設定ファイル |
| `index.html` | ゲームエントリポイント |
| `package.json` | プロジェクト設定（タイトル・画面サイズ等） |
| `game.rmmzproject` | RPGMaker プロジェクトファイル |
| `css/game.css` | スタイルシート |
| `icon/icon.png` | アプリアイコン |

## 除外ファイル（Git で管理しないもの）

以下の大容量バイナリファイルは除外しています：

| パス | 理由 |
|---|---|
| `audio/` | OGG音声ファイル（BGM/BGS/ME/SE） |
| `img/` | PNG画像（スプライト・タイルセット・キャラクター等） |
| `effects/` | Effekseerエフェクトファイル |
| `fonts/` | WOFFフォントファイル |
| `movies/` | 動画ファイル |
| `js/libs/` | 外部ライブラリ（Pixi.js・Effekseer等） |
| `js/rmmz_*.js` | RMMZエンジンコアファイル |
| `js/main.js` | RMMZエントリポイント |

## 別PCにクローンした後の復元手順

このリポジトリをクローンしても、除外されたファイルは含まれません。
以下の手順でゲームを動作可能な状態に復元してください：

1. **RPG Maker MZ をインストール**（プロジェクトと同じバージョン）
2. **エンジンファイルをコピー**（RMMZ インストール先から）：
   - `js/rmmz_core.js`
   - `js/rmmz_managers.js`
   - `js/rmmz_objects.js`
   - `js/rmmz_scenes.js`
   - `js/rmmz_sprites.js`
   - `js/rmmz_windows.js`
   - `js/main.js`
   - `js/libs/` フォルダ全体
   - `fonts/` フォルダ全体
3. **素材ファイルをコピー**（別途管理しているバックアップから）：
   - `audio/` フォルダ全体
   - `img/` フォルダ全体
   - `effects/` フォルダ全体

## RMMZ バージョン情報

| プロジェクト | RMMZバージョン |
|---|---|
| Test | 1.10.0 |

## 日常の Git ワークフロー

```bash
# 変更内容を確認
git status

# データファイルをステージング
git add Test/data/

# コミット
git commit -m "マップ001: ダンジョンを追加"

# GitHub にプッシュ
git push
```

## 新規プロジェクト追加時

RMMZ で新プロジェクトをこのフォルダ内に作成すれば、`.gitignore` のワイルドカードパターン (`*/audio/` 等) が**自動的に**適用されます。追加設定は不要です。

```bash
git add NewProject/
git commit -m "NewProject: 新プロジェクト追加"
git push
```
