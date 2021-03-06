# AppLovinドキュメント
- [AppLovin Webサイト](https://dash.applovin.com/)
- [AppLovin 開発者ガイド](https://dash.applovin.com/docs/integration#androidIntegration)

## 前提条件
- Android API レベル 14 以上

## 依存関係の導入
アプリケーションレベルの build.gradle に、下記の依存関係を追加します。

```java
dependencies {
    // AppLovin
    implementation "com.access_company.adlime:mediation_applovin:9.9.2.1"
    implementation "com.applovin:applovin-sdk:9.9.2"
    implementation "com.google.android.gms:play-services-ads:17.2.1"
}
``` 

## AndroidManifest の設定
[APPLOVIN_KEY]に AppLovin によって割り当てられる Key を設定してください。
```java
<meta-data
    android:name="applovin.sdk.key"
    android:value="[APPLOVIN_KEY]" />
```

## NetworkConfig の設定

### バナー広告
- AppLovinBannerConfig<br>
バナー広告の配置，広告をwindowから離れる時に自動デストロイかどうか。デストロイされないと黙認される。

    ```java
    AppLovinBannerConfig.Builder()
                        // 自動デストロイかどうかの設置
                        .setAutoDestroy(false)
                        .build();
    ```

## 広告フォーマット

### 利用可能なフォーマット

|ネットワーク|バナー|インタースティシャル|動画リワード|ネイティブ|
|:------: |:---:|:----------:|:------:|:----:|
| AppLovin |Y    |Y          |Y      |Y    |

### バナーサイズ
|ネットワーク   |320 × 50   |300 × 250   |320 × 100   |468 × 60   |728 × 90   |スマート   |
| :------: | :------: | :--------: | :-------: | :------: | :------: | :-------: |
|  AppLovin  |Y     |Y        |        |      |       |        |

### 設定情報
下記の AppLovin の情報が必要になります。  
- Zone ID&emsp;&emsp;**※Zone ID はオプションです。**

## バージョン情報

### リリースバージョン
| AppLovin バージョン | アダプタ バージョン|
|:-----------------|:----------------|
|9.9.2             |9.9.2.1          |
|9.7.2             |9.7.2.1          |
|9.7.2             |9.7.2.0          |

### バージョン履歴
| バージョン | 日付      | 更新内容                      |
|:---------|:----------|:----------------------------|
|9.9.2.1   |2019-10-24 | AppLovinBannerConfigの追加|
|9.0.2.0   |2019-10-23 | AppLovin SDK 9.9.2 に対応|
|9.7.2.1   |2019-9-28  | SDKの最適化  |
|9.7.2.0   |2019-7-18  | AppLovin SDK 9.7.2 に対応|
