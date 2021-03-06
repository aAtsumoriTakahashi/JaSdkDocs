# DFPドキュメント
- [DFP Webサイト](https://developers.google.cn/ad-manager)
- [DFP 開発者ガイド](https://developers.google.cn/ad-manager/mobile-ads-sdk/android/quick-start)

## 前提条件
- Android API レベル 14 以上

## 依存関係の導入
アプリケーションレベルの build.gradle に、下記の依存関係を追加します。

```java
dependencies {
    // DFP
    implementation "com.access_company.adlime:mediation_admob:15.0.1.10"
    implementation "com.google.android.gms:play-services-ads:15.0.1"
}
```

## 広告フォーマット

### 利用可能なフォーマット
|ネットワーク |バナー|インタースティシャル|動画リワード|ネイティブ|
|:------:|:----:|:----------:|:------:|:----:|
|DFP     |Y     | Y          |Y       |Y     |

### バナーサイズ
|ネットワーク|320 × 50  |300 × 250 |320 × 100 |468 × 60 |728 × 90 |スマート |
|:-----:|:------:|:------:|:------:|:-----:|:-----:|:----:|
|DFP    |Y       |Y       |Y       |Y      |Y      |Y     |

### 設定情報
下記のDFPの情報が必要になります。  
- App ID  
- AdUnit ID

## バージョン情報

### リリースバージョン
| DFP バージョン | アダプタ バージョン|
|:-------------|:----------------|
| 17.2.1       | 17.2.1.5        |
| 17.1.2       | 17.1.2.11       |
| 15.0.1       | 15.0.1.9        |

### バージョン履歴
| バージョン   | 日付        | 更新内容                   |
|------------|------------|--------------------------------- |
| 17.2.1.5   | 2019-10-31 |ネイティブ広告とフィードリスト広告では、InteractiveAreは設置される場合にMediaViewLayoutを追加されないと画像が展示されないという問題を解決する|
| 17.2.1.2   | 2019-10-2  |ネイティブ広告はクリックエリアのカスタムをサポート|
| 17.2.1.0   | 2019-7-18  |DFP SDK 17.2.1 に対応。複数のリワード広告の読み込みに対応|
| 17.1.2.11  | 2019-10-31 |ネイティブ広告とフィードリスト広告では、InteractiveAreは設置される場合にMediaViewLayoutを追加されないと画像が展示されないという問題を解決する|
| 17.1.2.7   | 2019-7-16  |動画リワード広告のクリックイベントが通知されない問題を修正|
| 17.1.2.4   | 2019-6-12  |ネイティブ広告のクリックイベントの改善|
| 15.0.1.9   | 2019-10-31 |ネイティブ広告とフィードリスト広告では、InteractiveAreは設置される場合にMediaViewLayoutを追加されないと画像が展示されないという問題を解決する|