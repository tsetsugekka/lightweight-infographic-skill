# 軽量インフォグラフィック

製品やワークフローの仕組みを、GitHub README、プレゼン資料、入門ガイドに使える分かりやすい図にします。

![Codex Skill](https://img.shields.io/badge/Codex-Skill-18202A)
![出力形式](https://img.shields.io/badge/Output-PNG%20%2F%20SVG-5086B1)

[English](README.md) | [简体中文](README.zh-CN.md) | **日本語**

## この Skill について

短い説明、意味を伝える小さなイラスト、淡い配色、明確な接続線で「どう動くのか」を伝える、再利用可能な Codex Skill です。

次の用途に適しています。

- **GitHub リポジトリ：**入力、主要な処理、出力を示す、読みやすい仕組みの説明図。
- **PPT プレゼン：**1 枚のスライドで伝える簡単な構成図、モジュール間の関係、製品の処理フロー。
- **製品ドキュメント：**導入手順、機能紹介、クイックスタートの図解。

デザインの方向性を保ちながら、配置、アイコン、ステップ数、接続関係を内容に合わせます。詳細な技術仕様書や固定のポスターテンプレートではありません。

## 作例ギャラリー

2 つの実際のプロジェクトを通じて、軽量なデザインを異なる内容に応用する例を紹介します。画像をクリックすると原図を表示できます。

### SignalScout TV · 製品の処理フロー

配信ソースの収集、チャンネルの整理、ブラウザーでの確認、再生までを、小さな画面イラストで具体的に伝えます。原図は中国語です。

[![SignalScout TV の仕組み：配信ソースの収集、チャンネル整理、ブラウザーでの確認、再生](https://raw.githubusercontent.com/tsetsugekka/signalscout-tv/main/public/architecture.png)](https://github.com/tsetsugekka/signalscout-tv/blob/main/public/architecture.png)

[SignalScout TV のリポジトリを見る →](https://github.com/tsetsugekka/signalscout-tv)

### Codex Market Skills · 調査フロー

質問からスキルの選択、根拠の確認を経て調査結果をまとめます。補助的な分析手法を主な流れの下に配置し、全体を読み取りやすくしています。

[![Codex Market Skills の仕組み：質問、スキルの選択、根拠の確認、結果の出力](https://raw.githubusercontent.com/tsetsugekka/codex-market-skills/main/assets/how-it-works.ja.svg)](https://github.com/tsetsugekka/codex-market-skills/blob/main/assets/how-it-works.ja.svg)

[Codex Market Skills のリポジトリを見る →](https://github.com/tsetsugekka/codex-market-skills)

これらの既存作例が、本 Skill のデザインの基になっています。新しい図では、構成、イラスト、説明文を実際の内容に合わせて調整します。

## Skill

| ファイル | 役割 |
|---|---|
| [`lightweight-infographic`](skills/lightweight-infographic/SKILL.md) | 内容の整理、作図、書き出し、確認 |
| [`agents/openai.yaml`](skills/lightweight-infographic/agents/openai.yaml) | Codex の表示情報と呼び出し用プロンプト |

Skill 本文は中国語です。図の言語はユーザーの指定に従います。3 言語の README は紹介文の翻訳であり、別々の Skill ではありません。

## プロンプト例

```text
$lightweight-infographic を使って、このリポジトリの仕組みを図解してください。
README と関連コードを確認し、主要な流れを分かりやすくまとめ、
README に掲載できる PNG と編集可能な SVG を作成してください。
```

```text
$lightweight-infographic を使って、このシステムの説明を 16:9 の PPT 用に
簡単な構成図にしてください。ユーザー、サービス、データストアの関係を示し、
スライドに挿入できる画像を納品してください。
```

```text
$lightweight-infographic を使って、この導入フローの日本語・英語・中国語版を
作成してください。言語ごとに改行を調整し、指定 URL の QR コードを追加して、
書き出した画像から読み取れることを確認してください。
```

## 特徴

- 内容に合う構成を選択。順序のある処理は通常 3〜5 ステップ、構成図は必要に応じて階層や分岐を使用。
- 小さな画面図やイラストで動作を説明し、控えめな色と文字の階層で読みやすく整理。
- 事実と矢印は実際の資料に基づき、参考画像は見た目の参考として使用。
- 表示用の PNG と、必要に応じて実際に編集できる SVG を出力。ネイティブに編集できる PPTX には対応するプレゼン作成ツールが必要。
- QR コードは必要な場合に実 URL から生成し、最終出力の読み取りを確認してから検証済みと報告。
- 可読性、はみ出し、接続線、多言語の配置、要求された編集可能性を描画結果で確認。

## 推奨構成

```text
README.md
README.zh-CN.md
README.ja.md
skills/
  lightweight-infographic/
    SKILL.md
    agents/openai.yaml
```

インストールするファイルは実行指針と表示用メタデータのみです。API キーや特定の描画サービスを前提とせず、実際の出力形式は利用可能なツールによって決まります。

## インストールと使い方

Codex のグローバル Skill ディレクトリへコピーします。同名の Skill がある場合は、内容を比較してから置き換えてください。

```sh
git clone https://github.com/tsetsugekka/lightweight-infographic-skill.git
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
cp -R lightweight-infographic-skill/skills/lightweight-infographic "${CODEX_HOME:-$HOME/.codex}/skills/"
```

新しい Codex タスクを開始して、インストールした Skill を検出させます。`$lightweight-infographic` と説明したい内容を入力し、必要ならサイズ、言語、形式を指定してください。ネイティブに編集できる PPTX が必要な場合は明示し、プレゼン作成ツールのある環境を使ってください。

## 安全上のルール

公開は許可された内容に限定し、認証情報、非公開パス、個人メタデータを出力に含めません。作図の依頼だけで、リポジトリの公開、文書の差し替え、既存画像の削除が許可されたことにはなりません。

## 制約

単体の描画ソフトではなく、エージェント向けの指示パッケージです。製品の動作確認を代替せず、未検証の QR コードや、画像を貼り付けただけの編集可能スライドを完成扱いにしません。実施できなかった確認は具体的に報告します。
