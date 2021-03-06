# Nend
- [Nend Webサイト](https://nend.net/)
- [Nend 開発者ガイド](https://github.com/fan-ADN/nendSDK-iOS)

## 前提条件
- ターゲットバージョン iOS 8.1 以上

## SDKを導入する
AdLime SDK で Nend を使用するためには、最初のステップは Nend SDK と、それに対応した AdLime SDK を導入してください。

### CocoaPods
CocoaPods を使用すると導入が簡単です。プロジェクトの Podfile を開き、下記のコードをアプリのターゲットに追加してください。
```objectivec
pod 'AdLimeMediation_Nend'
```

コマンドラインから、以下を実行してください。
```objectivec
pod install --repo-update
```

### 手動でダウンロード
SDK を 直接ダウンロードして解凍し、フレームワークを Xcode プロジェクトにインポートしてください。
- [NendAd.embeddedframework](https://github.com/fan-ADN/nendSDK-iOS-pub/releases/download/5.3.0/nendSDK_iOS.zip)
- [AdLimeMediation_Nend.framework](https://github.com/Ham-mer/AdLime-iOS-Pub/raw/master/DownloadZip/AdLimeMediation_Nend/5.3.0.0.zip)

### Carthage
SDK を 直接ダウンロードして解凍し、フレームワークを Xcode プロジェクトにインポートしてください。
- [NendAd.embeddedframework](https://github.com/fan-ADN/nendSDK-iOS-pub/releases/download/5.3.0/nendSDK_iOS.zip)

プロジェクトの Cartfile を開き、下記のコードをアプリのターゲットに追加してください。
```objectivec
github "Ham-mer/AdLimeMediation_Nend"
```

コマンドラインから、以下を実行してください。
```objectivec
carthage update
```

完了後、Carthage フォルダの AdLimeMediation_Nend > AdLimeMediation_Nend.framework をプロジェクトにインポートします。

## 他のフレームワークの追加
以下のフレームワークを追加する必要があります。

- AdSupport.framework
- Security.framework
- ImageIO.framework
- AVFoundation.framework
- CoreMedia.framework
- SystemConfiguration.framework
- WebKit.framework

以下のフレームワークはオプションです。 広告の詳細情報を取得可能です。
- CoreLocation.framework
- CoreMotion.framework
- CoreTelephony.framework

## 利用可能な広告フォーマット

### 広告フォーマット
|ネットワーク|バナー|インタースティシャル|動画リワード|ネイティブ|
|:-----:|:----:|:----------:|:------:|:----:|
|Nend   |Y     | Y          |Y       |Y     |

### バナーサイズ
|ネットワーク  |320 × 50  |300 × 250   |320 × 100  |468 × 60  |728 × 90  |スマート    |
|:-------:|:------:| --------:|:-------:|:------:|:------:|:-------:|
|Nend     |Y       |Y         |Y        |        |Y       |         |

## 広告枠の設置

AdLime を使って Nend の広告枠を設置する前に、Nend の管理画面上で広告枠を作成し、その広告枠の情報が必要になります。
- Api Key
- Spot Id

AdLime の管理画面を開き、左側の「ネットワーク」メニューをクリックして、 Nend を有効にしてください。

最後に、左側の「アプリ」メニューをクリックし、 Nend を表示する広告枠で、「広告のソース追加」をクリックし、Nend を追加してください。

**Nend には、ネイティブ広告は二つの種類があります。ネイティブ広告を追加する場合に Native Mode を入力してください**
| Native Mode     | 値 |
|:----------------|:--------|
|Native Ads       |0        |
|Native Video Ads |1        |

**Nendには、インタースティシャル広告は三つの種類があります。インタースティシャル広告を追加する場合に Native Mode を入力してください**
| Interstitial Mode     | 値 |
|:----------------------|:--------|
|Interstitial Ads       |0        |
|Interstitial Video ads |1        |
|Fullscreen Ads         |2        |

## バージョン情報

### リリースバージョン
| Nend バージョン     | アダプタ バージョン |
|:-----------------|:----------------|
|5.3.0             |5.3.0.0          |
|5.1.1             |5.1.1.4          |

### バージョン履歴
| バージョン    | 日付        | 更新内容                             |
|-------------|------------|----------------------------------|
| 5.3.0.0     | 2019-10-10 | Nend SDK 5.3.0 に対応  |
| 5.1.1.4     | 2019-8-6   | NativeAdLayout インタラクティブエリアのカスタマイズに対応|
| 5.1.1.2     | 2019-7-6   | クラスが重複する問題を改修             |
| 5.1.1.1     | 2019-7-2   | インターステーシャル広告イベントの最適化             |
| 5.1.1.0     | 2019-6-30  | Nend SDK 5.1.1 に対応  |
