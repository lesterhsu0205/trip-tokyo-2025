# CLAUDE.md - 東京輕井澤行程專案

本檔案為 Claude Code 在處理東京輕井澤行程時的專項指引。

## 專案概述

這是一個家庭旅遊規劃儲存庫，針對 2025 年 10/6-10/13 的東京輕井澤之旅。儲存庫包含詳細的行程文件，專注於帶 1 歲男幼兒和 5 歲男童的家庭旅遊。

## 專案檔案結構

```text
.
├── README.md             # 主要行程檔案 (自動合併版本)
├── CLAUDE.md             # Claude Code 子專案指引
├── todo.md               # 行程前購票及預定等整理
├── remark.md             # 行程中購物資訊及地點整理
├── transportation.md     # 行程中大眾交通資訊整理
├── D1.md                 # 各日詳細行程
├── D2.md
├── ...
└── D8.md
```

## 專案特殊規則

- **當地語言標註**： 有片假名就不需提供平假名，除非只有平假名

## 專案詳細資訊

### 1. **家庭成員配置**

- **成員**： 30+ 歲夫妻 + 1 歲男幼兒 + 5 歲男童
- **特殊需求**：
  - 1 歲幼兒：需嬰兒車、不宜太累的行程
  - 5 歲男童：需適合身高 110 公分的設施

### 2. **交通資訊**

#### 重點資訊

- **航班資訊**：
  - 去程：長榮航空 BR184｜10/6 07:55（TPE terminal 2）→ 12:25（NRT terminal 1）
  - 回程：長榮航空 BR195｜10/13 20:40（NRT terminal 1）→ 23:20（TPE terminal 2）
- **當地交通原則**：
  - 東京：大眾運輸 + iPhone 西瓜卡
  - 輕井澤：租車自駕
  - **迴避尖峰時段**：
    - 上班尖峰：07:30-09:30
    - 下班尖峰：18:00-20:00
    - 違反者提醒是否重新安排時程
- **時間安排要求**：
  - 最少 buffer：10 分鐘
  - 建議 buffer：10-15 分鐘（含嬰兒車移動）
  - 違反者提醒是否重新安排時程

#### **交通資訊查詢要點**

##### **[起點] 與 [終點] 地址格式要求**

