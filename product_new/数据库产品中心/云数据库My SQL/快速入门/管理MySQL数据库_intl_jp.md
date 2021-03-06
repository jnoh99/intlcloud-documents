## インスタンス管理ページ
MySQLを初期化した後に、インスタンスリストでインスタンス名をクリックするか、或いは操作列で【管理】をクリックすると、インスタンス管理ページに入ります。このページではインスタンスの詳細確認、インスタンス監視、データベース管理等の操作行うことができます。

### インスタンス詳細
【インスタンス詳細】ページでは、データベースのさまざまな情報の確認及び操作を行うことができます。下図の通りです。<img src="https://main.qcloudimg.com/raw/071659c8118f8c9b94d4ab90cebbd955.png"  style="margin:0;">をクリックすると、インスタンスの基本情報を修正できます。その中に、パブリックネットワークはデフォルトでオフ状態であり、必要な場合は手動でオンにしてください。
![](https://main.qcloudimg.com/raw/be7a1916b3cba0932a015b95fa857d2d.png)

### インスタンス監視
【インスタンス監視】ページでは、現在のデータベースの各重要な稼動指標を監視することができます。アクセス、負荷、キャッシュ確認、テーブル、InnoDB、MyISAM 等の監視が含まれています。
詳しいインスタンス監視機能及びアラーム機能の説明は [監視機能](https://cloud.tencent.com/document/product/236/8455) 及び  [アラーム機能](https://cloud.tencent.com/document/product/236/8457)をご参照ください。

### データベース管理
#### データベースリスト
【データベース管理】>【データベースリスト】ページでは、SQLファイルを指定したデータベースにインポートすることができます。
1. 【データインポート】をクリックし、データインポートページに入ります。
2. 【ファイル追加】をクリックし、ローカルSQLファイルを選択し、アップロードすることを確認すればよいです。

#### パラメータ設定
【データベース管理】>【パラメータ設定】ページでは、データベースの修正可能なパラメータに対し設定を行ったり修正履歴を表示したりすることができます。【パラメータ稼動値】の隣の<img src="https://main.qcloudimg.com/raw/071659c8118f8c9b94d4ab90cebbd955.png"  style="margin:0;">をクリックすると、当該パラメータ値を修正できます。詳しい説明は [パラメータテンプレート概要](https://intl.cloud.tencent.com/document/product/236/8461)をご参照ください。

#### アカウント管理
【データベース管理】>【アカウント管理】ページでは、システムデフォルトの root アカウントを管理することができます。例えば、権限変更、パスワードリセット、アカウントの新規作成や削除等があります。

### セキュリティグループ
【セキュリティグループ】ページでは、データベースに対してセキュリティグループのコンフィギュレーションを行うことができます。詳細については、 [MySQLセキュリティグループ](https://cloud.tencent.com/document/product/236/9537)をご参照ください。

### バックアップリカバー
【バックアップリカバー】ページでは、 binlog のダウンロード及びコールドバックアップ操作を行うことができます。詳細については、[バックアップ方式](https://intl.cloud.tencent.com/document/product/236/7513)をご参照ください。

### 操作ログ
【操作ログ】ページでは、スローログ、エラーログ及びロールバックログの確認とダウンロードを行うことができます。

### 読取専用インスタンス
【読取専用インスタンス】ページでは、一つか複数の読取専用インスタンスを作成することにより、ユーザーのリード・ライト分離及び1マスター対複数スレーブのユースケースを対応し、ユーザーのデータベース読取負荷能力を大幅に向上させることができます。詳細については、[読取専用インスタンス](https://intl.cloud.tencent.com/document/product/236/7270)をご参照ください。

### 接続チェック
【接続チェック】ページでは、MySQLの存在する可能性のある接続・アクセス問題をチェックし、提供されたソリューションでアクセス問題を解決することにより、MySQLの正常的なアクセスを確保します。詳細については、[チェックツールのワンクリック接続](https://cloud.tencent.com/document/product/236/33206)をご参照ください。

## インスタンスリストページ
MySQL コンソールの左側ナビゲーションバーで【インスタンスリスト】ページを選択すると、インスタンスリストページでインスタンスの関連情報を確認し、インスタンスを管理することができます。
![](https://main.qcloudimg.com/raw/ad7eb840269b428dd044ddd45b08545e.png)

### コンフィギュレーションの調整
【インスタンスリスト】ページでは、データベースインスタンスに対しコンフィギュレーションの調整（スケールイン・スケールアウト）を行うことができます。インスタンスのアップグレード及びダウングレードがサポートされています。詳細については、 [データベースインスタンス仕様の調整](https://cloud.tencent.com/document/product/236/19707)をご参照ください。

### ロールバック
【インスタンスリスト】ページでは、ロールバックしようとするインスタンスを選択し、【より多くの操作】>【ロールバック】を選択し、コールドバックアップとbinlog によりデータベースを指定した時点にロールバックすることができます。詳細については、[データのロールバック](https://intl.cloud.tencent.com/document/product/236/7276)をご参照ください。

### リスタート
【インスタンスリスト】ページでは、リスタートしようとするデータベースインスタンスを選択し、【リスタート】をクリックし、インスタンスのリスタート操作を行います。一括リスタートが対応されています（複数のインスタンスを選択する）。
> - リスタートの間に、インスタンスは正常にアクセスできず、既存の接続が中断されますので、影響がないように事前に準備してください。
> - リスタートの間に、サービスの書き込み量が多い場合、ダーティページが多くなり、リスタートの失敗を引き起こすことがあります。スタートは失敗したら、インスタンスはリスタートした前の状態に戻り、引き続きアクセス可能となります。
> - リスタートの成功率を確保し、サービスに対する影響を抑えるために、サービスのアイドルタイムにリスタートすることを確保してください。
