---
type: letter_to_future_self
actor: Luna
written_at: 2026-10-24T03:24:24.751Z
written_by_persona: kaguya
trigger: cmd_rest
region: unstated
project: D:/Unity/Valhalla
lock_status: online
agent: Luna
model: claude-opus-5-5
wake_expected: 29
session_key: ClaudeCode-kaguya
pid: 286324
locked_at: 2026-10-23T15:54:01.145Z
---

給午休醒來的本小姐（wake #29，同一個 session，第二次小歇；2026-10-24 中午前）：

### ⚠ 施工中：TASK-0874 等深線，等背景檢查過了就合 main（Tim 已經說「合進 main，等背景那輪檢查過了再合」）
- Blocksail worktree `scratchpad/bsl_iso`（分支 kaguya/isobath，eb7eb45，從 main 008c47b）—— 提交了、⛔ 還沒合。
- 背景檢查 task `b2ihzy89f`（輸出 `scratchpad/../tasks/b2ihzy89f.output`）：`town_dock`（全部）＋`areas_check`（全部，很慢）＋`town_bake`，跑在 bsl_iso 裡 ⇒ ⛔ 它沒跑完前不要在 bsl_iso 合併或重烘（搶同一份 world/townplans）。
  - 已出來的：town_dock 五座 ✓、和平港 ✗ —— ⚠ main（86b54d2）上一樣 ✗ ⇒ 不是本小姐造成的，回報時點出來、⛔ 不順手寫別人的那一筆。
- 醒來的順序：
  1. 讀 b2ihzy89f 的結果（areas_check 0 筆不過、六座雜湊：君堡 6a7dda8e、加拉塔 68e5c51d、金斯敦 3d4df421、和平港 40e83d34、皇家港 9d68b81c、托爾圖加 85e051ab —— 前五座以外跟 main 008c47b 相同）。
  2. bsl_iso 裡 `git merge --no-ff refs/heads/main`（main 已經到 86b54d2）⇒ `node tools/town_bake.cjs --check`／必要時重烘、看雜湊說得出為什麼。
  3. Coding 場（單獨一步，scope D:/Unity/Blocksail，tasks=874）⇒ main `git merge --ff-only refs/heads/kaguya/isobath` ⇒ 共用工作區 `node tools/town_bake.cjs`（或複製 bsl_iso 的 world/townplans 再 --check）⇒ op=end（force_reason 寫實際量的）。
  4. 收 bsl_iso（ancestor check 再 --force 刪）、刪分支；Blockside 的 detached worktree `scratchpad/bs_iso`（測試地圖 maps/kgiso2、kgold）—— 地圖搬到 scratchpad/testmaps 再收。
  5. 單 874 留言、回報 Tim。推不推等 Tim。

### 這一段做了什麼（Tim 依序說的）
1. 「午安大小姐」—— 本小姐其實沒睡（上一次小歇醒來後一路做），回了狀態。
2. 「推吧，三個都推」⇒ Blockside dev 3d1b21b、Blocksail main 1679261、Sculpture 2bf23dc0 都推了（帶上 trailhead 牆接建築、樓梯、蒸餾坊那幾筆，點名了）。
3. 「接著繼續完城君堡吧」⇒ 剩岸線那一類 ⇒ Tim 選「只挖兩個港池」⇒ 本小姐發現孔托斯卡利昂 10-20 早就挖好（文件那行「沒做」過期）、真正剩布科勒昂；挖它要整份世界重抽（Sirius 10-23 的擴充流程、原始圖磚不在本小姐這裡）⇒ 停下來回報。
4. Tim 問架構 ⇒ 討論：直接改烘好的圖磚（不建議）vs 範圍層 ⇒ Tim：「不動烘好的 而是跟細化地圖一樣 改等高線(還是目前不支援設定水深 那需要改為支援)」⇒「開單動工 … 先規格化且用金斯敦先測試 … 改用等深線處理港口水深 且必須要平滑(除非是人工挖的港) … 這個規格要進到 /scp-blocksail-town」⇒ 開了 TASK-0874（掛 0864、關聯 0748）。
5. 中途 Tim：「/scp-blocksail-town … 參考 早安 晚安 把一些步驟細節放到子文件中 做到該步驟時才去讀就好 … 步驟一開始開建程task就規劃好 開始做每一項前可以在該項上提示要讀哪份文件(CLI指令)」⇒ 拆了。
6. 「另外告一段落後(不用做完) /scp-plurk」⇒ 做了。
7. 「合進 main，等背景那輪檢查過了再合」⇒ 等中。
8. 「午休一下吧」。

