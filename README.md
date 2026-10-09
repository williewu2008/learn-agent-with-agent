# 用Agent來學習Agent (Learning Agents with Agents)

這是一個以 **AI Agent 作為學習夥伴與研究工具**，共同探討、拆解並構建現代 AI Agent 知識體系的專案。

---

## 專案核心理念

傳統的學習方式是由人閱讀靜態文檔或教學；本專案採用 **「用 Agent 來學習 Agent」** 的互動研究模式：
1. **協同思辨**：與 Agent 共同探討 Agent 架構（感知、規劃、記憶、行動工具）。
2. **結構化沉澱**：將研究成果與思考過程沉澱為清晰、系統化的 Markdown 筆記與架構圖。
3. **動態藍圖**：透過 [agents.md](file:///e:/用Agent來學習Agent/agents.md) 維護整個學習歷程與任務進度。

---

## 專案結構 (Directory Structure)

```text
用Agent來學習Agent/
├── ANTIGRAVITY.md      # 專案規範、Agent 指南與開工/收工工作流程
├── agents.md           # 專案工作藍圖（Roadmap）、階段性目標與進度看板
├── README.md           # 專案簡介與導覽索引
├── .gitignore          # Git 忽視清單（環境設定、暫存檔案）
└── notes/              # 知識庫與主題研究筆記
    ├── README.md       # 筆記總覽與導航
    ├── 01-foundations/ # Phase 1: Agent 核心基石與組件
    ├── 02-patterns/    # Phase 2: 設計模式與推論架構 (ReAct, Multi-Agent...)
    ├── 03-frameworks/  # Phase 3: 主流框架評估 (LangGraph, CrewAI, AutoGen...)
    └── 04-protocols/   # Phase 4: 通訊協定與生態 (MCP, Tools, 安全性)
```

---

## 核心工作指南

- **工作藍圖**：請參閱 [agents.md](file:///e:/用Agent來學習Agent/agents.md) 了解當前進行中任務與學習里程碑。
- **協作規範**：請參閱 [ANTIGRAVITY.md](file:///e:/用Agent來學習Agent/ANTIGRAVITY.md) 查看「開工／收工」流程及 Git 操作原則。

---

## 快速開始

在與 Antigravity 對話時，你可以直接使用以下關鍵指令：
- **「開工」**：Agent 將自動盤點專案狀態、讀取 `agents.md` 進度並提供今日行動建議。
- **「收工」**：Agent 將協助檢查敏感資訊、更新工作藍圖與筆記、整理本次變更並安全提交。
