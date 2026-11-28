# BENCHCORE 新製品・価格ウォッチ

CPU・GPUの新製品と国内価格の動きを毎日チェックした記録。新しい日付を上に追記する。
スプレッドシートは本番サイトに直接反映されるため、ここには「追加・更新すべき行の提案」だけを書く。反映するかどうかはらすくが判断する。

CSVの列は `index.html` の読み込み処理に合わせている:
- CPUシート: `CPU名,PassMarkスコア,コア数,スレッド数,TDP,クロック,キャッシュ,価格(円),コスパ指数`（後半の読み込み処理は `ソケット` 列も参照するので、シートに列があれば埋める）
- GPUシート: `GPU名,3DMark Time Spy,TDP,VRAM,帯域幅,コスパ,価格(円)`
- スコア列が空だとサイトに表示されない（`score > 0` の行だけ読み込むため）。出典のないスコアは書かない

---

## 2026-11-28（土）

### 1. CPU国内価格: Core Ultra 5 245K が初の3万円割れ、Ryzenは軒並み値上がり ★
AKIBA PC Hotline! の「11月後半のCPU価格」（11/26公開、調査日 11/14〜11/21、アキバ店頭の**最安値・税込**）。比較対象は前回調査（10/31〜11/7）。
- **何があった**: Intel Core Ultra 200S が値下がり、AMD Ryzen は値上がりが目立つ。245K が3万円を割るのは今回が初めて（記事より）。Ryzen 5 9600 が 9600X より高くなる逆転も起きている
- **10%前後以上動いた主なモデル**（前回価格と%は記事の「前回比」から計算）:

  | モデル | 今回最安 | 前回比 | 前回 | 変化率 |
  |---|---|---|---|---|
  | Core Ultra 5 245K | 29,980円 | -3,000 | 32,980円 | -9.1% |
  | Core Ultra 7 265K | 44,980円 | -4,820 | 49,800円 | -9.7% |
  | Ryzen 9 9900X3D | 102,690円 | -10,110 | 112,800円 | -9.0% |
  | Ryzen 7 8700F | 34,980円 | +12,000 | 22,980円 | +52.2%（在庫ショップ減少、3店のみ） |
  | Ryzen 5 9600 | 42,580円 | +10,000 | 32,580円 | +30.7% |
  | Ryzen 9 9900X | 78,970円 | +15,170 | 63,800円 | +23.8% |
  | Ryzen 7 9850X3D | 81,800円 | +11,750 | 70,050円 | +16.8% |
  | Ryzen 5 7600 | 36,480円 | +4,880 | 31,600円 | +15.4% |
  | Ryzen 5 8500G | 28,980円 | +3,480 | 25,500円 | +13.6% |
  | Ryzen 5 8600G | 36,800円 | +3,670 | 33,130円 | +11.1% |
  | Ryzen 7 9800X3D | 71,800円 | +6,000 | 65,800円 | +9.1% |

  - 変化なし: Ryzen 7 9700X 44,800円、Ryzen 5 9600X 41,800円、Ryzen 7 7800X3D 54,800円、Ryzen 5 5600 19,980円 など
  - 値上がりの理由は記事に書かれていない（8700F と Core Ultra 9 285 だけ「在庫ショップ数の減少」と記載）
- **出典**:
  - AKIBA PC Hotline!「『Core Ultra 5 245K』が初の3万円割れ、Ryzenは値上がりの動きが目立つ [11月後半のCPU価格]」(2026/11/26) https://akiba-pc.watch.impress.co.jp/docs/price/monthly_repo/2158919.html
  - 前回分: AKIBA PC Hotline!「11月前半のCPU価格」(2026/11/12) https://akiba-pc.watch.impress.co.jp/docs/price/monthly_repo/2155701.html
- **スプレッドシート（CPUシート）の価格更新提案**: シートに該当行がある場合、**`価格(円)` 列だけ**を下の値に直す（スコアなど他の列は既存のまま。`コスパ指数` は既存の式で再計算）。行がない場合は追加しない（出典つきのスコアを今回取っていないため）
  ```csv
  CPU名,価格(円)
  Core Ultra 5 245K,29980
  Core Ultra 7 265K,44980
  Ryzen 9 9900X3D,102690
  Ryzen 7 8700F,34980
  Ryzen 5 9600,42580
  Ryzen 9 9900X,78970
  Ryzen 7 9850X3D,81800
  Ryzen 5 7600,36480
  Ryzen 5 8500G,28980
  Ryzen 5 8600G,36800
  Ryzen 7 9800X3D,71800
  ```
  - 注意: アキバ店頭の最安値（2〜6店）で、調査は 11/21 時点。11/30〜のAmazonブラックフライデー本セールで一時的にまた動く可能性あり
  - シートの現在値はこちらから読めなかった（シートのCSVにアクセスできない環境）ので、すでに同じ値なら更新不要
- **サイト的な注意**: フォールバック用の内蔵データ（`index.html` の BPARTS）は Ryzen 7 9800X3D 89,800円、Core Ultra 7 265KF 48,880円（店頭は 41,980円）と古い。「コスパ最強CPU」系のランキングが今の相場とずれる
- **サイト的な価値**: 「245K 3万円」「Ryzen 値上がり」「Intel と AMD どっちが安い」系の話題に乗れる。今は Intel 側のコスパが上がっているので、ランキングの価格が新しいほど検索で来た人に刺さる

### 2. 参考: GeForce RTX 50 の卸価格は下落継続、ただし供給減のうわさ（背景情報）
- 11/23 と 11/16 の卸価格比較で RTX 5070 が約300元（約6,900円）、5060 Ti 8GB が約150元、5060 Ti 16GB が約100元、5060 が約50元下がった（中国のサプライチェーン筋、ニッチなPCゲーマー経由）
- 一方、NVIDIA がボードパートナーに「中国向けゲーミングGPUの供給が 2026年Q4（11月〜翌1月）に前期比20〜30%減る」と伝えたとのリーク（中国フォーラム 博板堂、NVIDIA未確認）。国内価格がこの先また上がる要因になりうる
- **出典**:
  - ニッチなPCゲーマー (2026/11/23) https://www.nichepcgamer.com/archives/post-134236.html
  - ニッチなPCゲーマー (2026/11/26) https://www.nichepcgamer.com/archives/post-134271.html
- **スプレッドシート**: 変更提案なし（卸価格・うわさ段階のため）

### その他（スプレッドシート対象外）
- 11/27〜28 に新しいデスクトップCPU・グラボの国内発売記事はなし（AKIBA PC Hotline! トップは 11/27 12:30 更新が最新、価格.com 新製品ニュースのグラボは 11/25 の ASRock Intel Arc Pro B65 Creator 32GB〈ワークステーション向け、11/27発売〉が最新） https://akiba-pc.watch.impress.co.jp/ ／ https://news.kakaku.com/prdnews/cd=pc/ctcd=0550/id=160556/
- PC Watch の 11/28 のお買い得品は Mac mini などで、CPU・グラボ単体のセールはなし https://pc.watch.impress.co.jp/docs/news/todays_sales/2160187.html
- 4Gamer: NVIDIA RTX Spark（N1X）搭載ノート ProArt P16 のゲーム性能検証（11/27、ノート向けSoCなのでシート対象外） https://www.4gamer.net/games/050/G105051/20261126054/
- Intel Nova Lake-S（28コア）の PassMark リークは 10/26 の話で今回の範囲外 https://www.techpowerup.com/354143/28-core-intel-nova-lake-s-cpu-shows-promising-performance-boost-in-leaked-benchmark

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