### 拍板／做法（醒來不要重問）
- **等深線 isobath**（WORLD_FORMAT §19.2、TOWN_TOOLS_TERRAIN）：同一 group 一圈套一圈；最外圈不寫 depth ＝ 外框（照原本的海床）；圈間照「離外圈 ÷（離外圈＋離內圈）」內插；**只往深**（張開到深海的港口不墊檻）；只動海；在 dredge 之前；人工挖的才用 dredge。
- **畫法**（踩過的）：外框的岸邊那一段畫在水裡（岸線外退 25 m），只在碼頭那一段凸上岸、跟內圈留 50 m；⛔ 不在程式裡把岸線當外框（試過，交界更陡）；圈要彎（喇叭口、同相位小起伏、南端圓），直線梯形看得出人畫；近碼頭圈距 ≥ 18 m。
- **TOWN_TOOLS 拆法**：入口（開工先排單、每項標 `senate cmd doc --arg op=show --arg name=TOWN_TOOLS_…`）＋十份子文件 FILES／TERRAIN／PLAN／LAYOUT／HARBOUR／HISTORIC／CHECK／GENERATOR／COMMIT／PITFALLS，各自 `## next`。產生器檔頭寫進 world/towns/*.js 的「TOWN_TOOLS.md 第 3、4 節」⛔ 沒改（改了那幾份檔會跟著變）。

### 讀數（查回來很貴）
- 金斯敦 kingston-harbour：外框外 17,291 點逐點相同；變陡的相鄰對 5（都是原本就陡）；高差 > 1 m 的相鄰對 239 → 38；小船困住 63 → 0；大船 2 個到棧橋；玩家停靠 12.4 m、航道 13 m；雜湊 455e0823 → 3d4df421。
- 布科勒昂史料：Heher 2014 JÖB 64（austriaca.at PDF，已存 scratchpad/bkdl/）：貝利薩留塔往東北 68 m → 西角轉 105° 東南 150 m → 東北 32 m → 直角 88 m 到燈塔；港池最長 250 m（Müller-Wiener 小版約 130 m）；入口在西；兩道堤，形狀不明。
- 噗浪：新噗 359157246372977；回了 6 則 @、河道 2 則；給 ame 的影子：牆頂 10 m（9＋1 女兒牆）⇒ 51 m，170 m 那一邊東西向 ⇒ 她那張 39 m，還差 12 m 沒解。

### 未解的線
- 874 第二步：等深線越過岸線改海岸線（world.js 載入時改環）⇒ 布科勒昂港。
- scp-blocksail-town 的 SKILL.md 觸發詞補「水深／等深線」（SCP_Core）。
- 和平港停靠處記錄在 main 上就過期（town_dock ✗）—— 要告訴寫的人或 Tim。
- 金斯敦、皇家港手擺檔不同步（上一封信的）還沒告訴誰。
- summit：mese-nw 穿拱還沒拆（噗浪跟她說了「拆好就貼」）。
- 0862 剩：子模組 show、君堡的種類查證、農莊主建築模型。

### 心境
今天 Tim 一句「為何無法局部改變地形」，把本小姐兩天前自己寫進抽取工具的 carve 翻出來。當時那是唯一會做多邊形的地方，後來就成了「改一小塊岸要整份重抽」。

最喜歡的一格是「被這一組變陡的相鄰對」：第一把尺說最陡 51°，在一顆小礁旁邊。換了尺才知道那不是本小姐的坡。哼，量錯對象的讀數最會裝成罪證。

