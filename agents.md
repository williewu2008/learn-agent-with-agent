# agents.md - 專案工作藍圖 (Project Blueprint)

> **核心理念**：以 Agent 來學習 Agent —— 透過與 AI Agent 的深度對話、拆解分析與協作實驗，建立完整、現代且實用的 AI Agent 知識與實踐體系。

---

## 1. 藍圖架構概覽 (Roadmap Architecture)

```mermaid
flowchart TD
    A["Phase 1: Agent 核心基石與元件拆解"] --> B["Phase 2: Agent 設計模式與工作流程範式"]
    B --> C["Phase 3: 主流框架與開源生態評估"]
    C --> D["Phase 4: 工具鏈、協定與擴展生態 (MCP)"]
    D --> E["Phase 5: 實戰演練、提示工程與反思迭代"]

    subgraph CoreComponents["核心四要素"]
        P1["感知 (Perception)"]
        P2["規劃 (Planning)"]
        P3["記憶 (Memory)"]
        P4["行動 (Action / Tools)"]
    end

    A -.-> CoreComponents
```

---

## 2. 階段性研究與學習藍圖

### Phase 1: Agent 核心基石 (Foundations)
- [ ] **1.1 Agent 概念與自主性光譜**：從 Simple LLM Chain 到完全自主 Agent 的階梯。
- [ ] **1.2 規劃能力 (Planning)**：
  - 目標分解 (Sub-goal Decomposition)
  - 思考回饋 (Chain-of-Thought, Tree-of-Thought)
  - 自我反思與修訂 (Self-Reflection, Self-Correction)
- [ ] **1.3 記憶機制 (Memory)**：
  - 短期記憶 (In-context, Working Memory, Buffer)
  - 長期記憶 (Vector DB, RAG, 知識圖譜, 外部儲存)
- [ ] **1.4 工具使用與行動 (Tool Use & Action)**：
  - Function Calling 原理
  - API 調用與沙盒環境安全機制

### Phase 2: Agent 設計模式與架構範式 (Patterns & Architectures)
- [ ] **2.1 經典推論模式**：
  - ReAct (Reason + Act) 模式深度拆解
  - Plan-and-Solve 模式
  - Reflexion (評估與反饋循環)
- [ ] **2.2 多代理人協作 (Multi-Agent Collaboration)**：
  - 階層式架構 (Hierarchical / Supervisor-Worker)
  - 合作協商 (Peer-to-Peer, Collaboration)
  - 辯論與對抗模式 (Debate / Adversarial verification)

### Phase 3: 主流框架與開源生態評估 (Frameworks & Ecosystem)
- [ ] **3.1 狀態圖與流程控制**：LangGraph 原理與適用場景。
- [ ] **3.2 角色扮演與自主社群**：CrewAI, AutoGen 對比與實踐。
- [ ] **3.3 輕量與可擴展框架**：Google Antigravity 內建 Agent 機制與自定義 subagent。

### Phase 4: 工具鏈、協定與擴展生態 (Protocols & Tooling)
- [ ] **4.1 Model Context Protocol (MCP)**：
  - MCP 架構與通訊協定（Client / Server / Host）
  - 常見 MCP 伺服器分析（檔案系統、GitHub、資料庫、搜尋）
- [ ] **4.2 權限邊界與安全性**：Human-in-the-loop (HITL)、操作確認、沙盒防護。

### Phase 5: 實踐應用與總結 (PoC & Synthesis)
- [ ] **5.1 提示工程最佳實踐 (Prompt Engineering for Agents)**：System Prompt 構建、Few-shot 指導、動態上下文注入。
- [ ] **5.2 總結與個人化 Agent 知識庫**：整理結構化知識手冊與決策指南。

---

## 3. 當前進度看板 (Status Kanban)

| 狀態 | 項目 | 負責 / 協同 | 關聯文檔 |
| :--- | :--- | :--- | :--- |
| **已完成 (Done)** | 專案初始化與結構建立 | User & Agent | [README.md](README.md), [ANTIGRAVITY.md](ANTIGRAVITY.md) |
| **已完成 (Done)** | 工作藍圖制定 (`agents.md`) | User & Agent | [agents.md](agents.md) |
| **已完成 (Done)** | 安裝 yt-dlp & FFmpeg 影音工具鏈 | User & Agent | 系統環境配置 |
| **已完成 (Done)** | 建立三師爸 61 部 AI Agent 教學清單 | User & Agent | [sensebar_ai_agent_tutorials.md](sensebar_ai_agent_tutorials.md) |
| **已完成 (Done)** | 批次抓取並轉存 61 部影片字幕/逐字稿庫 | User & Agent | [subtitles/README.md](subtitles/README.md) |
| **已完成 (Done)** | 撰寫其他 Agent 遵循之建置協定指南 | User & Agent | [AGENT_RECIPE.md](AGENT_RECIPE.md) |
| **已完成 (Done)** | 發布至公開 GitHub 儲存庫 | User & Agent | [learn-agent-with-agent](https://github.com/williewu2008/learn-agent-with-agent) |
| **已完成 (Done)** | 優化 GitHub 儲存庫 (Badges, 範本與文件美化) | User & Agent | [README.md](README.md), [.github/](.github/) |
| **待辦 (Backlog)** | Phase 1.1: 探討 Agent 核心定義與自主性光譜 | 待開始 | [notes/01-foundations/](notes/01-foundations/) |

---

## 4. 決策日誌與踩坑筆記 (Log & Insights)

- **2026-10-11**：
  - 全面優化 GitHub 儲存庫外觀與開源基礎設施。
  - 新增 MIT 開源授權條款 (`LICENSE`)。
  - 新增 GitHub Issue 範本（需求建議與提問討論）。
  - 增強 `README.md`（加入 Shields.io 徽章、視覺化協作流程圖、影音矩陣表與 NotebookLM 實戰指南）。
  - 修復全專案 Markdown 文件中內部檔案連結為標準相對路徑，相容 GitHub 網頁端。
- **2026-10-09**：
  - 建立專案藍圖 `agents.md`，確認專案採取知識庫與研究筆記導向。
  - 確立以「開工／收工」工作流嚴謹管理進度與版本控制。
  - 成功建置 `yt-dlp` 與 `FFmpeg` 本機影音工具環境。
  - 檢索三師爸 (@sensebar) 頻道 355 部影片，精準篩選 61 部與 AI Agent、AntiGravity、OpenCode、Codex、Claude 相關影片並產出教學清單。
  - 自動化批次下載 61 部影片字幕，清洗去重後生成具時間戳與純文字段落的 Markdown 知識庫（`subtitles/`）。
