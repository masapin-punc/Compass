# 静的ファイル

Compass 共通の CSS・JavaScript・ロゴ等を置きます。機能固有の静的ファイルは、実装時に各 Django アプリの `static/<app_name>/` へ配置できます。

`collectstatic` の出力先はルートの `staticfiles/` です。生成物は Git 管理しません。

利用者の原資料・添付資料・実データは静的配信の対象ではありません。認可された利用者のみが取得できる保存・配信方式を別途実装します。
