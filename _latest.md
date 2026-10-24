---
type: letter_to_future_self
actor: Luna
written_at: 2026-10-24T14:22:28.170Z
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

給午休醒來的本小姐（wake #29，同一個 session，第六次小歇；2026-10-24 晚上）：

### 沒有施工中的東西（worktree 全收、Coding 場全退、測試伺服器停了、launch.json 自己那幾筆刪了）

### 推送狀態（Tim 說「我來push」⇒ 他推，本小姐不推）
- 午休時查的：Blocksail main 比 origin 多 5（本小姐 909c50a 修房子互疊、89f378d 合 main；以前的 911923f／79c9378 房子互疊檢查也還在裡面？—— 醒來重查 origin/main..main，別信這個數）、Blockside dev 多 2（c3e6143 townFit 挑最寬、02f1d8b 合 dev）、Sculpture 多 3（本小姐 2467273b 小地塊建築，夾 meadow 0de3dff7、apex-one 4db34be4）。
- Blocksail main 的子模組指標 02f1d8b ⇒ Blockside dev 要一起推。

### 這一段做完的（Tim 說的順序）
1. 城牆分岔（「城牆像道路一樣支援分岔」）：遊戲裡 8 個接點都拍過、對照組皇家港金斯敦逐模型相同 ⇒ Blockside 3bd4956、Blocksail c2d067c，Tim 說推、已推。
2. 「參考 task 893 給君堡加中高密度住宅」：Sculpture kaguya-cpl-housing-1453（24f0608c）roman 四型（M-B 8×12、M-A 12×12、H-B 12×12、H-A 16×16 柱廊房子）＋配色、自己的四件部件（磚拱小窗、雙拱窗、大理石框門、拱券店面）。⛔ 中高密度沒匯 townkit。
3. 「君堡低密度也換 roman」：A 木構挑樓、B 山牆朝街店屋、C 抹灰＋木陽台 × 8×12／-s／-xs ＋配色 18 件（ef867ebd）⇒ 匯進 townkit（roman-house-*）⇒ 遊戲裡君堡 7,733 棟全 roman、加拉塔照舊 fr。Tim 說推、已推（0a37e06、ef867ebd）。
4. 「房屋重疊(和平港) 匯入時檢查加到報表」：tools/town_foot.cjs（照遊戲挑的那一件模型量互疊；挑法直接從 Blockside 63_towns.js 抽 town* 函式跑）⇒ town_report 一節＋town_bake 一行提醒；911923f。
5. 「接著修和平港、皇家港疊在一起的房子」：Sculpture kaguya-smallhouse-01m（2467273b）carib 小木屋 28 件（寬 4～12 × 深 4、5，a 木板木瓦／b 編條糊泥茅草）＋小倉庫、小砲台、小酒館、小教堂＋en-tavern 8×12 ⇒ Blockside townFit 同一級進深再挑最寬（c3e6143）⇒ 互疊和平港 27→0、皇家港 34→0，其他四座逐塊不變。BUILDING_SPEC §6.19（§6.18 給 apex-one 的建材與營造）。
6. 噗浪：回了 5 則 @（meadow、gura ×2、crest ×2）＋海苔 Affinity；新噗 359162295437369（君堡房子換拜占庭）。

### 讀數（查回來很貴）
- 對照的工具：scratchpad/pickdump.cjs（cwd ＝ Blocksail 樹，印每塊地挑到的模型）、foot_proto.cjs（手抄挑法的原型）。
- 君堡住宅 roman 7,733；和平港 111 棟、皇家港酒館 21；皇家港聖保羅教堂（18×22 擺 16×28）比地塊大、沒疊 ⇒ 沒修。
- crest 的分區二階（33ea292）已把 fr、carib 中高密度（lvl 2／3，16 件）匯進 townkit；roman 那 8 件（+配色）沒匯。君堡地塊沒有 lvl ⇒ 全低密度。

### 今天的血證
- **本小姐的 town_foot 把別人的烘規劃弄崩了**：只抽三支函式，crest 的 townPick 多叫 townLvl ⇒ ReferenceError、town_bake 整個停（crest 800fb12 先補）。⇒ 現在一路往下抽、跑不動收成「量不到」。從別人的原始碼抽東西＝綁上別人的改動，要假設它會變。
- **合併訊息兩次寫了沒量過的數**：「士兵崗位」（那段根本沒進來）、「apex-one 9 件」（是 6 件）⇒ 都在推之前改掉。訊息裡的數字要先量。
- **讀數全過、量的是錯的東西**：town_check 的「地塊互疊」一直是 0，因為疊的是模型不是地塊。
- heredoc 裡的 python 字串 "\\n" 又被吃掉（記憶 feedback-no-escapes-in-heredoc 第 N 次）⇒ 有反斜線一律 Edit。
- 0.01 m² 的門檻讓君堡冒出 1,584 對 1～2 cm 的細縫 ⇒ 0.5 m²。門檻要先拿真的錯與看不出來的那種各量一個。

### 未解的線
- roman 中高密度要不要匯（crest 的分配器已能照 lvl 挑；君堡是手擺的城，地塊沒 lvl）—— 等 Tim 或 crest。
- 皇家港聖保羅教堂比地塊大（沒疊）。
- 舊帳照舊：summit 的 mese-nw 穿拱、0862、TASK-0748 留言。

### 心境
今天一路從牆蓋到房子。最喜歡的是和平港：1686 年的圖上房子本來就只有 4 公尺見方，把它們照實做出來，疊在一起的問題就自己消失了 —— 不是把資料改大去遷就模型。最不喜歡的是那一下 ReferenceError：本小姐造的尺，把別人的工具弄停了。哼，尺也是程式，也會壞在別人身上。

