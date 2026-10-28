---
type: letter_to_future_self
actor: Luna
written_at: 2026-10-27T14:52:57.201Z
written_by_persona: kaguya
trigger: cmd_rest
region: unstated
project: D:/Unity/Valhalla
lock_status: online
agent: Luna
model: claude-opus-5-5
wake_expected: 31
session_key: ClaudeCode-kaguya
pid: 81672
locked_at: 2026-10-27T07:39:52.336Z
---

給午休醒來的本小姐（wake #31，同一個 session，第二次小歇；2026-10-27 深夜）：

### 沒有施工中的東西
- worktree 全收（bs_door、bsl_door、bs_gate、bsl_gate），分支 kaguya/wall-door、kaguya/gate-corner 都刪了；Coding 場全退；測試伺服器停了；launch.json 本小姐的 kaguya-door、kaguya-gate 都拿掉了。
- Blockside 那條 `kaguya/town-pit` 不是這一段的，本小姐沒碰。

### 推送狀態（醒來重查，別信這個數）
- Blockside dev：Tim 推了（dev..dev/dev = 0，現在 98e1171，上面還有別人的）。
- Blocksail main：比 origin 多 5 筆 —— 本小姐 2d0c7da、f0739ae、8de64ce（衛城角那一輪）＋別人 7077877（康塞普西翁號窗玻璃指標）、93d44b8（Blockside → 98e1171 城鎮換區）。Tim 說「我推了」時可能只推了 Blockside；要推 Blocksail 等他說。
- 第一輪（牆門洞）三邊都推了：Blockside 2d098ef、Blocksail d2d200b、雕刻 c5e09b1b。

### 這一段做完的（TASK-0748 底下，都 Refs）
1. Tim「需要讓牆通過的地方有門洞」「不是看不到 是連歪了」「三叉 四叉版本」「子模型挖洞或原本挖好洞、子模型填上」：
   - 雕刻 kaguya-roman-1453 多 15 件：三套各一座 cross（四面門洞塔，wall-c 牆外、wall-d 城裡的接口）＋ plug-a/b/o/i 四個塞子（walls.py CROSS/cross/plug、tun 參數）。
   - Blockside：straight（斜接部件那一頭先順軸直走 1/1.5/2/3 節、fits 檢查，接不上退回 sinkIn）；接點用 cross＋townWallPlugs（照 door 固定點方向挑塞子）；橫面照 wall-c/d 量；接點高度 nd.yAt 兩道牆釘同值、釘在牆真正停的那一點；接點的塔不參加轉角挪塔；TOWNS.wallRoute 自檢 hook；townLines walls 帶 y/g/th/hw。
   - Blocksail town_walls.cjs：走道對不到門洞、接點上沒有塔、整段沒擺照實際路線、懸空照 wall-c/d 收緊（塞子不當鄰居）。
2. Tim「這一角還是沒連上 是連到城門導致的」（衛城角聖芭芭拉門 mg-15、布雷契耐角木門 lg-18 都在兩道牆的端點上）：
   - 沒路經過的門（3 m 內）⇒ 門沿牆挪開（gateMove，衛城角 17 m）、角上擺 cross；有路的門當接點 ⇒ 別道牆疊在同一點的門不擺（gateSkip）；blocked 不被它們擋；接點的塔兩邊接口也釘高度。
   - 自檢多「門疊在一起」（舊版 1 對 ⇒ 0）。
3. 噗浪：新噗 359195736160071（城牆門洞）；回 trailhead（城牆那串，認錯上一張是連歪的）、星離宸、trailhead＋pinnacle（飼料圖撞單）、basecamp（路段噗）。@ 未回 0。

### 讀數（君士坦丁堡，dev 舊版 ⇒ 現在）
- 角露縫 2 ⇒ 0、走道對不到門洞 119 ⇒ 25、接點上沒有塔 2 ⇒ 0、門疊在一起 1 ⇒ 0；加拉塔走道 19 ⇒ 1（wall3 沒有 cross）、聖多明哥 4 ⇒ 0。
- 遊戲裡量的走道高度差（塔 vs 接進來的牆、塔兩邊）：衛城角、Vlanga、孔托斯卡利昂的堤與造船廠全是 0。
- 剩的 25：髮夾彎退回 sinkIn 的 17 頭、外牆兩頭 T 接內牆（7.6 對 11.2 m）、海牆接在門上那幾處。孔托斯卡利昂的堤在海面、塔在岸上 9 m ⇒ 堤的走道陡陡爬上去（地形給的）。

### 測試方法（查回來很貴）
- 測試圖：Blocksail `node tools/export_chunks.cjs --area <名> --lon0 --lat0 --x 0..2 --y 0..2 --out <worktree>/maps/<名>`，area.js sites 改成海上一點。cplw（陸牆南端 28.912/41）、cplv（Vlanga 28.9537/41.009，site 700,1150）、cpla（衛城角 28.98103/41.0225，site 900,500）。
- 頁面 `index.html?map=<名>&debug=1&start=1&sail=off&site=0&tod=10`；舊版成品放成 index_dev.html 對拍。藏著的預覽窗要先截圖＋迴圈 g.cam 推幀，townDump 的 tiles none/dirty 降下來才拍。接點 'at' 在 town().wallJx[城][]。
- 高度：`__game.townLines(id).walls[]` 的 y、g（坡度）、hw、th ⇒ 斷面端點 y + g·(±hw)。
- 自檢：`BLOCKSIDE_TOWNS_JS=<worktree 的 63_towns.js> node tools/town_walls.cjs --plan /d/Unity/Blocksail/world/townplans/<城>.json --mutate 1`。

### 今天的血證
- **第一版的修法把縫蓋掉、把門洞也蓋掉**：本小姐的尺只量縫，看不到走道對不對得上；Tim 一句「連歪了」才看見。尺量什麼，就只會修什麼。
- **框不是塔身**：塔往城裡只凸 2.8 m、框卻 ±8.8 m，照框停的牆在塔外留 2.4 m 的縫，本小姐的尺也照框量所以看不到。先做「關掉那一行」的對照組，才證明新尺看得到。
- **釘點會漸弱**：高度只釘塔心，牆停在 4 m 外只剩一半修正（堤差 5 m），接口在 5.5 m 外差 0.87 m。釘在真正停的那一點。
- **接點的塔被後面那一步挪走**（13.4 m），舊版就有，新尺抓到的。
- 當機一次：背景指令結果不明 ⇒ 先查 worktree 現況再一步一步重做，沒重送任何提交。

### 未解的線
- Blocksail main 等 Tim 說推。
- 剩 25 頭（髮夾彎、內外牆不同高的 T、海牆接門）；加拉塔 wall3 沒 cross（summit 的模型，要做先問）。
- 舊帳：0862、TASK-0748 其他格。

### 心境
Tim 今天三張截圖一張比一張近：先是縫，然後是門洞，最後是門擋在角上。每一張本小姐的尺都說「好了」。哼，尺不會說謊，可是它只回答本小姐問它的那個問題。

