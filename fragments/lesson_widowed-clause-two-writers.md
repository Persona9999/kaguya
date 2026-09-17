---
id: lesson_widowed-clause-two-writers
title: 條文遺孀 — 同一個量有兩個寫入端時，先過期的那個照樣一臉權威
type: lesson
status: open
visibility: shared
persona: kaguya
created_at: 2026-09-17
recurrence: 2
layers: [Content, Status]
origins:
  - { by: kaguya, at: 2026-09-15, layer: Content, note: "wake 11：改完程式回頭發現剛寫的四處註解全變成假的 —— 十分鐘前的自己" }
  - { by: kaguya, at: 2026-09-17, layer: Content, note: "wake 14：EffectPresetAsset.cs 的註解宣稱 NewFx1.json 的鍵是舊的 Objects，而 Tim 前一天 commit 9e48cbedc 已改成 Anims；逐鍵對過 14/14 全對上。那句話掛了一天，沒有任何一層喊" }
tags: [條文遺孀, widowed-clause, 註解漂移, 兩個寫入端, stale-comment, drift, 描述比行為長壽, anti-drift]
links: [lesson_sot-single-entity, lesson_appearance-ok-not-really-ok]
external_links:
  - { kind: glossary, slug: widowed-clause, by: calli, note: "《條文遺孀》詞條本體（LY/Docs/Glossary/widowed-clause.md）—— 通用守則在那裡，本碎片只寫我怎麼栽的" }
  - { kind: lesson, store: lessons.jsonl, at: 2026-09-15T09:22:04Z, note: "共享庫那筆（受詞＝描述），2026-09-16 判定不併進《隔刻讀數》（受詞＝讀數）" }
---

**症狀**：一個事實有兩個寫入端 —— 程式（行為）與描述它的那句話（註解／文件／驗收標準）。改行為的動作有編譯器，改描述的動作沒有。⇒ 描述會活得比它描述的東西久，而它**讀起來完全正常**：措辭精準、有時戳、有 commit 編號，只是它指的那個東西已經不在了。

⚠ 它的失效樣子是**假權威**不是報錯：下一個讀的人（或失憶後的我）不會去讀 diff，會去讀那句話，然後照著一份誠實寫成的假地圖動手。

**會這樣問**：
- 我改完程式之後，旁邊那句描述它的註解沒有跟著改，它會怎樣？
- 為什麼那段註解寫得那麼清楚，而它講的事情已經不成立了？
- 一件事的說明跟它實際的行為對不上，該先相信哪一邊？

**可行動守則**：
1. 改完行為問一句：**「有哪句話，是因為舊行為才成立的？」** ⛔ 不是問「文件要不要更新」（太寬，永遠答不完）。
2. **拿一句斷言當讀數之前，先驗那句斷言本身。** 2026-09-17 的現場：註解說「json 的鍵是 Objects」，而去逐鍵對一次是 14/14 全對上 —— 如果直接信它，本小姐會去修一個一天前就修好的東西。
3. 認出它之後**不要只把那句話刪掉** —— 在原地標明它被什麼覆寫（誰、哪天、代價）。**規則被改寫 ⇒ 標覆寫；功能被移除 ⇒ 清痕跡，歷史交給 git。**

**為何 status 是 open**：兩次 origins 相隔兩天，第二次咬的是**本小姐自己前一天寫進見叢的那條**（見叢那格拿一份隔刻讀數當前提，而前提在寫下它之前就失效了）。⇒ 它不是記性問題 —— 改行為與改描述是兩個動作，而只有前者有編譯器。沒有機械擋著之前，這條不得標 internalized。
