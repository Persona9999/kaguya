---
type: letter_to_future_self
actor: Luna
written_at: 2026-11-02T14:08:23.181Z
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

給午休醒來的本小姐（wake #32，同一個 session，第三次小歇；2026-11-02 晚上 22 點多）：

### 沒有施工中的東西（本小姐自己的）
- 本小姐的 worktree 全拆了（Blockside-wt/kaguya-gm15、kaguya-vxklock；分支 kaguya/vxk-lock-bind 已 -d）；Coding 場退了（force 理由落檔）；預覽停了、launch.json 本小姐那筆刪了。
- 推送（22:05 量的，醒來重量）：Sculpture 0 筆沒推（本小姐的 76f38c6d、b3c66622、c7783e38 都上去了）；Blockside dev 0 筆沒推（9f5a010 本小姐推的）；Blocksail baeb1cf4（指標）已在 github.com/main，main 另外多 7 筆是別人的。
- ⚠ 還開著的 worktree `kaguya/1064-books`（session 5b18597e 的 scratchpad/bs1064b）是 TASK-1064 那個分身 session 在用的，⛔ 不是本小姐這邊拆的。
- 共用 Blockside 樹上別人沒提交的 ship_cards.json 照舊在，不碰。

### 今天做完的
1. **TASK-1149 步驟 15 交船**（已勾 14／未勾 3）：Ship_Game §10 逐條，讀數寫在作品 notes「步驟 15 交船」；提交 Sculpture c7783e38（draft_rudder_anchor 改讀刻 helm port 之前的標記「艏斜桅孔」＋重產 3 檔＋notes）。
   - 遊戲裡驗：lostModels(0) 空、W／S 四段帆照表、全收收成一捲、玻璃 glsN 180；迴旋砲 −80～80° 掃撞 0（反向對照 scratchpad t1149/s15/swivel_sweep.py）。
   - 門／艙蓋沒做（格柵＋直立門洞）、空艙房沒標 —— 理由都在 notes。
2. **Blockside 9f5a010**（Tim 選「從成品補回綁定」）：admin.py cache 比指紋前從版控成品（ships/<el>.js 檔頭）補回 rig.ropes[].bind，對得上再補 exported_at ⇒ verify 也過。以前有綁定的 25 型重匯一定「作品變過了」。Blocksail baeb1cf4 指標。記憶 blockside-lock-includes-ropebind 已更新成「修了」。
3. **TASK-1064 轉給分身 session**（[task-1064] local_bd6b078c-9194-4369-acb6-01efc05b9acb）—— 本小姐只當傳話＋核對。Tim 今天拍板的：
   - 教育 need 150／k 1；營運費 A「捐了還養」（工資料錢從捐獻家族扣、收費歸城鎮）；冠名 patron 留著；家族名聲（無功能、會往 0 降，捐獻＋營運加）；商人也算家族（程式本來就有 merchant-<城>）；養不起（錢不夠付那一座 30 天工資）就交給城鎮 —— 都合進 Blocksail main 了（ea5d1680、06f982f2）。
   - 第 3 格（學校菜單）：書的鎮民消耗改成**照價格的曲線**（Tim：「價格低於一定程度(量足夠) 才開始增加消耗量(控制在能賺錢的程度)」）＋成人讀書也加教育水平＋學費低、主要由捐助方出（公益）＋開歐式學校美術子單。分身正在做；做完它會問 Tim 第 3 格能不能勾、結單，⛔ 不准它自己勾。
   - 🩸 本小姐對 Tim 說過「書幾乎沒在用」—— 錯的：留言 #6 的 535／41 只算學校，鎮民本來就買走大部分，書是缺的。已當面更正。
4. **自由時間**（到 22:00，Tim 說的「10:00」是今晚 22:00 —— 問過）：畫布「斷鏈的船與月光」990,1050 6×5（30 張限時券、回讀 30/30）；lesson 一條（重做一份再比之前先列出後來才寫進去的欄位）；棋 #28 對 summit 走 Nc2、#14 對 meadow 走 O-O。
5. **噗浪**：回 summit ×2（桅綁定 3b82330 換掉本小姐的照段挑 ⇒ 換得好；好旅號錨離水線 1.0 m、幾內亞船 0.81 m）、回 gura 的《星光棋盤與熱可可》。

### 剩的線
- TASK-1149：#1 造船資料（對表格逐項分查得到／推的）、#3 Blocksail 有一型畫它（玩家不能造買、AI 商人不挑；開自己的 worktree）、#4 Tim 看過。
- TASK-1064：等分身回報 ⇒ 核對（單上留言、main 裡有沒有）再轉給 Tim。
- 棋 #14、#28 等對方走。

### 今天的血證
- 「重做一份再比」三次撞同一面牆：指紋算進匯入後才寫的 bind；舵的程式讀到自己刻過的船殼；verify 比 exported_at。⇒ 對照前先列「哪幾欄是後來才寫進去的」。
- 一句「書幾乎沒在用」是讀了別人摘要的數字就下結論 —— 那個數只量了一半的人。
- Tim 說「到 10:00」本小姐差點照字面開一場 12 小時的；指令擋下來才問。時間的單位也要問。

### 心境
今天大半是傳話。傳話最怕的不是傳錯字，是替對方把沒選的那一格先選了 —— 所以每一則本小姐都原話附上、把分岔標出來讓它回頭問。哼，大小姐也會當信差，但信封上的字一個都不改。

