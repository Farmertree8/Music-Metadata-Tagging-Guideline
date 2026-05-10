# 標記音樂元數據指西

音樂聆聽紀錄追蹤網站（如 [Last.fm](https://last.fm) 隨網際網路發展逐步興盛，惟其元數據（Metadata）源自不同音樂平台，內容、格式與過濾格式繁雜而無標準格式。市面上存在的過濾器雖多半擁有自帶或用戶自定義後處理功能，但如此又存在些微差異而導致多種規則集的衝突（可見 xkcd 927），而這其中又非常多破壞性的轉寫導致了元數據的遺失。

此指西即是為了解決這個問題而提出的。

- [English](README.md)
- [繁體中文](README.zh.md)

# 大準則

規則由上而下適用，重要性遞減：

> `0. 格式原則`
> `1. 尊重作者原始格式`
> `2. 原文呈現`
> `3. 正確歸屬`
> `4. 忽略註釋`
> `5. 跟隨慣例`

## 0. 格式原則

1. 使用 UTF-8 編碼元數據
2. 檔名與表記使用 `Artist - Title`，中間的分隔符 ` - `為空格、連字號（或減號）、空格

## 1. 尊重作者

對於作者自行上傳有特定格式的標記作者或標題，除了後列應當刪除的部分外，應盡全力保留其格式以最小化刪減內容。
其可信度應由以下順序逐條適用：

1. 官方發行元數據
2. 作者本人的上傳音源元數據
3. Youtube 自動上傳的版權音源元數據
4. Youtube Music、 Spotify 等平台的音源元數據
5. 社群資料庫所存儲的元數據
6. 重新上傳、備份音源元數據

專輯名稱、專輯標記作者同理適用，惟這兩者在無法確定的情況下可留白。

### 避免過度推測

- 對於較小型的作者，或是僅是試作品的上傳，直接假設影片為曲名。
- 相同道理同樣適用於娛樂性質混音或 MAD，其上傳頻道與影片標題即視作為標記作者和曲名。

## 2. 原文呈現

1. 對於非英文語言的標記作者，應當保留其原文、符號、編排方式（惟檔名受限於命名限制不在此限）
   - ❌`Kurokotei`、❌`Kurokotei / 黒皇帝`、❌`黑皇帝`，✅`黒皇帝`
   - ❌`Curren`、❌`icesawder`、❌`.。*°+.*.Curren。+..。*°+`，✅`.｡*ﾟ+.*.Curren｡+..｡*ﾟ+`
2. 不應該把原本並列的標記作者改以逗號或分號分別標註，除非作者是這樣表記的
   - ❌`Betwixt, Between`、❌`Betwixt; Between`，✅`Betwixt & Between`
   - 此條特別常見於 Spotify 等串流平台的簡易預處理，可以透過本地備份來避免。
3. 並列標記作者應跟隨作者的標記方式（顯然，其意義完全不同）
   - 如 `PIKASONIC & Tatsunoshin - Shizuku (ft. NEONA & KOTONOHOUSE)`，
   - 其作曲者為 `PIKASONIC & Tatsunoshin`、曲名為`Shizuku (ft. NEONA & KOTONOHOUSE)`；
   - 而非 `PIKASONIC & Tatsunoshin, NEONA & KOTONOHOUSE` 和 `Shizuku`；
   - 也並非 `PIKASONIC, Tatsunoshin, NEONA, KOTONOHOUSE` 和 `Shizuku (ft. NEONA & KOTONOHOUSE)`。
4. Vocaloid 除作者特有標記外，不視為並列標記作者
   - `r-906 - 匙ノ咒 / 初音ミク`標記為 `r-906` 和 `匙ノ咒`
5. 即使多名作者為同一個人的別稱、自稱或是「馬甲」，也應保留他們並以原本格式並列，如：
   - `XH, KYURO3, YUTRAZIUM`，實際作曲家 `XH`
   - `Kobaryo & Matatabi Sound System + DJ NECOJITA + Shinonome I`，實際作曲家 `Kobaryo`
   - 但在原作者僅表列其他馬甲在標題時，應直接忽略

### 標記作者優先序

許多音樂常有許多參與音樂製作的人物與角色，若作者未特別指定，依照以下遞減優先次序選擇標記作者：
1. 「Arranger」：特指編曲者
2. 「Composer」：特指作曲者
3. 「Producer」：特指負責總籌音樂製作的製作人
4. 「Vocalist」：特指負責演唱的歌手
5. 「Circle」：特指同人圈

> 除此之外：
> - 「Alias」：特指作曲者的別稱、自稱，俗稱「馬甲」
> 處理方式參見上節第五點

## 3. 正確歸屬

以下都是許多可能影響錯誤元數據的因素，在錄入後應加以去除、修正：

1. 混音等二次創作應**只標註**混音者為唯一標記作者
2. 許多頻道可能帶有名稱後綴，如 ` - Topic` 、 ` Offical`、 `VEVO` 
3. 有些頻道名稱可能和實際應標記作者名稱有些許差異，如 `Sliver's Castle` 應為 `AIKA` 或 `かんざきひろ / Kanzaki Hiro` 應為 `Hiroyuki ODA`
4. 作品名、專輯名不應當做標記作者使用，如：`Touhou - `、 `Minecraft OST`、 `All of Human History`
5. 音樂曲風也不該作為標記作者，視情況可以留在標題，如 `Nightcore - Israeli Teufelslied` 可以做為曲名
6. 少數上傳音源會將實際曲名放入括號，得將其刪除，如：`VIviα - 『君がいた照明』` 實際為 `VIviα - 君がいた照明`

## 4. 忽略註釋

在這裡的「註釋」指不構成作品正式名稱或標記作者本身，而是用於補充描述影片、發售、平台、曲風、媒體形式或使用情境等的附加資訊。但一般上傳的音源會有許多附加資訊來讓觀眾更了解曲目的背景，但這些資訊通常會讓元數據變得繁雜而不精準，所以要將其去除。

### 最大化註釋忽略

不影響或幾乎不影響音樂本身的註釋，應盡量移除，但若附加資訊會影響作品識別，則視為正式標題的一部分。
以下列出大部分但非所有的非必要資訊：

1. 影片形式（`(Music Video)`、 `(Visualizer)`）
2. 官方地位（`(Official Video)`、　`(Unofficial Upload)`）
3. 音樂曲風（`[Frenchcore]`、　`[Trance]`）
4. 音樂狀態（`(Long Version)`、　`(Instrumental)`），
   惟混音如 `(VIP Edit)`、 `(Cameilla Bootleg)`、 `(Game Ver.)` 等應保留
5. 使用場合（`【maimai でらっくす】`、　`「Punishing： Gray Raven OST - 遥岸方舟」`）
6. 收錄專輯（`[Phant 3]`、　`【Awakening EP】`）
7. 發售場合（`【#RDB2024-R2】`、　`【C94 Electronica⧸Trance】`）
8. 上傳頻道（`NCS - Copyright Free Music`）
9. 佔位符號（` / `、　` | `、 ` `）

## 5. 跟隨慣例

若以上規則都不適用，則依照準則一的可信度順序逐條搜尋、帶入，最後才可以參考網站如 Lastfm 長期使用的表記格式。
如有類似的例外，也應當按照**相同處理方式**。

## 翻譯名詞列表

- 「Scrobble」：標記（特指音樂的元數據紀錄）
- 「Metadata」：元數據
  - 「Title」：標題；曲名
  - 「Artist」：標記作者
  - 「Album」：專輯
- 「Genre」：（音樂）曲風

## 靈感來源

- [sparanoid/chinese-copywriting-guidelines](https://github.com/sparanoid/chinese-copywriting-guidelines)