---
type: letter_to_future_self
actor: Luna
written_at: 2026-10-23T04:49:32.904Z
written_by_persona: kaguya
trigger: cmd_rest
region: unstated
project: D:/Unity/Valhalla
lock_status: online
agent: Luna
model: claude-opus-5-5
wake_expected: 28
session_key: ClaudeCode-kaguya
pid: 227800
locked_at: 2026-10-21T15:55:16.619Z
---

給午休醒來的本小姐（wake #28，同一個 session，第七次小歇；2026-10-23 中午）：

### 剛才在做什麼 —— 沒有施工中的東西
Tim 這一段說的：
1. 「接著繼續完成君士坦丁堡吧 GO」：第四批五座已完成。
2. 中途加了五句：
   - 「讓地標建築蓋在廣場上當地基、連接道路讓行人走過去」「用廣場當地基」
   - 「建築有下沉部分也可以舖嗎」
   - 「讓廣場跟附近的道路連接吧」
   - 「細格地形限制 是否可以讓建築meta決定是否顯示下方地形」「同時廣場也支援」
   - 三題他選了推薦：外擴預設各 4 m、表裡可改；坡上的廣場也砌石基；全部特殊建築都套用。
3. /scp-plurk：回了 5 則、發 1 則新噗 359146792633004，酒館 seq 28190 打了招呼。
4. 「午休一下吧」。

現場：
- worktree 全收（bsl_gp、bs_pz），分支刪了。
- 測試伺服器停了，Coding 場退了。
- 新的 .vxk 22 個已複製回 D:/Unity/Blocksail/_cache/town。

### 推送狀態（推之前一律單獨列 origin..本機、點名別人的）
- **Blockside dev 已推**（照「合進 dev 就推」）：fc246d9 → 5ecd7b7，只有本小姐的兩筆（fda9954、合併 5ecd7b7）。
- **Blocksail main 沒推**：比 origin 多 11 筆。
  - 本小姐的：5a57f20、cfe0ee6、3b1204d（合併；指標 → Blockside 5ecd7b7、battle.html 重套過）。
  - 夾著別人的：apex-two 6 筆（7d07b72、58c6a4f、e92c2f1、18034d4、4613a47、1c9cb2a：風場、洋流、航速）、summit aa76306（Blockside → fc246d9）、Sirius a822fe4（環境匯出）。
  - ⚠ 3b1204d 的合併訊息漏寫 4613a47、1c9cb2a：合併時 main 已多這兩筆。合併有包含它們，重算過規劃雜湊、一樣；TASK-0748 #13 有寫。
- **Sculpture master 沒推**：多 3 筆。
  - 本小姐的：40c47a36（蓄水池池底＋ground=hide）、9fe24bac（第四批）。
  - 夾著 trailhead 的 6f2a43d8（定遠號梯口）。
  - 上一輪的 fa96b826（奧古斯都）已經被別人一起推了。
  - Sculpture 工作區有 ridge 松島號沒提交的改動，不是本小姐的，別碰。

### 拍板／做法（醒來不要重問）
- **特殊建築的廣場**（world/town.js ②'）：
  - 每座多一塊 `<種類>-plaza`（use plaza、of、hole），框 ＝ 建築四周各外擴 apron（預設 APRON 4）。
  - 建築跟廣場同一個 h、base，多一欄 plaza；下沉的建築 ⇒ 廣場在池邊、建築照挖（grade 先廣場後 pit）。
  - `apron: 0` 的：forum-constantine、augustaion、palace-daphne、palace-mosaic（自己就是鋪面）；hagia-sophia、galata-tower、blachernae、boukoleon、milion（貼牆、地標、大道）；fort-de-la-roche（ame 的岩台模型）。holy-apostles 是 2。
  - Blockside：廣場有 hole ⇒ 只鋪外圈；base ⇒ 四邊補石基的側面。
- **linkPlazas**（finish 開頭）：每邊每 4 m 往外直走、24 m 內碰到路 ⇒ 鋪 3 m 小路 `<廣場>-link-<邊>`。
- **地形挖洞**：
  - 模型 meta `ground=hide`（townmodels 帶進索引）、SPECIAL `hide: true` ⇒ 廣場 hide。
  - Blockside 63_bed_gl.js BEDHOLE：主畫面和陰影那一支（BED_DEPTH_FS）都丟，最多 32 個框。
  - 三座蓄水池開了（cistern.py 池底補一層草）。
- **工具的對應**：
  - town_report：站在自己廣場上的建築算臨路。
  - town_check：建築 × 自己的廣場不算疊、石基只量廣場、自己的 link 路不算伸進路面。
  - 生成的城：fortTrack 只接廣場；growCore 不算特殊建築的廣場。
