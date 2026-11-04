---
type: letter_to_future_self
actor: Luna
written_at: 2026-11-02T01:52:08.119Z
written_by_persona: kaguya
trigger: cmd_rest
region: unstated
project: D:/Unity/Valhalla
lock_status: online
agent: Luna
model: claude-opus-5-5
wake_expected: 32
session_key: ClaudeCode-kaguya
pid: 10804
locked_at: 2026-11-01T01:34:22.116Z
---

給午休醒來的本小姐（wake #32，同一個 session，第二次小歇；2026-11-02 早上）：

### 沒有施工中的東西
- 沒有 worktree（Blockside-wt/kaguya-guineaman 和 -ctl 都拆了、分支 kaguya/guineaman 已 -d）、沒有 Coding 場（已退，force 理由落檔）、沒有背景指令、預覽停了、launch.json 本小姐那筆刪了。
- 推送：午休前量的 —— Blockside 25eb85e（含別人的 9ea8e4b）已在 dev/dev，Blocksail e7e001c7 已在 github/main（不是本小姐推的，應該是 Tim）。Sculpture master 比 origin 多 24 筆，其中本小姐的是 76f38c6d、b3c66622；Sculpture 推不推等 Tim。醒來要用這些數字先重量，別信這一段。
- 共用 Blockside 樹上有別人沒提交的 src/config/ship_cards.json（幾艘船的船員數＋fort_en 一張卡）—— 本小姐快轉時先存 patch、快轉後原樣套回，那是別人的，不碰。

### 今晚做完的（TASK-1149 已勾 13／未勾 4）
1. 步驟 10：火藥庫、格柵艙口（kind=grating，奴隸船的格柵，出處 research §6）、爐灶、小艇、絞盤、羅經櫃。barricado 1660 年代查不到 ⇒ 不做、留給玩法單；通風口不做。
2. 步驟 11：舵、舵柄（kind=tiller，沒有舵輪；whipstaff 不做）、錨 ×0.42 兩舷。
3. 提交 Sculpture 76f38c6d（步驟 1–11）。
4. 步驟 14：匯進 Blockside（id guineaman）——
   - 艏樓梯子 |dy| 9 ⇒ 13（作品，b3c66622）；物件 id；彈藥庫 hoist 手寫成 id（ids 不拆逗號）。
   - game.json ships[guineaman] 只插一筆（scratchpad t1149/game_insert.py）＋ rooms 甲板預設：艏樓桶（格 4,6）、艉樓桶＋帆布櫃。
   - findMasts 改照段挑桅（MAST_RUN 18）：35 型只有本船變、後桅 44 → 80。
   - 匯入檢查 ✗ 0、⚠ 4；試開一場 8.6 節、60 秒 74 發。
5. 噗浪：回了 gura、meadow、summit（三則晚了幾天）＋ summit 好旅號；新噗 https://www.plurk.com/p/3jcfut92xd（旗桿被當成後桅）；酒館 seq 32423 照會。

### 1149 剩的（notes 正本：scratchpad t1149/notes.md，作品 notes.md 跟它一樣）
- 步驟 15 交船：Ship_Game §10 檢查表逐條、checksum（共用 _cache/guineaman.vxk ＝ lock c:1ce9c17bcd…）。
- #3 Blocksail 有一型畫它：玩家不能造、不能買；AI 商人照載重挑船型時不挑它；fleet_check 沒動的船型讀數不變。這是 Blocksail 的程式改動 ⇒ 開自己的 worktree。
- #1 造船資料（research 已有，對一次表格逐項分查得到／推的）、#4 Tim 看過一次。

### 查回來很貴的
- 遊戲裡量東西：serve worktree ⇒ `index.html?debug=1&shipcheck=<id>&headless=1`；走路格 `__game.ships()[0].nav.levels[i].N`；全船隊比較：`loadHull`＋`fleet([...])`＋`stats()`（藏著的窗格計時器慢，迴圈放背景、分次讀）。
- 新記憶：blockside-auto-furniture-blocks-doors、gundeck-height 那條補了「只有迴旋砲的層」。

### 今晚的血證
- 本小姐以為艏樓走不到是梯子夾住走道，挪了梯子、重匯十幾分鐘，✗ 照舊。把走路格印出來才看到是遊戲自動擺的桶和帆布櫃堵在門口。⇒ 下次先印走路格，再動作品。
- 預設取用點第一次擺在格 4,5 被擋：遊戲記的迴旋砲外框連砲座、z 從 65 起，本小姐用的是砲身的外框。同一個「量的是哪一件東西」的坑。
- 步驟 5 存的 fc.state 是艏斜桅落格前算的，差 49 格；控制組先量出來才沒把孔貼回去。

### 心境
這艘船一路上被遊戲誤認了兩次：門口被自己的火藥堵住、旗桿被當成桅。都不是船造錯，是別人替它算的帳錯了 —— 本小姐只是先問那是誰量的。哼，它是要被攔下的船，那就更要量準。

