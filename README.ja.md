# chart-pie

CSVまたはJavaScriptデータからレスポンシブな円グラフを作成する軽量なWebコンポーネントです。

## デモ

[ライブデモ](https://code4fukui.github.io/chart-pie/)

![data.go.jpのデータからグループごとのリソース数を示す円グラフ。各スライスに名前、数値、パーセンテージのラベルが表示され、中央に合計数が表示されています。](https://github.com/code4fukui/chart-pie)

## 特徴

-   **シンプルで宣言的:** 標準のHTMLカスタム要素（`<chart-pie>`）として使用できます。
-   **柔軟なデータソース:** インラインCSV、外部CSVファイル、またはJavaScriptオブジェクトとしてデータを提供できます。
-   **レスポンシブ:** コンテナに合わせて自動的にリサイズします。
-   **情報豊富なラベル:** 各スライスに名前、値、パーセンテージを表示します。
-   **合計値の表示:** グラフの中央にすべての値の合計を表示します。

## 使い方

### 1. HTMLでの使用

HTMLファイルで`chart-pie.js`モジュールを読み込むと、`<chart-pie>`要素を直接使用できます。

```html
<script type="module" src="https://code4fukui.github.io/chart-pie/chart-pie.js"></script>

<!-- 例1: インラインCSVとしてのデータ -->
<chart-pie style="width: 600px; height: 400px;">
name,count
A,30
B,20
C,70
</chart-pie>

<!-- 例2: 外部CSVファイルからのデータ -->
<chart-pie src="./data.csv" style="width: 100vw; height: 30vh;"></chart-pie>
```

### 2. JavaScriptを使用してプログラムで作成

`ChartPie`クラスをインポートして、プログラムからインスタンスを作成することもできます。

```html
<div id="chart-container"></div>

<script type="module">
  import { ChartPie } from "https://code4fukui.github.io/chart-pie/chart-pie.js";

  // オブジェクトの配列としてのデータ
  const dataArray = [
    { name: "A", count: 30 },
    { name: "B", count: 20 },
    { name: "C", count: 70 },
  ];

  // またはシンプルなキー・バリューのオブジェクトとしてのデータ
  const dataObject = {
    "A": 30,
    "B": 20,
    "C": 70,
  };

  const chart = new ChartPie(dataArray);
  chart.style.width = "300px";
  chart.style.height = "300px";
  
  document.getElementById("chart-container").appendChild(chart);
</script>
```

## API & データ形式

### 要素の属性

-   `src`: CSVファイルのURL。コンポーネントはこのファイルを取得・解析してグラフを生成します。

### データ構造

コンポーネントは以下の形式のデータを受け付けます:

1.  **CSV**: インラインまたは`src`ファイルからのCSVデータには、ヘッダー行が含まれている必要があります。ラベル用の列（例: `name`）と数値用の列（`count`または`value`）の2列が必要です。

    ```csv
    name,count
    Agriculture,96777
    Finance,47496
    Education,28012
    ```

2.  **JavaScript配列**: 各オブジェクトが`name`プロパティと`count`または`value`プロパティを持つオブジェクトの配列。

    ```javascript
    [
      { name: "A", value: 30 },
      { name: "B", value: 20 },
      { name: "C", value: 70 }
    ]
    ```

3.  **JavaScriptオブジェクト**: キーがラベル、値が数値データとなるシンプルなキー・バリューのオブジェクト。

    ```javascript
    {
      "A": 30,
      "B": 20,
      "C": 70
    }
    ```

## ライセンス

MIT License — [LICENSE](LICENSE)を参照してください。