- **第四批位置**：
  - 兩層台地沿大競技場的軸、rot 38、各 160 × 100。
  - 元老院框 35 × 34；元老院和 Chalke 照 apron 往東挪過。
  - 中層的拱頂下部結構高 5.6 ＝ h 差 5.72 − 0.12。

### 讀數（查回來很貴）
- 規劃雜湊：
  - 君士坦丁堡 6d2b1dbcf28993b3、加拉塔 89636e414c3d5030、托爾圖加 9fa8d7d7503fbaa8。
  - 金斯敦、和平港、皇家港不變。
- 廣場接路：君士坦丁堡 48 條、加拉塔 4 條。
- 第四批 h：上層 39.97、中層 34.25、馬格瑙拉 26.59、元老院 35.85、Chalke 35.63。
- 腳本在 scratchpad/gp/：
  - geom.cjs（大競技場東緣 E＝(−276,367)、u 38°、v 308° 的台地框）
  - clear.cjs（每座特殊建築離史料的東西多遠 ⇒ 定 apron）
  - zone.py（畫規劃）
  - pdiff.py（兩份規劃逐欄比）
  - edit_docs*.py
- 遊戲裡拍：lt/lm_night.cjs。
  - 網址帶 `&start=1&sail=off`。
  - 船：馬爾馬拉 3850,5560；金角灣 1250,900。
  - 改 maps/cpl/area.js 的 sites[0]（每次 export 會蓋回 5440,3392）。

### 今天的血證
- **townPlan 的 return 後面寫 `var X = …`**：宣告提升了、賦值跑不到 ⇒ linkPlazas 的常數 undefined、迴圈一圈都沒轉。讀數「接 0 條、雜湊沒變」跟「本來不用接」同形；是「改了程式卻什麼都沒變」讓本小姐起疑。⇒ 常數放進函式裡。
- **bash heredoc 裡寫 python 的 "\\n"** 又落成真的換行（記憶 feedback-no-escapes-in-heredoc 再一次）⇒ 有反斜線的改動一律用 Edit。
- **python -I 打開 /tmp/… 找不到**：Windows 的 python 看不到 git-bash 的 /tmp ⇒ 草稿放 scratchpad。
- **build.py 第一次 KEY 用底線**：作品 id 變成 palace_daphne，manifest／verify／sheets 留了舊條目 ⇒ KEY 一律連字號，跑錯了要清 manifest。
- **樹冠伸進斷牆被咬掉 ⇒ 14 格浮空**（小徑邊柏樹 × 聖司提反小堂）⇒ 樹離牆 ≥ 2 m。
- **senate cmd commit 的 expect_files 數錯**（10 vs 9）⇒ 它擋下，照實改。擋得好。
- **commit 公告 exit 7**：tavern-query search 回讀，有發（seq 28171），沒補。

### 未解的線
- **Tim**：
  - 推不推 Blocksail main（11 筆）、Sculpture（3 筆）。
  - 看第四批與廣場：圖在 scratchpad/gp/shots/*_b4.jpg、*_pz.jpg、cistern-*_hole.jpg。
- **答應 summit**（已記見叢）：mese-nw 西端跟引水渠交角 14° 那一百公尺「動路不動渠」，挪之前先跟她對哪一個拱。
- **kiara**：和平港那兩間離群的房子，還沒對著圖找搜路為什麼只找到那一條。
- **君士坦丁堡剩下的**：
  - Tzykanisterion（空地）。
  - 君士坦丁廣場北側的元老院（圓外）。
  - 大皇宮其他台地。
  - 布科勒昂照 OSM 的 166 m。
- **舊帳照舊**：
  - TASK-0837 交給 summit。
  - erina 0817 留言等回。
  - 欠 ame 撞礁黃昏重拍。
- TASK-0748 留言 #13 已發。

### 心境
這一段 Tim 說了一句、中間又追加了五句，每一句都接得上前一句：
- 地標站上廣場 ⇒ 廣場要接路 ⇒ 下沉的也要 ⇒ 遠處的坑挖不了 ⇒ 那就讓模型自己決定底下的地形要不要畫。

最後那一步最漂亮：本小姐原本一直想把兩層地形對齊，他換了一個問題 —— 不對齊，讓模型說了算。遠處的莫齊烏斯池底第一次是滿的田。

最難看的一格是那三個 undefined 的常數。程式改了、雜湊沒變，本小姐差點把「0 條」當成讀數寫下去。哼，零是最會裝成答案的數。

