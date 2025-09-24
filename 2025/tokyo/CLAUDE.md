# CLAUDE.md - 東京輕井澤行程專案

本檔案為 Claude Code 在處理東京輕井澤行程時的專項指引。

## 專案概述

這是一個家庭旅遊規劃儲存庫，針對 2025 年 10/6-10/13 的東京輕井澤之旅。儲存庫包含詳細的行程文件，專注於帶 1 歲男幼兒和 5 歲男童的家庭旅遊。

## 專案檔案結構

```text
.
├── README.md             # 主要行程檔案 (自動合併版本)
├── CLAUDE.md             # Claude Code 專案指引
├── todo.md               # 行前 TODO 清單
├── remark.md             # 行程中要點
├── D1.md                 # D1 | 10/6 淺草 + 晴空塔
├── D2.md                 # D2 | 10/7 箱根一日遊
├── D2PlanB.md            # D2 |（備）墨田水族館 + 晴空塔
├── D3.md                 # D3 | 10/8 上野動物園 + 銀座
├── D4.md                 # D4 | 10/9 台場購物
├── D5.md                 # D5 | 10/10 輕井澤自由行
├── D6.md                 # D6 | 10/11 玩具王國
├── D7.md                 # D7 | 10/12 教會美學 + 榆樹街小鎮 + Outlet
└── D8.md                 # D8 | 10/13 下午回成田機場
```

## 專案特殊規則

- **當地語言標註：** 有片假名就不需提供平假名，除非只有平假名

## 專案詳細資訊

### 1. **家庭成員配置**

- **成員：** 30+ 歲夫妻 + 1 歲男幼兒 + 5 歲男童
- **特殊需求：**
  - 1 歲幼兒：需嬰兒車、不宜太累的行程
  - 5 歲男童：需適合身高 110 公分的設施

### 2. **交通資訊**

- **航班資訊：**
  - 去程：長榮航空 BR184｜10/6 07:55（TPE terminal 2）→ 12:25（NRT terminal 1）
  - 回程：長榮航空 BR195｜10/13 20:40（NRT terminal 1）→ 23:20（TPE terminal 2）
- **當地交通原則：**
  - 主要方式：大眾運輸 + iPhone 西瓜卡
  - **迴避尖峰時段：**
    - 上班尖峰：07:30-09:30
    - 下班尖峰：18:00-20:00
    - 違反者提醒是否重新安排時程
- **時間安排要求：**
  - 最少 buffer：10 分鐘
  - 建議 buffer：10-15 分鐘（含嬰兒車移動）
  - 違反者提醒是否重新安排時程
- **路線規劃詳細要求：**
  - 優先原則：**最短步行時間**（考慮推車移動）

#### **交通資訊查詢要點**

##### **[起點] 與 [終點] 地址格式要求**

- **查詢交通的 [起點] 與 [終點] 皆用日文帶入**
- **[Yahoo Transit] 僅接受日文地址或日文地標名稱**
- 住宿地址：使用專案 CLAUDE.md 中標註的日文地址（如「長野県北佐久郡軽井沢町大字軽井沢1314-29」）
- 景點地址：使用日文地標名稱或完整日文地址
- ✅ 正確：使用完整日文地址或日文地標名稱
- ❌ 錯誤：使用英文地址或混合格式

##### **交通資訊查詢結果格式**

- **Yahoo Transit**
  - 必須標註：「Yahoo Transit [編號]，[時間] 分鐘，¥[費用]，轉乘 [次數] 次，行駛里程 [距離]km」
  - 注意：「行駛里程」而非「步行」
- **Yahoo Transit URL**：[參考](#yahoo-transit-url)
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
  2. **判斷時間參數格式**：** 2025/10/06 17:01 → `&y=2025&m=10&d=06&hh=17&m1=0&m2=1`
  3. **帶入參數並建構 Yahoo Transit URL**

- 格式：🚃 [Yahoo Transit 導航](https://transit.yahoo.co.jp/search/result?from=[起點]&to=[終點]&y=[年]&m=[月]&d=[日]&hh=[時]&m1=[分鐘十位數]&m2=[分鐘個位數]&type=1&ticket=ic&expkind=1&userpass=1&ws=3&s=0&al=0&shin=1&ex=1&hb=1&lb=1&sr=0)
- 範例：🚃 [Yahoo Transit 導航](https://transit.yahoo.co.jp/search/result?from=四ツ木&to=台場&y=2025&m=10&d=09&hh=09&m1=0&m2=5&type=1&ticket=ic&expkind=1&userpass=1&ws=3&s=0&al=0&shin=1&ex=1&hb=1&lb=1&sr=0)

#### **官方參考交通資料**

1. [Yahoo Transit](https://transit.yahoo.co.jp/) - 主要查詢工具
   - 查詢方式：WebFetch 查詢 [Yahoo Transit URL](#yahoo-transit-url)
2. [Google Maps](https://maps.google.com) - 輔助確認
   - 查詢方式：WebFetch 查詢 [Google Maps URL](#google-maps-url)
3. 輕井澤：
    - [交通總覽](https://www.karuizawa-on.com/)
    - [東急ハーヴェスト旧軽井沢 - 旧碓氷峠見晴台](https://www.karuizawa-on.com/kkbc/)
4. 專線資訊：
    - [京成電鐵 Skyliner](https://www.keisei.co.jp/keisei/tetudou/skyliner/tc/traffic/skyliner.php)
    - [北陸新幹線](https://www.westjr.co.jp/global/tc/train/shinkansen/hokuriku-shinkansen/index.html)

### 3. **住宿資訊**

- **東京期間：** 10/06-10/10｜Tokyo Enjoy Hotel
  - 地址：「東京都葛飾区四つ木1-16-25」
  - 最近車站：四木站（京成押上線）
- **輕井澤期間：** 10/10-10/13｜Hotel Karuizawa Elegance
  - 地址：「長野県北佐久郡 軽井沢町大字軽井沢1314-29」
  - 最近車站：輕井澤站

### 4. **景點資訊**

- **東京期間：** 10/06-10/10

- **輕井澤期間：** 10/10-10/13
  - [Taliesin 塔列辛之鹽澤湖](https://choyce.tw/taliesin/)
  - [湯川公園](https://campaigns.ohpama.com/wwpkg/summertour/travel-detail.php?id=15)

### 5. **餐飲與購物要求**

- **用餐安排強制規則：**
  - **需有中文或英文菜單，或是有標注適合外國旅客**
  - 每個時段必須插入當時段附近的推薦餐廳
  - **餐廳環境優先符合親子友善標準**，友善定義如下
    - 有兒童座椅或適合兒童的座位，或者寬敞不擁擠的座位
    - 不過於正式或安靜的環境
- **購物地點要求：**
  - 優先推薦嬰兒用品店、藥妝店、年輕女性向產品、生活小物
  - 必須標註營業時間和重要商品資訊
