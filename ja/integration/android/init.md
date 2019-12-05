﻿# 初期化
広告を読み込む前に、AdLime アプリ ID で初期化を行います。この処理は1回だけ実行します。(アプリの起動時に実行することが望ましい)

## AdLime SDK の初期化

1. 初期化は Activity の onCreate メソッドで実行します。<br>
        - setGdprConsent メソッドを呼び出し、 GDPR を設定します。<br> 
        - AdLimeConfiguration インスタンスを作成し、アプリ ID を設定後、 最後に initialize メソッド で初期化します。

2. Activity のライフサイクル onBackPressed メソッドにおいて、SDK の onBackPressed メソッドを呼び出してください。

## サンプルコード
下記のコードをご参照ください。

```java
@Override
protected void onCreate(Bundle savedInstanceState) {
    ...
    AdLime.getDefault().setGdprConsent(true);

    // NWの全体配置を設置する
    AdLime.getDefault().setGlobalNetworkConfigs(
                NetworkConfigs.Builder()
                        .addConfig(DFPGlobalConfig.Builder()
                                .addTestDevice("test device id 1")
                                .addTestDevice("test device id 2")
                                .build())
                        .addConfig(...)
                        .build());

    AdLimeConfiguration configuration = new AdLimeConfiguration.Builder(this)
                .appId("YOUR APP ID") //the APP_ID generated by AdLime
                .build();

    AdLime.getDefault().initialize(this, configuration);
    ...
}
...

```
Chartboost　を使う場合、 Chartboost 広告を表示する全ての Activity に下記のコードを追加する必要がある。
```java
@Override
public void onBackPressed() {
    super.onBackPressed();
    ...
    AdLime.getDefault().onBackPressed(this);
    ...
}
```

## テスト用の広告枠
Android の各広告フォーマットの、テスト用広告ユニット ID は、以下の通りです。

テスト アプリ ID           : 14fac732-0853-4f1e-83a4-77db7915fc62

| 広告フォーマット          | テスト広告ユニット ID                 |
|:---------------------- |:------------------------------------- |
|バナー                   |e302ae32-d770-4635-9b2f-97fd024e059e   |
|インタースティシャル        |ecc5a7d7-872b-4c6c-a042-6b0b311ccc04   |
|ネイティブ                |444dd66b-af52-4fd1-9260-5559e7488432   |
|動画リワード               |cca19625-d829-4902-8164-1e75a0e5e6f5   |

## SDK の例
各広告の実装について、[SDKの例](https://github.com/Ham-mer/AdLime-Android-Demo)をご覧ください 。