このドキュメントではTencent Cloud CLBの入門使用方法を案内します。`clb-test`という名前の従来型のパブリックネットワークCLBインスタンスを作成し、クライアントからのリクエストを2台のバックエンドCVMに転送します。

## 前提条件
1. CLBはトラフィックの転送のみを行い、リクエストを処理する能力はありません。従って、ユーザーのリクエストを処理するCVMインスタンスが必要です。
この例においては、2台のCVMインスタンスさえあれば、自身でCVMの数を計画することができます。この例では既に広州地域に`rs-1`と`rs-2`が作成されています。CVMインスタンスの作成方法については、[CVMインスタンスの購入と起動](https://cloud.tencent.com/document/product/213/4855)を参照してください。
2. 本文ではHTTP転送を例として、CVMにおいて対応するWebサーバー（例：Apache、Nginx、IISなど）を配置する必要があります。
結果を検証するため、例では`rs-1`上にApacheを配置し「Hello Tomcat! This is rs-1!」を含むHTMLを返し、`rs-2`上でApacheを配置し「Hello Tomcat! This is rs-2!」を含むHTMLを返しました。CVM上でサービスを配置する方法の詳細については、[Linux（CentOS）におけるJava Webの配置](今後リリース予定)及び[WindowsにおけるPHPのインストールと構成](https://cloud.tencent.com/document/product/213/10182)を参照してください。
3. CVMのパブリックネットワークIP + パスにアクセスし、配置済みのページを表示することができる場合、サービスの配置が完了したことが証明されます。

>注：
> - 現在の帯域幅の属性がCLBではなくCVMにあるため、CVMでパブリックネットワーク帯域幅を購入する必要があります。
> - 例ではRSにより配置されるサービスの戻り値が異なりますが、実際の状況ではすべてのユーザーに一貫した体験を維持するため、RSは一般的に完全に同じなサービスを配置します。

## 従来型CLBインスタンスの購入
1. Tencent Cloudの[CLBサービス購入ページ](https://buy.cloud.tencent.com/lb)にログインします。
2. この例では、地域はCVMと同じ【広州】、インスタンスのタイプは【従来型】、ネットワーク属性は【パブリックネットワーク】、ネットワークは【Default-VPC（デフォルト）】を選択し、インスタンス名称は【clb-test】と記入します。
3. 【すぐに購入】ボタンをクリックすると、支払いが完了します。
CLBインスタンスの詳細内容については、[購入属性のガイド](今後リリース予定)を参照してください。
![](https://main.qcloudimg.com/raw/fbe58e6536dbd0b24d383f892dc6446d.png)
4. 【LBインスタンスリスト】ページで対応する地域を選択すると、新規作成したインスタンスが表示されます。
![](https://main.qcloudimg.com/raw/181110567fc16a3ad9a3547ef8e53dc1.png)

## CLBリスナーの作成
CLBリスナーはプロトコル及びポートを指定することにより実際の転送を行います。本文はCLBクライアントのHTTPリクエスト転送の構成を例とします。
1. [Tencent Cloudコンソール](https://console.cloud.tencent.com/)にログインし、【クラウド製品】-【ネットワーク】-【CLB】をクリックしてCLBコンソールに進みます。
2. 【LBインスタンスリスト】で作成済みの従来型CLBインスタンス`clb-test`を見つけ、インスタンスIDをクリックしてCLBの詳細ページに進みます。
3. 【基本部分】で、名前の後の小さいアイコンをクリックしてインスタンス名を変更することができます。
4. 【リスナー管理】の【リスナー】において、【新規作成】ボタンをクリックし、CLBリスナーを新規作成します。
![](https://main.qcloudimg.com/raw/f0e2d9431fd7eebfffd96e4392e3a70a.png)
5. ポップアップウィンドウにおいて以下の内容を構成します。
  - 名称は「Listener1」にカスタマイズします。
  - 監視プロトコルのポートは`HTTP：80`です。
  - バックエンドポートは`80`です。
  - 分散方式は`重み付きラウンドロビン`を選択します。
  - セッション保留をチェックしません。
  - 正常性検査を有効にします。
  - 【完了】ボタンをクリックしてCLBリスナーの作成を完了します。
![](https://main.qcloudimg.com/raw/84f8d4b675e1095d3efa193f3ded0281.png)

CLBリスナーの詳細内容については、[CLBリスナーの概要](https://cloud.tencent.com/document/product/214/6151)を参照してください。

## バックエンドCVMのバインディング
1. 【LBインスタンスリスト】で先ほど作成した`clb-test`を見つけ、IDをクリックしてCLBの詳細ページに進みます。
2. 【リスナー管理】の【CVMのバインディング】モジュールにおいて、【CVMのバインディング】ボタンをクリックします。
![](https://main.qcloudimg.com/raw/6fd77c5e62f56f73ada410d8fad8de09.png)
3. ポップアップウィンドウにおいてCLBと同じ地域にあるCVMインスタンス`rs-1`と`rs-2`を選択し、且つ重み付けをデフォルト値`10`に設定します。
4. 【確定】ボタンをクリックすると、バインディングが完了します。
![](https://main.qcloudimg.com/raw/014e181f64fcc1e22e6bd90f3ebe5bc6.png)
5. リスナー【Listener1】を展開すると、バックエンドCVMの正常性検査のステータスを確認することができます。ステータスが「正常」の場合、CVMはCLBが転送したリクエストを正常に処理できることを示します。
![](https://main.qcloudimg.com/raw/9f43f89b03bd0845749cb1c90413c97d.png)

## CLBサービスの検証
ブラウザにCLBのサービスアドレスとポートhttp://vip:80を入力して、CLBサービスのテストを行います。以下では今回のリクエストがCLBによりrs-1のCVMに転送され、CVMがリクエストを正常に処理し返すことを示します。
![](https://main.qcloudimg.com/raw/5df0db4039dfb4864af5db6b9c6cc3c1.png)

このリスナーのラウンドロビンアルゴリズムは「重み付きラウンドロビン」であり、2台のCVMの重み付けはいずれも10です。ブラウザをリフレッシュして再度リクエストを送信すると、今回のリクエストがCLBによりrs-2のCVMに転送されていることが分かります。
![](https://main.qcloudimg.com/raw/ac62269e1fa5373f65c76f9134d96589.png)

>注：
> - ユーザーがセッション保留機能をオフにし、ラウンドロビンモードを選択してスケジューリングを行った場合、リクエストは順次それぞれのRSに割り当てられます。
> - ユーザーがセッション保留機能をオンにし、またはセッション保留機能をオフにするがip_hashのスケジューリング方式を選択する場合、リクエストは引き続き同じRSに割り当てられます。

## ドメイン名の購入とCLBインスタンスへの解析（オプション）
1. [Tencent Cloudドメイン名登録ページ](https://dnspod.cloud.tencent.com)を開いてドメインの照合と登録を行います。この例はqcloudtest.comを例としており、詳細については、[ドメイン名の登録](https://cloud.tencent.com/document/product/242/9595)を参照してください。
2. [Tencent Cloudコンソール](https://console.cloud.tencent.com/)にログインし、【クラウド製品】-【ドメイン名とWebサイト】-【クラウド解析】をクリックします。
3. 購入した【ドメイン名】をクリックし、【ドメイン名分析管理】のページで【記録の追加】ボタンをクリックし、ドメイン名にA記録を追加し、以下の内容を入力します。
  - 記録タイプ：`A記録`。
  - CVMの記録：すなわちドメイン名のプレフィックス。この例はすべてのプレフィックスの解析を例として、`*.qcloudtest.com`に設定します。
  - 回線タイプ：デフォルト。
  - 記録値：【クラウドリソースの関連付け】をクリックして、ポップアップウィンドウで作成したばかりの`clb-test`を選択します。
  - TTL：デフォルト値`600s`に設定します。
  - 追加が完了後、【保存】をクリックします。

クラウド解析がこの記録をInternet上で広めるにはしばらく時間がかかります。ドメイン名が正常に解析されているかどうかをテストするため、解析記録を追加した後しばらく経ってから、バインディングされたCNAMEドメイン名（例：この例では、www.qcloudtest.com）に直接アクセスすることによりCLBを検証することができます。

