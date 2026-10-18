# 開発環境と確認手順

## 前提

- 開発ルート: D:/projects/Compass
- Python: 3.12以上。現在のPyCharm SDKはCompass/.venvのPython 3.12.10。
- 依存管理: uv、pyproject.toml、uv.lock。
- 設定モジュール: compass.settings。生成済みのmanage.py/ASGI/WSGIを使う。
- Djangoは作成時の依存指定を継承する。正確な解決版はuv.lockを参照する。
- docs: MkDocs Material。アプリ依存とはdocsグループで区別する。

## 初回セットアップ

```powershell
Set-Location D:/projects/Compass
uv sync --group docs
uv run python manage.py check
```

PyCharmでは既存のCompassモジュールを使い、SDKがCompass/.venvを指すことを確認します。
すでにlibraryとProject_Knowledgeをアタッチしていても、それぞれの仮想環境を混用しません。

## docsのプレビュー

```powershell
uv run --group docs mkdocs serve --dev-addr 127.0.0.1:8001
```

http://127.0.0.1:8001/ を開きます。MDの保存で再読込されます。
Djangoの開発用8000番と分けているため、同時起動できます。停止はCtrl+C。

静的HTMLを生成するとき:

```powershell
uv run --group docs mkdocs build --strict
```

生成先はsite/です。原稿はdocs/にあり、site/を直接編集しません。
docsはローカル閲覧用であり、自動公開・外部配信は設定していません。

## Djangoの確認

```powershell
uv run python manage.py check
uv run python manage.py runserver 127.0.0.1:8000
```

現在は初期プロジェクトです。業務機能はまだありません。
adminを利用する場合だけローカルDBを作成し、管理者を登録します。

```powershell
uv run python manage.py migrate
uv run python manage.py createsuperuser
```

この作業では共有DBや既存アプリのDBを変更しません。初回整備時点では業務データを取り込んでいません。

## 環境変数

.env.exampleは設定項目の見本で、自動読み込みは行いません。
PyCharmのRun Configurationの環境変数、またはPowerShellで設定します。

```powershell
$env:DJANGO_DEBUG = "true"
$env:DJANGO_ALLOWED_HOSTS = "localhost,127.0.0.1"
uv run python manage.py check
```

DEBUG=Trueでは開発専用の既定キーでローカル起動できます。
DEBUG=Falseで動かす際は独自のDJANGO_SECRET_KEYが必要です。
これは本番配置を完成させる手順ではありません。HTTPS・DB・共有認証等は[運用手順](../operations/runbook.md)を参照します。

## データの扱い

SQLiteはローカル開発用です。共同管理のPostgreSQL接続・移行は今後実装します。
利用者の原資料、予算、添付、認証情報をテストfixtureやGitへそのままコピーしません。
検証データは合成データか、利用を許可した範囲のコピーを使います。

## 変更ごとの確認

- Python変更: manage.py checkと変更した振る舞いの検証。
- docs変更: mkdocs build --strict。
- 認証・権限変更: 未許可・除外・文書単独共有・履歴・AI・出力を含めて確認。
- 予算変更: 未入力/ゼロ、10進数、版、配賦、二重計上を確認。
- 移行変更: 原本ハッシュ、ID、履歴、権限、再実行、復旧を確認。

単なる見出し・案内文の変更だけのために新しいテストを増やす必要はありません。
