# BENCHCORE 新製品・価格ウォッチ

CPU・GPUの新製品と国内価格の動きを毎日チェックした記録。新しい日付を上に追記する。
スプレッドシートは本番サイトに直接反映されるため、ここには「追加・更新すべき行の提案」だけを書く。反映するかどうかはらすくが判断する。

CSVの列は `index.html` の読み込み処理に合わせている:
- CPUシート: `CPU名,PassMarkスコア,コア数,スレッド数,TDP,クロック,キャッシュ,価格(円),コスパ指数`（後半の読み込み処理は `ソケット` 列も参照するので、シートに列があれば埋める）
- GPUシート: `GPU名,3DMark Time Spy,TDP,VRAM,帯域幅,コスパ,価格(円)`
- スコア列が空だとサイトに表示されない（`score > 0` の行だけ読み込むため）。出典のないスコアは書かない

---

## 2026-11-27（金）

### 1. Ryzen 5 5500F が国内発売（新製品）★
- **何があった**: Socket AM4 の新CPU「Ryzen 5 5500F」（100-100001905BOX）が11月27日11時から国内販売開始。店頭価格は **16,980円**。6コア12スレッド、ベース3.0GHz／最大4.4GHz、TDP 65W、Wraith Stealthクーラー付属。内蔵GPUなし（ディスクリートGPU必須）。既存の Ryzen 5 5500 に比べてベースクロックは下がった（3.6→3.0GHz）が、ブーストは上がり（4.2→4.4GHz）、PCIe Gen4 に対応
- **ベンチ**: PassMark CPU Mark **20,398**（シングル 3,249、サンプル数79、2026/11/27時点）。Ryzen 5 5500（19,246）より約6%高い
- **出典**:
  - AKIBA PC Hotline!「AM4環境の新CPU『Ryzen 5 5500F』が発売、価格は16,980円」(2026/11/27) https://akiba-pc.watch.impress.co.jp/docs/news/news/2159563.html
  - AMD公式 製品ページ（仕様） https://www.amd.com/ja/products/processors/desktops/ryzen/5000-series/amd-ryzen-5-5500f.html
  - PassMark 5500F vs 5500 https://www.cpubenchmark.net/compare/7509vs4807/AMD-Ryzen-5-5500F-6--vs-AMD-Ryzen-5-5500
  - 参考: エルミタージュ秋葉原 (2026/11/27) https://www.gdm.or.jp/crew/2026/1127/662240 （取得できず未確認）
- **スプレッドシート（CPUシート）に追加提案**:
  ```csv
  CPU名,PassMarkスコア,コア数,スレッド数,TDP,クロック,キャッシュ,価格(円),コスパ指数
  Ryzen 5 5500F,20398,6,12,65W,3.0/4.4GHz,19MB (L2 3MB + L3 16MB),16980,
  ```
  - `ソケット` 列がある場合は `AM4`
  - `コスパ指数` は既存行と同じ計算式で埋めてください（式がリポジトリ内にないので空欄にしています）
  - `クロック` `キャッシュ` の書式は既存行に合わせて調整してください
- **サイト的な価値**: 「AM4 アップグレード」「1万円台 CPU」系の検索需要に合う。PC構成ビルダーは今 LGA1700/AM5 前提のパーツしかないので、AM4 の安価構成を入れるならマザーボード側（B550等）の追加も必要

### 2. Amazonブラックフライデー先行セールでグラボが1万円以上安く（一時的な値下がり）
11/30〜12/7 の本セールの前の先行セール。価格は期間限定なので、**スプレッドシートの価格列は更新しない**のをおすすめ（セール終了で戻る可能性が高い）。
- **GeForce RTX 5060**（MSI 8G VENTUS 2X OC V1）: **79,800円**（11/26比 10,088円引き、約11%減）。ただし国内最安は11/3時点ですでに79,800円（gaming-st調べ）で、相場より下がったわけではない
- **Radeon RX 9060 XT 16GB**（ASRock Challenger、ドスパラ公式ストア）: **81,800円**（直近より18,000円安い、約18%減）。gaming-st が集計した11/2の国内最安 93,737円 と比べても約13%安く、今回いちばん大きい動き
- **Radeon RX 9070 GRE 12GB**（ASUS PRIME OVER EDITION）: **90,719円**（直近より10,081円引き、約10%減）
- **出典**:
  - PC Watch「本日みつけたお買い得品」(2026/11/27) https://pc.watch.impress.co.jp/docs/news/todays_sales/2159814.html
  - ゲーミングスタイル GPU価格レポート（11/2時点の国内最安、11/3更新） https://gaming-st.com/news/gpu-price-report-2026-04/
- **スプレッドシート**: 変更提案なし（一時的なセール価格のため）

### 3. 参考: RTX 50シリーズの国内価格は高止まり（背景情報、48時間より前）
- メモリ高騰の影響で、10月上旬→11月上旬に RTX 5080 が約26%、RTX 5060 Ti 8GB が約30% 上がった（gaming-st、国内通販最安の集計）。ドスパラ最安では RTX 5070 Ti 234,780円、RTX 5080 329,800円、RTX 5090 1,098,000円（AUTOMATON、11/9）
- 11/20 のアキバでは ROG Astral RTX 5090 が150万円超え（AKIBA PC Hotline!）
- **サイト的な注意**: フォールバック用の内蔵データ（`index.html` の BPARTS）の GPU 価格は RTX 4090 239,800円など旧世代・旧価格のまま。スプレッドシート側の GPU 価格も今の相場とずれている可能性があるので、一度見直すと良さそう
- **出典**:
  - ゲーミングスタイル (2026/11/4公開・11/7更新) https://gaming-st.com/news/rtx50-november-price-hike-colorful-galax-japan/
  - AUTOMATON (2026/11/9) https://automaton-media.com/articles/newsjp/20261109-478291/
  - AKIBA PC Hotline!「アキバお買い得価格情報（11月19日～20日調査）」 https://akiba-pc.watch.impress.co.jp/docs/sale/2158015.html

### その他（スプレッドシート対象外）
- ASUS「TUF Gaming Radeon RX 9070 XT Onimusha Way of the Sword Edition」が11/27発売、店頭価格249,800円（ゲームクーポン付きのコラボモデル。GPU自体は既存の RX 9070 XT なので行の追加は不要） https://akiba-pc.watch.impress.co.jp/docs/news/news/2159623.html
- PC Watch の 11/25〜26 の記事には、デスクトップCPU/GPUの新製品・価格・ベンチの話題はなし https://pc.watch.impress.co.jp/backno/top/index.html
