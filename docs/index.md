# Compass

知識・判断根拠と仕事を結び付け、プロジェクトを進めるための統合サービスです。
既存のProject_Knowledgeと図書館を出発点にしています。

## 最初に読む

| 確認したいこと | ページ |
|---|---|
| 別のCodexセッションで作業を再開する | [指示書](handoff/next-agent.md) / [経緯説明](handoff/history.md) |
| 何を作るか | [要件定義](requirements/overview.md) |
| できたと判断する条件 | [受入条件](requirements/acceptance.md) |
| コードとフォルダの役割 | [構造設計](architecture/structure.md) |
| データの正本と共有範囲 | [データと権限](architecture/data-and-access.md) |
| すぐに開発を始める | [開発環境](development/setup.md) |
| 何から実装するか | [開発段階](planning/roadmap.md) |
| 旧環境から引き継ぐ | [移行計画](migration/plan.md) |

## 現在地

- 採用済み: プロジェクト名Compass。図書館を知識機能として扱う統合構想。
- 整備済み: 既存Djangoプロジェクト、開発設定、docs環境、要件・設計・移行・運用文書。
- 今後の実装: 業務画面・モデル、共有認証、権限、PostgreSQL、資料取込、AI。
- 未決: 利用規模、オフライン要件、共有AIの利用条件、本番配置先。

設計文書の「初期機能」は実装予定の範囲を表します。動作済みの機能一覧ではありません。

## 更新の約束

Compassの要件・設計の正本はこのdocsです。library側P002には初期提案を残し、ここへの案内を置きます。
事業資料の原本・既存のタスク状態は、移行が完了するまで旧環境が正本です。

文書を追加したらmkdocs.ymlのナビゲーションと関連リンクを更新し、厳格ビルドを実行します。
変更理由は[意思決定テンプレート](decisions/template.md)を使い記録します。
