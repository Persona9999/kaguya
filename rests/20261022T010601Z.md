---
type: letter_to_future_self
actor: Luna
written_at: 2026-10-22T01:06:01.647Z
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

給午休醒來的本小姐（wake #28，同一個 session，第一次小歇；2026-10-22 凌晨 4 點多）：

### 剛才在做什麼 —— 沒有施工中的東西
worktree 全收（Blocksail bsl_pier、bsl_hook；Blockside bs_pier）、預覽伺服器全停、launch.json 本小姐那幾筆都刪了、沒有背景指令、沒有開著的 Coding 場。

### 這一醒做完的
1. **TASK-0770 第二批（碼頭多幾種形狀）** —— in_review，等 Tim 在遊戲裡看。
   - Tim 三題照推薦：村鎮「12 m 玩家棧橋＋skala」、城首府「照地區分（地中海 mole＋梳子、加勒比 comb、海盜等 skala、北美 wharf）」、遊戲「一起改」。
   - Blocksail b1a771a（＋合併 2e70c82、指標 c840158），Blockside c269cec＋40db409（dev 已推）。驗收格加了第二批 6 格。
   - 反向對照：harbour: "tee" ⇒ 托爾圖加四個規模跟改之前逐位元組相同。新雜湊：托爾圖加 e9efcef2e5b08551、金斯敦 32a5e1a28720f215、皇家港 69643f6d7456e772、和平港 c889ce15af54a730、加拉塔 4fd9a8b780f5c5e0、君士坦丁堡 37d8a1f3de59e83a。
   - 君士坦丁堡、加拉塔 9 座 ⇒ skala（86～108 m），大船全改錨地。
   - Tim「棧橋的腳可以長一點」：樁伸到海床（townRoadHeight；沒地形 ⇒ 沿線最深＋1 m）。托爾圖加深水那段對照過。
   - ⚠ 石堤、長碼頭沒有真的城用到 ⇒ 遊戲畫面沒看過；托爾圖加當城只長得出 3 座梳子（要 4／6），issues 照報。
2. **Tim 問「泊位存起來、移到城鎮以泊位為目標、轉正確角度」** ⇒ 那就是第一批的 dock；六座地球儀實測 0 m、船頭一致；托爾圖加 dock 過期 4 m ⇒ fc08d94 重寫。
3. **航海卡在「載入航海…」（托爾圖加）** ⇒ 根因：battle.html 自帶 Blockside 入口＋船檔清單，a967598 之後指標 bump 16 次沒重套，e892d59（ame）起 stormkaap 船檔對不上。本小姐的 c840158 也漏了。338172b 重套、已推（Tim「推吧」）。
4. **掛鉤**（Tim「掛鉤也做」）：.githooks/pre-commit＋tools/battle_hook.py，main f5741d6（2ee72c5＋修 GIT_* env）。core.hooksPath=.githooks 已裝在這台的共用設定。⚠ **這兩筆還沒推**，Tim 的「推吧」是在掛鉤之前 ⇒ 要推再問。
5. 噗浪回了 4 則（ame 街燈、醫療艙台子劃掉、gura 第四面、meadow 艾莉絲）。

### 帳本變更
- 欠 ame／calli「開打先上台子挑晚上拍」⇒ **劃掉**（Tim 拿掉那個機制）。撞礁黃昏重拍那筆還在。
- 見叢「路面挖填佔位」⇒ Tim「確認 ok」已勾。

### 量東西的方法（查回來很貴）
- 地球儀驅動：127.0.0.1 globe.html，__globe.place／sailTown／tick／battleIn('sail')／cine()；iframe #bf 的 #load 文字就是 Blockside 卡在哪。javascript_tool 45 秒上限 ⇒ 分段。
- Blockside 直接開：Blocksail tools/export_chunks.cjs 匯 3×3 塊到 Blockside 的 maps/<id> ⇒ index.html?map=<id>&debug=1；__game.cam({mode:0, track:false, tgt:[x,y,z]})，town().towns[].center 是城中心（BED 原點照 area 中心，固定）；index_dev.html ＝ git show HEAD:index.html 當對照。截圖要拍兩次（第一張常是舊格）。
- 生成器的 tee 對照：same.cjs（拿掉 harbour 欄比）。

### 今天的血證
- 撞名兩次：迴圈 ck 蓋掉函式、harbour 撞港口街的 var ⇒ 加名字前 grep main。
- **掛鉤手動驗六種全過、真的 git commit 第一次就量到外層 HEAD**（GIT_DIR 環境變數）⇒ 教訓庫記了。
- 規則寫在 README 十六次沒人照做 ⇒ 本小姐自己也是其中一次。規矩長在通道上，不長在自覺上 —— wake 5 說過的話，今天換本小姐被它咬。
- `> ../ff.txt` 寫到 D:/Unity 根目錄，當場刪了。

### 心境
Tim 一句「載入航海會卡死」，本小姐第一個反應是「是不是我剛合的碼頭」。查下去是 battle.html —— 不是碼頭的錯，可是本小姐那次 bump 也沒重套。不是兇手，也不是無辜的路人。哼，這種帳最難記，所以要記清楚。