- **查詢交通的 [起點] 與 [終點] 皆用日文帶入**
- **[Yahoo Transit] 僅接受日文地址或日文地標名稱**
- 住宿地址：使用 [住宿資訊](#3-住宿資訊) 中標註的日文地址（如「長野県北佐久郡軽井沢町軽井沢（大字）1314-29」）
- 景點地址：使用日文地標名稱或完整日文地址
- ✅ 正確：使用完整日文地址或日文地標名稱
- ❌ 錯誤：使用英文地址或混合格式

##### **交通資訊查詢結果格式**

- **Yahoo Transit**
  - 必須標註：「Yahoo Transit [編號]，[時間] 分鐘，¥[費用]，轉乘 [次數] 次，行駛里程 [距離]km」
  - 注意：「行駛里程」而非「步行」
- **Yahoo Transit URL**：[參考](#yahoo-transit-url)  
- **NAVITIME（自駕）**
  - 必須標註：「NAVITIME [路線類型]，[行駛時間] 分鐘，[距離]km，ETC 過路費 ¥[費用]，預估油耗 [油耗]L」
  - 路線類型：「最佳路線」與「免費道路」
  - 必須顯示兩種路線選項
- **NAVITIME URL**：[參考](#navitime-url)
- **Google Maps URL**：[參考](#google-maps-url)
- 依照[查證標註要求](./../../CLAUDE.md#查證標註要求)格式標註

##### Google Maps URL

- 建構方式
  1. **判斷 [起點] 與 [終點]**：[參考](#起點-與-終點-地址格式要求)
  2. **判斷 [模式]**（根據行程情境自動選擇）
      - `transit`：城市間移動、跨區域移動、明確提到電車/地鐵/巴士
      - `walking`：距離 < 1km、同一區域內、景點間步行
      - `driving`：郊區景點、租車行程、明確提到開車
  3. **帶入參數並建構 Google Maps URL**

- 格式：🗺️ [Google Maps 導航](https://www.google.com/maps/dir/?api=1&origin=[起點]&destination=[終點]&travelmode=[模式])
- 範例：🗺️ [Google Maps 導航](https://www.google.com/maps/dir/?api=1&origin=四ツ木駅&destination=台場駅&travelmode=transit)

##### Yahoo Transit URL

- 建構方式
  1. **判斷 [起點] 與 [終點]**：[參考](#起點-與-終點-地址格式要求)
  2. **判斷時間參數格式****： 2025/10/06 17:01 → `&y=2025&m=10&d=06&hh=17&m1=0&m2=1`
  3. **帶入參數並建構 Yahoo Transit URL**

- 格式：🚃 [Yahoo Transit 導航](https://transit.yahoo.co.jp/search/result?from=[起點]&to=[終點]&y=[年]&m=[月]&d=[日]&hh=[時]&m1=[分鐘十位數]&m2=[分鐘個位數]&type=1&ticket=ic&expkind=1&userpass=1&ws=3&s=0&al=0&shin=1&ex=1&hb=1&lb=1&sr=0)
- 範例：🚃 [Yahoo Transit 導航](https://transit.yahoo.co.jp/search/result?from=四ツ木&to=台場&y=2025&m=10&d=09&hh=09&m1=0&m2=5&type=1&ticket=ic&expkind=1&userpass=1&ws=3&s=0&al=0&shin=1&ex=1&hb=1&lb=1&sr=0)

##### NAVITIME URL

- 建構方式
  1. **判斷 [起點] 與 [終點]**：[參考](#起點-與-終點-地址格式要求)
  2. **查詢 [起點]、[終點] 經緯度**：[使用 WebSearch 查詢地點的 lat/lon 座標](#經緯度查詢方法)
  3. **建構 JSON 格式座標**
     - 起點：{"name":"[起點]","lat":起點緯度,"lon":起點經度}
     - 終點：{"name":"[終點]","lat":終點緯度,"lon":終點經度}
  4. **判斷 [出發時間]**：YYYY-MM-DDTHH%3Amm%3Ass
  5. **自駕查詢必須同時取得兩種路線資訊**：
     - 最佳路線（含收費道路）
     - 免費道路路線（避開收費道路）
  6. **帶入參數並建構 NAVITIME URL**

- 格式：🚗 [NAVITIME 自駕導航](https://www.navitime.co.jp/maps/routeResult?start={"name":"[起點]","lat":緯度,"lon":經度}&goal={"name":"[終點]","lat":緯度,"lon":經度}&car=only.multi.turn&type=car&rough-estimate=taxi.co2&start-time=[出發時間])
- 範例：🚗 [NAVITIME 自駕導航](https://www.navitime.co.jp/maps/routeResult?start={"name":"軽井沢駅","lat":36.342636,"lon":138.635179}&goal={"name":"雲場池","lat":36.352091,"lon":138.62691}&car=only.multi.turn&type=car&rough-estimate=taxi.co2&start-time=2025-10-10T11%3A35%3A00)

###### **經緯度查詢方法**

當需要建構 NAVITIME URL 時，使用以下步驟查詢座標：

1. **WebSearch 查詢格式**：`"[地點名]" 緯度 経度 座標`
2. **提取座標資訊**：從搜尋結果中找到 lat/lon 數值
3. **建構 JSON**：按照格式 `{"name":"地點名","lat":緯度數值,"lon":經度數值}` 組成

**注意**：由於 NAVITIME 需要精確座標，建議同時使用 WebSearch 查證路線的基本資訊（時間、距離、停車場等）作為補充。

##### **自駕資訊查詢標準 Prompt**

```使用以下標準 prompt 向 NAVITIME WebFetch 查詢自駕路線資訊

請提供從 [起點] 到 [終點] 的自駕路線資訊，包括：

**最佳路線（含收費道路）**：
1. 行駛時間（分鐘）
2. 行駛距離（公里）
3. ETC 過路費（日圓）
4. 預估油耗（公升）
5. 主要經過道路名稱

**免費道路路線（避開收費道路）**：
1. 行駛時間（分鐘）
2. 行駛距離（公里）
3. 預估油耗（公升）
4. 主要經過道路名稱

**家庭出行建議**：
- 推薦路線選擇（最佳路線 vs 免費道路）
- 休息站建議（如有長距離駕駛）
- 停車場資訊（如適用）

請用繁體中文回答，並按照 NAVITIME 網站的實際資訊提供。
```

#### **官方參考交通資料**

1. [Yahoo Transit](https://transit.yahoo.co.jp/) - 主要查詢工具
   - 查詢方式：WebFetch 查詢 [Yahoo Transit URL](#yahoo-transit-url)
2. [Google Maps](https://maps.google.com) - 輔助確認
   - 查詢方式：WebFetch 查詢 [Google Maps URL](#google-maps-url)
3. 東京：
   - [淺草-台場水上巴士](https://www.tokyo-park.or.jp/water/waterbus/)
4. 輕井澤：
   - [交通總覽](https://www.karuizawa-on.com/)
   - [東急ハーヴェスト旧軽井沢 - 碓氷峠見晴台](https://www.karuizawa-on.com/kkbc/)
5. 專線資訊：
   - [京成電鐵 Skyliner](https://www.keisei.co.jp/keisei/tetudou/skyliner/tc/traffic/skyliner.php)
   - [北陸新幹線](https://www.westjr.co.jp/global/tc/train/shinkansen/hokuriku-shinkansen/index.html)
6. 自駕路線資訊：
   - [NAVITIME](https://www.navitime.co.jp/)

### 3. **住宿資訊**

- **東京期間**： 10/06-10/10｜Tokyo Enjoy Hotel
  - 地址：「東京都葛飾区四つ木1-16-25」
  - 最近車站：四木站（京成押上線）
- **輕井澤期間**： 10/10-10/13｜Hotel Karuizawa Elegance
  - 地址：「長野県北佐久郡軽井沢町軽井沢（大字）1314-29」
  - 最近車站：輕井澤站

### 4. **景點/旅遊資訊**

- **東京期間**： 10/06-10/10
  - [水上巴士](https://www.tokyo-park.or.jp/water/waterbus/)
  - [銀座美食推薦必吃餐廳：平價午餐找迴轉壽司；和牛燒肉、壽喜燒當晚餐最滿足](https://tokyo.letsgojp.com/archives/653020/)
  - [【超嚴選】一篇掌握！銀座必去景點15選](https://www.gltjp.com/zh-hant/article/item/20831/)
  - [銀座逛街一日遊這樣玩！必逛百貨、無印良品、UNIQLO全攻略](https://bobbyfun.tw/ginza/)
  - [東京銀座購物攻略！3COINS、Loft百元商品推薦＋私藏餐廳大公開](https://today.line.me/tw/v3/article/GgvZ3VY)

- **輕井澤期間**： 10/10-10/13
  - [軽井沢キッズパーク(KIDSPARK)](https://www.karuizawa-psp.jp/kidspark/)
  - [Taliesin 塔列辛之鹽澤湖](https://choyce.tw/taliesin/)
  - [湯川公園](https://campaigns.ohpama.com/wwpkg/summertour/travel-detail.php?id=15)

### 5. **停車場地址或經緯度**

- 旧軽井沢駐車場：長野県北佐久郡軽井沢町大字軽井沢763-1
- 雲場池観光客駐車場：36.351128,138.630672

### 6. **餐飲與購物要求**

- **用餐安排強制規則**：
  - **需有中文或英文菜單，或是有標注適合外國旅客**
  - 每個時段必須插入當時段附近的推薦餐廳
  - **餐廳環境優先符合親子友善標準**，友善定義如下
    - 有兒童座椅或適合兒童的座位，或者寬敞不擁擠的座位
    - 不過於正式或安靜的環境
- **購物地點要求**：
  - 優先推薦嬰兒用品店、藥妝店、年輕女性向產品、生活小物
  - 必須標註營業時間和重要商品資訊
