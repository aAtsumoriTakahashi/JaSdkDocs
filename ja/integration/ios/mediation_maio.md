# Maio ドキュメント
- [Maio Webサイト](https://maio.jp/)
- [Maio 開発者ガイド](https://github.com/imobile-maio/maio-iOS-SDK)

## 前提条件
- ターゲットバージョン iOS 8.0 以上

## SDKの導入

AdLime SDK で Maio を使用するためには、 Maio SDK と、それに対応した AdLime SDK を導入してください。

### CocoaPods

CocoaPods を使用すると導入が簡単です。プロジェクトの Podfile を開き、下記のコードをアプリのターゲットに追加してください。
```objectivec
pod 'AdLimeMediation_Maio'
```

コマンドラインから、以下を実行してください。
```objectivec
pod install --repo-update
```

### 手動でダウンロード
SDK を 直接ダウンロードして解凍し、下記のフレームワークを Xcode プロジェクトにインポートしてください。
- [Maio.framework](https://github.com/imobile-maio/maio-iOS-SDK/releases/download/v1.4.8/Maio.framework.zip)
- [AdLimeMediation_Maio.framework](https://github.com/Ham-mer/AdLime-iOS-Pub/raw/master/DownloadZip/AdLimeMediation_Maio/1.4.8.0.zip)

### Carthage
SDK を 直接ダウンロードして解凍し、フレームワークを Xcode プロジェクトにインポートしてください。
- [Maio.framework](https://github.com/imobile-maio/maio-iOS-SDK/releases/download/v1.4.8/Maio.framework.zip)

プロジェクトの Cartfile を開き、下記のコードをアプリのターゲットに追加してください。
```objectivec
github "Ham-mer/AdLimeMediation_Maio"
```

コマンドラインから、以下を実行してください。
```objectivec
carthage update
```

完了後、Carthage フォルダの AdLimeMediation_Maio > AdLimeMediation_Maio.framework をプロジェクトにインポートします。

## 利用可能な広告フォーマット

### 広告フォーマット
|ネットワーク|バナー|インタースティシャル|動画リワード|ネイティブ|
|:-----:|:----:|:----------:|:------:|:----:|
|Maio   |      | Y          |Y       |      |

## 広告枠の配置
AdLimeのページにてMaioの広告枠を配置するためには、まずMaioのページにおいて広告枠を作成して、下記の情報を獲得する必要があります。：  
- Media ID
- Zone ID

AdLime の管理画面を開き、左側の「ネットワーク」メニューをクリックして、Maio を有効にしてください。

最後に、左側の「アプリ」メニューをクリックし、 Maio 広告を表示する広告枠で、「広告のソース追加」をクリックし、Maio 広告を追加してください。

## バージョン情報

### リリースバージョン
| Maio バージョン     | アダプタ バージョン |
|:-----------------|:----------------|
| 1.4.8            | 1.4.8.0         |
| 1.4.6            | 1.4.6.2         |

### バージョン履歴
| バージョン        | 日付       | 更新内容                           |
|-----------------|------------|----------------------------------|
| 1.4.8.0         | 2019-10-10 | Maio SDK 1.4.8 に対応          |
| 1.4.6.2         | 2019-8-6   | 不要なヘッダーファイルの削除|
| 1.4.6.1         | 2019-7-15  | 動画リワード広告のイベント最適化     |
| 1.4.6.0         | 2019-6-30  | Maio SDK 1.4.6 に対応          |
