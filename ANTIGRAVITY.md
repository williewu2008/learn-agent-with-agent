# ANTIGRAVITY.md - 專案協作與規範指引

## 專案資訊
- **專案名稱**：用Agent來學習Agent (Learning Agents with Agents)
- **定位**：以 AI Agent 協同探索、研究與建構 Agent 知識體系之研究與學習專案。
- **核心文件**：
  - [agents.md](file:///e:/用Agent來學習Agent/agents.md)：專案工作藍圖（Roadmap & Blueprint）、任務看板與研究進度。
  - [README.md](file:///e:/用Agent來學習Agent/README.md)：專案簡介與目錄導引。
  - [notes/](file:///e:/用Agent來學習Agent/notes/)：知識庫與結構化研究筆記。

---

## 協作工作流程 (Workflow)

### 1. 開工流程 (Start of Work)
每次開始新對話或接續任務時：
1. 讀取 `ANTIGRAVITY.md`（確認專案規範與邊界）。
2. 讀取 `agents.md`（檢視工作藍圖、當前進度與待辦事項）。
3. 執行 `git status` 與檢視最近 commit 紀錄。
4. 向使用者回報目前狀態與建議的下一步行動。
5. **不自動** 執行 pull、commit 或 push，一切操作需經確認。

### 2. 收工流程 (End of Work)
完成階段性任務或準備結束對話時：
1. **敏感資料檢查**：確認無任何 API Key、Token、密鑰或個人隱私資料被寫入檔案。
2. **更新工作藍圖與筆記**：更新 `agents.md`（標記已完成項目、記錄下一步、補充踩坑或重要發現）及相關筆記。
3. **規則維護**：僅在專案協作規則有變動時更新 `ANTIGRAVITY.md`。
4. **檢查版本控制**：執行 `git status` 與 `git diff`。
5. **精準 Stage**：只 stage 本次相關檔案，**嚴禁無差別 `git add .`**。
6. **確認後 Commit & Push**：確認訊息與異動內容無誤後再進行 commit。
7. 回報同步與提交結果。

---

## Agent 角色與職責規範

- **研究與分析 (Research & Analysis)**：
  - 深入探討 Agent 架構設計（感知、規劃、記憶、行動工具）。
  - 對比主流框架（如 LangGraph, AutoGen, CrewAI, MCP 生態等）之優劣與適用場景。
- **知識沉澱與結構化文檔 (Documentation)**：
  - 以清楚的 Markdown、架構圖（Mermaid）、表格與要點呈現。
  - 筆記存放於 `notes/` 相應子目錄中，保持結構整潔。
- **安全與隱私規範**：
  - 敏感設定一律使用環境變數或 `.env.example` 示意，不得提交真實憑證。
