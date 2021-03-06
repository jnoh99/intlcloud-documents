## 概要
現在、CVMは敏感的操作に対するプロテクション機能をサポートしています。敏感的操作を実行する前に、身分を表明できる証明を入力し身分を検証してから、関連操作が実行できるようになります。
敏感的操作に対するCVMのプロテクション機能はアカウントリソースのセキュリティを有効的に保証することができます。現在、シャットダウン、リスタート、VNCログイン、パスワードリセット、廃棄、システムリインストール、コンフィギュレーション調整、キーのロード、Virtual Private Cloudの切り替え、自動更新設定等を対応しています。

## 操作プロテクションを有効にする
 [セキュリティコンフィギュレーション](https://console.cloud.tencent.com/developer/security) で操作プロテクションを有効にすることができます。詳細については、 [操作プロテクション](https://cloud.tencent.com/document/product/378/10740)をご参照ください。

## 操作プロテクションの検証
操作プロテクションを有効にしている場合は、敏感的操作を実行する時に、先に操作プロテクションの検証が行われます。
-  **MFA検証**を有効にし操作プロテクションを行っている場合は、MFAデバイスにおける6桁のダイナミック検証コードを入力する必要があります。
- **携帯電話の検証コード**を有効にし操作プロテクションを行っている場合は、携帯電話の検証コードを入力する必要があります。
