# Compass

**知識をもとに、プロジェクトの方向を決め、仕事を進める。**

Project_Knowledgeの業務・共有機能と、libraryの原資料・知識・方針を統合するプロジェクトです。
「図書館」はCompass内の知識機能の名称として残します。

## 入口

- [次のCodexへの指示書](docs/handoff/next-agent.md) / [これまでの経緯](docs/handoff/history.md)
- [ドキュメント目次](docs/index.md)
- [要件定義](docs/requirements/overview.md) / [受入条件](docs/requirements/acceptance.md)
- [構造設計](docs/architecture/structure.md) / [データと権限](docs/architecture/data-and-access.md)
- [開発手順](docs/development/setup.md)
- [開発段階](docs/planning/roadmap.md) / [未決事項](docs/planning/open-questions.md)
- [移行計画](docs/migration/plan.md) / [運用手順](docs/operations/runbook.md)

## 現在の状態

作成済みなのはDjango初期プロジェクト、開発設定、設計文書、MkDocsによるdocs閲覧環境です。
予算・施策・タスク・共有・AI等の業務機能は今後実装します。
既存のProject_Knowledgeとlibraryの実データは元の場所で管理を継続します。

正式名はCompass、フォルダは `D:/projects/Compass`、Pythonプロジェクト名は `compass` です。

## ローカルで始める

プロジェクト直下で実行します。既存のPython 3.12環境とuvを使用します。

```powershell
uv sync --group docs
uv run python manage.py check
uv run --group docs mkdocs serve --dev-addr 127.0.0.1:8001
```

docsは http://127.0.0.1:8001/ で確認できます。停止はCtrl+Cです。
Djangoの初期画面を確認するときは別ターミナルで実行します。

```powershell
uv run python manage.py runserver 127.0.0.1:8000
```

adminを使う場合の初期DB作成・管理者登録は[開発手順](docs/development/setup.md)を参照してください。
.env.exampleは設定例です。.envを置くだけでは自動読込されません。

## 構成

```text
Compass/
├── compass/          # Django設定・URL・起動
├── apps/             # これから追加する業務機能
├── docs/             # 要件・設計・開発・移行・運用
├── templates/        # Web画面
├── static/           # Web静的資産
├── tests/            # 検証方針と今後の試験
├── tools/            # 開発・移行の補助処理を追加する場所
├── deploy/           # 将来の配置・運用設定
├── manage.py
├── mkdocs.yml
├── pyproject.toml
└── uv.lock
```

開発中のアプリはSQLiteを使用します。共同利用のPostgreSQL構成は設計段階です。
利用者の原資料・添付・共有DBはコードリポジトリの外で保存する設計です。

## 確認コマンド

```powershell
uv run python manage.py check
uv run --group docs mkdocs build --strict
```

ビルド結果のsite/、ローカルDB、.venv/、.idea/はGit管理対象外です。
