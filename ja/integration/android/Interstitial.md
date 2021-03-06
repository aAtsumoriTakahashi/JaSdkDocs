# インタースティシャル広告

インタースティシャル広告とは、アプリ上にオーバーレイで表示されるフルスクリーン広告です。一般的にアプリの画面が切り替わるタイミング（アクティビティが切り替わるタイミングやゲームのステージが変わる合間）で表示されます。アプリにインタースティシャル広告が表示される場合、ユーザーは広告をタップしてリンク先 URL に移動するか、広告を閉じてアプリに戻るかを選ぶことができます。


このガイドは、インタースティシャル広告を Android アプリに実装方法について説明します。

## 前提条件

- AdLime SDK が導入済みであること

## インタースティシャル広告オブジェクトを作成する

インタースティシャル広告は、InterstitialAd オブジェクトによってリクエストし、表示されます。まず InterstitialAd をインスタンス化し、その広告ユニットIDを設定してください。

```java
// 広告ユニットID の定義
String interstitial_test = "46dca932-2a10-4702-89fc-e5e87e00b09c";
// InterstitialAd を作成
InterstitialAd mInterstitialAd = new InterstitialAd(context);
mInterstitialAd.setAdUnitId(interstitial_test);
```

## 広告の読み込み

インタースティシャル広告を読み込むには、 InterstitialAd オブジェクトの loadAd() メソッドを実行します。

```java
// 広告の読み込み
mInterstitialAd.loadAd();
```

## 広告を表示する

インタースティシャル広告は、アプリの流れが一時的に中断する自然なタイミング（ゲームのステージが変わる合間や一つのミッションが完了になった直後など）で表示することが相応しい形です。インタースティシャル広告を表示するには、 isReady() メソッドで読み込みが完了したかどうかを確認し、 show() を呼び出してください。


```java
if (mInterstitialAd.isReady()) {
    // 広告の表示
    mInterstitialAd.show();
}
```

## 広告イベント
広告の動作をより細かくカスタマイズするには、広告のライフサイクルで発生するイベント（読み込み、開始、終了など）を追加することができ、 AdListener クラスを使い、これらのイベントを受け取ることができます。

InterstitialAd で AdListener を利用するには、 setAdListener() メソッドを呼び出してください。

```java
mInterstitialAd.setAdListener(new SimpleAdListener() {
    @Override
    public void onAdFailedToLoad(AdError adError) {
        // 広告の読み込み失敗、エラー詳細は adError から取得
        Log.d(TAG, "on BannerAd FailedToLoad err:" + adError.toString());
    }

    @Override
    public void onAdLoaded() {
        // 広告のロード完了
    }

    @Override
    public void onAdClosed() {
        // 広告を閉じる
        Log.d(TAG, "on BannerAd Closed");
    }

    @Override
    public void onAdClicked() {
        // 広告をクリック
        Log.d(TAG, "on BannerAd Clicked");
    }

    @Override
    public void onAdShown() {
        // 広告を表示
        Log.d(TAG, "on BannerAd Shown");
    }
});
```

### エラーの情報
広告の読み込に失敗した場合は、AdListener の onAdFailedToLoad(AdError adError) が呼び出されます。その際に adError.getCode()、adError.toString() から、エラーコード、エラー情報が取得できます。

 AdError エラーコード一覧
|定義                        |説明     |
|:--------------------------|:--------|
|ERROR_CODE_INTERNAL_ERROR  | 内部エラー |
|ERROR_CODE_INVALID_REQUEST | リクエストが無効 |
|ERROR_CODE_NETWORK_ERROR   | ネットワークエラー |
|ERROR_CODE_NO_FILL         | 配信できる広告がない    |
|ERROR_CODE_TIMEOUT         | リクエスト　タイムアウト |

エラーは AdUnit、ネットワーク、ラインアイテムの各情報が含まれています。

```
ErrorCode is [3], Message is [No Fill]
AdUnit is ...
Network is ...
LineItem is ...
```

## プリロードとキャッシュ
プリロードで事前に広告を用意して展示するまでの時間を短くする<br>
広告をプリロードするかどうかにもかかわらず、広告をキャッシュすることはお勧め。理由としては一つのAdUnitに各LineItemはロードされるはずで、一つの広告インスタンスを繰り返して使うと、展示率を高めて必要ではないリクエストも減らせる。
自ら広告キャッシュを実現できるし、[AdLimeLoader](./adloader.md)でも実現できる。

## 推奨事項

### インタースティシャル広告がアプリに適しているかどうか確認してください。

インタースティシャル広告は、画面の切り替わりがあるアプリに適しています。
このような移行ポイントは、画像の共有やゲームステージのクリアなど、アプリで特定のタスクが完了した際に発生します。ユーザーはこのタイミングで中断が入ることを想定しているので、インタースティシャル広告を表示してもユーザーエクスペリエンスに悪影響を及ぼすことはありません。アプリケーション・プロセスの、どの時点でインタースティシャル広告を表示するか、またユーザーがそれにどう反応するかを共に考慮に入れてください。


### インタースティシャル広告を表示する際には、必ず操作を一時停止してください。

インタースティシャル広告には、テキスト・イメージ・動画など様々な種類があります。インタースティシャル広告を表示する際に、アプリのリソースを一時停止させることが重要です。たとえば、インタースティシャル広告を呼び出した後、アプリの音声出力を一時停止させてください。音声出力は、イベントハンドラ onAdClosed() によって再開できます。このハンドラは、ユーザーが広告に対する操作を完了した後に呼び出されます。また広告を表示している間は、複雑な計算処理（ゲームループなど）も一時停止させてください。こうすることで、画像の読み込みが遅くなり、あるいは反応しなくなったり、動画が頻繁に途切れたりするリスクが低くなります。


### 十分な読み込み時間を確保してください。

インタースティシャル広告を適切なタイミングで表示することも大事ですが、それと同様に読み込みの待ち時間を短くすることも重要です。 show() を呼び出す前に、 loadAd() を実行してください。こうすることで表示前の段階で、インタースティシャル広告の読み込みを完了させることができます。

### 過度に広告を表示しないように注意してください。

インタースティシャル広告の表示頻度を増やすことで収益の向上が見込めますが、それが原因でユーザー体験が損なわれ、クリック率の低下につながる可能性もあります。ユーザーがアプリでの体験を楽しめるように、適度な広告表示頻度に調節しましょう。
