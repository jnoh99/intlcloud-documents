本書では、CDNによってCOSを加速する全体的な操作フローと具体的な操作方法について、詳しく説明します。

## 前提条件
1. Tencent Cloudアカウントの登録と実名認証が完了していること。
2.COSバケットが作成されていること。詳細については、[バケットの作成](https://intl.cloud.tencent.com/document/product/436/13309)を参照してください。

## 操作ガイド
## ドメイン名の追加
[CDNコンソール](https://console.cloud.tencent.com/cdn)にログインし、左側ナビゲーションバーで【ドメイン名管理】をクリックすると､ドメイン名管理ぺージが表示されます｡【ドメイン名の追加】をクリックします。
 ![](https://main.qcloudimg.com/raw/d301ff1eea5fe534ce09ec5964e8c82b.png)

### COSをオリジンサーバーとして選択する
![](https://main.qcloudimg.com/raw/ec7ea324171295b8fd0321e226d0e0a3.png)
1. 加速する**ドメイン名**を入力します。
汎用ドメイン名へのアクセスをサポートします。たとえば、*.test.comです。ドメイン名の一括アクセスをサポートします。最大10個のドメイン名を追加できます。
ドメイン名は次の条件を満たす必要があります。
 - ドメイン名はすでに中国工業情報化部に登録されていること
 - ドメイン名はTencent Cloud CDNにアクセスされたことがないこと
2. ドメイン名の**所属プロジェクト**を選択します。
このプロジェクトは、Tencent Cloudのすべての製品で共有されているため、[プロジェクトの管理](https://console.cloud.tencent.com/project) でプロジェクトを追加できます。
3.**ドメイン名の構成**の**オリジンサーバーのタイプ**でCloud Object Storage(COS）を選択します。
4.対応する**バケット**のドメイン名を選択します。
5. **プライベートバケットへのアクセス**を有効にするには、先にCDNサービスを許可する必要があります。許可した後、手動で有効にすることができます。

>
> - CDNからCOSオリジンのドメイン名にアクセスする場合、そのバージョンはすでに全面的にCOSV5に切り替えられています。COSV4のbucketをオリジンサーバーとして追加する場合は、COSV4コンソールで、該当bucketの加速サービスを有効化する必要があります。
> - お持ちのCOSV5 bucketがプライベートである場合、CDNサービスに対応するCOS bucketへのアクセスを許可してから、back to originアクセスを有効化する必要があります。この場合、プライベートbucket中のリソースはすべてCDNパブリックネットワークを介して割り当てることができ、セキュリティリスクが高いため、慎重に操作してください。

### 加速サービスの構成
ユーザーのサービスニーズに応じて**サービスのタイプ**、**基本構成**、**キャッシュ期限切れの構成**を選択します。
![](https://main.qcloudimg.com/raw/6264633c18801547e4aece61a94009cb.png)
1. **サービスのタイプ**
   サービスタイプの選択は、ドメイン名がスケジューリングするリソースプラットフォームを決めています。異なるリソースプラットフォームの加速の構成も異なりますので、ユーザーのサービスに適したサービスタイプを選択してください。
   - 静的加速：Eコマース、ウェブサイト、ゲーム画像など静的リソースの加速に適しています。
   - ダウンロードの加速：ゲームのインストールパッケージ、音声・動画リソースファイルのダウンロード、携帯電話ファームウェアの配布などに適しています。
   - ストリーミングメディアのオン・デマンド加速：音声・動画のオン・デマンド加速などに適しています。

2. **基本構成**
CDNによるフィルタリングパラメータスイッチを利用することで、サービスニーズに応じて、ユーザーリクエストURLの中の**「?」**に続くパラメータをフィルタリングするかどうかを制御できます。フィルタリングパラメータを利用することで、バージョンを柔軟に制御したり、リソースのToken付き認証を行ったりすることができます。詳細については、[フィルタリングパラメータの構成](https://intl.cloud.tencent.com/doc/product/228/6291)を参照してください。

3. **キャッシュ期限切れの構成**
キャッシュ期限切れの構成とは、CDN加速ノードがユーザーのサービスコンテンツをキャッシュする際に従う期限切れルールのセットです。詳細については、[キャッシュ期限切れの構成](https://intl.cloud.tencent.com/doc/product/228/6290)を参照してください。


### アクセス完了
**ドメイン名の追加**ページのすべての設定項目を入力してから、【サブミット】をクリックしてドメイン名の追加を完成します。ドメイン名の構成をネットワーク全体のノードに反映されるまで約5～10分かかるため、しばらくお待ちください。

### CNAMEの構成
ドメイン名が正常に追加された後、**ドメイン名の管理**ページで、CDNによってドメイン名にアサインされた加速CNAMEを確認できます。ユーザーは、ドメイン名にアクセスしているDNSプロバイダー（たとえば、Dnspod）で、このドメイン名にCNAME記録を1件追加する必要があります。**DNSの構成が有効になる後**、加速サービスを実行できます。詳細については、[CNAMEの構成](https://intl.cloud.tencent.com/doc/product/228/3121)を参照してください。
