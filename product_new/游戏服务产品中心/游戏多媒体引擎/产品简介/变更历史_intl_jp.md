## GME_SDK2.5 2019-06-27
### 新規機能
- リアルタイム音声チャットルーム内のメンバーの上がり音量獲得インターフェースと下り音量獲得インターフェースを追加しました。
- オフライン音声の録音設定/再生音量及び録音獲得/再生音量のインターフェースを追加しました。
- オフライン音声の録音中止と録音再開のインターフェースを追加しました。

### 機能の最適化
エラーコードを更新し、エラーシナリオを具体化しました。


## GME_SDK2.3.5 2019-03-25
### 新規機能
- 新しく Android v8a アーキテクチャに対応しました。
- Android での低レイテンシーキャプチャー・再生に対応しました。

### 機能の最適化
安定性を向上させました。

## GME_SDK2.3 2019-01-11
### 新規機能
- リアルタイム音声チャット中に、オフライン音声が使用できるようになりました。
- リアルタイム音声のフィルタリングに対応し、暴力、テロ、性的、政治的な内容を認識できるようになりました。
- H5 リアルタイム音声チャットに対応し、オールプラットフォーム間のリアルタイム音声の相互通信が可能になりました。

### 機能の最適化
- SDK 範囲音声機能のインターフェースを最適化し、アクセス条件を下げました。
- 音声ノイズ除去の効果を最適化しました。
- SDK のメモリ消費量を大幅に下げました。

## GME_SDK2.2 2018-10-29
### 新規機能
- 複数のカラオケ音響効果に対応するようになりました。
- 超大ルームのユーザー体験を最適化し、レイテンシーの低減によってよりスムーズな体験を実現しました。
- オフライン音声メッセージはストリーミングボイステキスト変換に対応するようになりました。
- Windows で BGM 機能に対応するようになりました。

### 機能の最適化
- 音声の帯域幅を最適化し、よりトラフィックを節約できるようになりました。
- CPU とメモリの性能を最適化しました。

## GME_SDK2.1.5 2018-09-13
### インターフェース変更
- GenAuthBuffer パラメータの roomId タイプを int32 型から文字列型に変更しました。
- EnterRoom パラメータの roomId  タイプを int32 型から文字列型に変更しました。
- SetMicVolume をマイクハードウェア音量設定からマイクソフトウェア音量設定に変更しました。
- GetMicVolume をマイクハードウェア音量獲得からマイクソフトウェア音量獲得に変更しました。

### 機能の最適化
- ルーム番号をint32 型から文字列型にアップグレードしました。
- 音量調節インターフェースをハードウェア音量設定・獲得からソフトウェア音量設定・獲得に変更しました。
- Bug を修正し、安定性を向上させました。


## GME_SDK2.1 2018-08-21
### 新規機能
- Windows でボイス・チェンジに対応するようになりました。
- Windows でオフライン音声に対応するようになりました。
- Windows で 3D サウンドに対応するようになりました。
- Android SDK は x86 アーキテクチャに対応するようになりました。
- iOS と MacSDK は XCode10 に対応するようになりました。

### 機能の最適化
- オフライン音声認証を最適化しました。
- モバイルデバイスは個別オフ機能に対応するようになりました。
- 中等レベル音質のネットワークイミュニティを最適化しました。

## GME_SDK2.0 2018-06-22
### 新規機能
- GMEはPC Native、PC Unity バージョンをリリースしました。
- GMEはUnrealエンジンに対応するようになりました。
- GMEオフラインボイスツーテキスト変換は多言語に対応するようになりました、最大120言語に対応できます。
- GME PCバージョンは3Dリアルタイム音声に対応するようになりました。

### 機能の最適化
- 通話音量の高音質体験を向上させました。
- アクセス条件を下げ、スムーズな音質や普通の音質、高音質など多様な選択を提供するようになりました。
- 安定性を向上させました。

## GME_SDK1.2    2018-04-02
### 新規機能
- GME は Cocos エンジンに対応するようになりました。
- マイク音量調節インターフェースを提供しました。
- モバイルデバイスでチーム内音声チャットがてきるようになりました、バトロワ系ゲームの体験を向上させます。
- PC バージョンは多種類の形式の BGM 再生に対応するようになりました。
- Android バージョンの BGM 再生はより多くの形式に対応するようになりました。

### 最適化
- 人狼ゲームのユースケースでのオーディオ前処理効果を最適化し、多人数は同時発言の音声をよりはっきりと聞こえるようにさせました。
- カラオケなどユースケースでの音質効果を最適化し、より高い音質の設定に対応するようになりました。
-  Moba ゲームのユースケースでの音声ディレーを最適化し、チーム内音声チャットのディレーを低減させました。
- ノイズ除去のアルゴリズムを最適化し、音声チャットの音質をよりきれいにしました。

## GME_SDK1.1    2017-10-18

### 新規機能
- ゲーム SDK は複数形式の BGM と音響効果に対応するようになりました。
- ゲームのユースケースでのオフライン音声及びボイスツーテキスト変換機能を新しく追加しました。

### 最適化
- ルーム入室認証のクライアント実現モジュールを提供し、 SDK のアクセス条件を下げました。
- iOS / Android バージョンのきしみ音抑制効果を最適化しました。
- 人狼ゲームのユースケースでの音質安定性、ネットワークイミュニティなど指標を最適化しました。

### 修正
Android 4.2 及びそれ以下のバージョンで必ず発生するcrash問題を修正しました。





