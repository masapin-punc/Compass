---
status: reference
updated: 2026-09-29
as_of: 2026-09-29
---
# 参照資料一覧

Compassの要件・構造設計は、本人の依頼、libraryのP002設計、Project_Knowledgeの既存構想を基に整理した。
このページは、ドキュメントサイトに含まれないローカル資料の所在を示す。
パスは2026-09-29時点の配置であり、Webサイトから参照できるリンクではない。PyCharm等で開いて確認する。
事業原資料・実データ・秘密設定を文書サイトへ同梱しない。

## 本人の依頼と採用

| 時点 | 本人が示したこと | 設計上の扱い |
|---|---|---|
| 2026-09-29 図書館整備 | 複数プロジェクトの知識・方針・メイン/サブタスクをMDとAGENTS.mdで整理 | 出典と原資料を保ち、PyCharmで扱える構造を継承 |
| 2026-09-29 統合依頼 | 予算・施策・タスク・スケジュール・資料・メンバー共有をAIで補助。管理しやすい方式を検討 | [要件定義](../requirements/overview.md)の目的と6管理領域 |
| 2026-09-29 Compass採用・整備依頼 | Compassを作成・アタッチし、既存案・必要ファイル・docs環境を整理 | 名称Compassと既存Djangoプロジェクトへの文書・開発基盤集約は採用済み |

過去の名称案「羅針盤 / Project Compass」「共創室 / Project Atelier」「地図帳 / Project Atlas」は検討履歴。
今後の正式な表記は **Compass**、知識機能の名称は **図書館** とする。
商標・ドメイン・外部パッケージ名の取得可能性を確認したことは意味しない。

## 設計と運用文書

| ID | 資料 | 参照用の実パス | 主な用途 |
|---|---|---|---|
| R01 | 図書館P002の設計一式 | `D:/projects/library/projects/P002_知識・プロジェクト管理統合/` | 旧調査、要件、構造・移行、名称案、本人方針との区別 |
| R02 | Project_Knowledge README | `D:/projects/Project_Knowledge/README.md` | 既存機能・構成・版・次フェーズ |
| R03 | 原構想 | `D:/projects/Project_Knowledge/doc/Project_Knowledge_OS_構想.md` | 雑に書く、整理を強制しない、原文を残す、仕事と情報の関連 |
| R04 | 初期設計 | `D:/projects/Project_Knowledge/doc/Phase1_実装と今後の設計.md` | 既存保存・文書整理・拡張方針 |
| R05 | 予算管理 | `D:/projects/Project_Knowledge/doc/budget-guide.md` | 月次予算・実績、差額、Excel出典 |
| R06 | 共有導入 | `D:/projects/Project_Knowledge/doc/sharing-start-guide.md` | 現行の共有サーバー・社員認証・運用 |
| R07 | グループ共有 | `D:/projects/Project_Knowledge/doc/group-sharing-guide.md` | グループ、個別許可、除外の扱い |
| R08 | 図書館初回取込記録 | `D:/projects/library/catalog/20260929_初回取込記録.md` | 原資料の件数・ハッシュ、不足画像・文字化け |
| R09 | 図書館の運用・資料台帳 | `D:/projects/library/README.md`、`D:/projects/library/catalog/資料台帳.md` | 現行MDの状態定義、資料分類、出典 |

R01の移植元は `knowledge/00_現状調査.md`、`knowledge/01_要件定義.md`、`knowledge/02_構造・移行設計.md`、`knowledge/03_名称案.md`、`方針.md`。
元資料を保管し、Compass側で名称・ディレクトリ・現在の段階を整理した。
元設計を採用済み実装として読み替えず、今後の要件・設計の更新先はCompassのdocsへ集約する。

## 旧調査が参照したコード

| ID | 実パス | 主な確認対象 |
|---|---|---|
| R10 | `D:/projects/Project_Knowledge/knowledge_os/server.py` | ローカルHTTPアプリと共有AIの通常利用停止 |
| R11 | `D:/projects/Project_Knowledge/knowledge_os/share_server.py` | 共有サーバーとOrigin付きPOSTの拒否 |
| R12 | `D:/projects/Project_Knowledge/knowledge_os/remote.py` | ローカルからの共有クライアント |
| R13 | `D:/projects/Project_Knowledge/knowledge_os/storage.py` | 容量制限、文書保存、競合検出 |
| R14 | `D:/projects/Project_Knowledge/knowledge_os/budget.py` | 予算項目、10進数、集計・差額、Excel取込 |
| R15 | `D:/projects/Project_Knowledge/knowledge_os/sharing.py` | 社員認証、セッション、共有操作 |

この参照表は移植した調査の根拠を追跡するもの。今回のdocs整備で旧コードを試験実行した結果ではない。
再利用前には現行コードと試験を再確認し、既存の権限・予算規則を回帰検証する。

## Compassへの対応

| 元の設計 | Compassで更新する文書 |
|---|---|
| 現状調査 | [既存環境と調査の根拠](current-state.md) |
| 要件定義 | [要件定義](../requirements/overview.md)、[受入条件](../requirements/acceptance.md) |
| 構造・移行設計 | [構造設計](../architecture/structure.md)、[データ・権限](../architecture/data-and-access.md)、[移行計画](../migration/plan.md) |
| 名称案・方針 | [名称の決定](../decisions/0001-name.md)、[Web構成の判断](../decisions/0002-web-architecture.md)、[未決事項](../planning/open-questions.md) |
