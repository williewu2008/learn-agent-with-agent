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
├── ANTIGRAVITY.md                  # 專案規範、Agent 指南與開工/收工工作流程
├── agents.md                       # 專案工作藍圖（Roadmap）、階段性目標與進度看板
├── AGENT_RECIPE.md                 # 專供其他 Agent 閱讀的知識庫自動建置協定 (SOP)
├── antigravity_tutorials.md        # YouTube Antigravity 精選教學影片清單
├── sensebar_ai_agent_tutorials.md  # 三師爸 (@sensebar) AI Agent 61 部教學影片清單
├── urls.txt                        # 純網址清單 (供快速複製貼入 NotebookLM)
├── README.md                       # 專案簡介與導覽索引
├── .gitignore                      # Git 忽視清單（環境設定、暫存檔案）
├── subtitles/                      # 61 部 AI Agent 系列教學影片完整逐字稿與字幕庫
│   ├── README.md                   # 字幕檔案分類與快速導覽索引
│   ├── 01-antigravity/             # AntiGravity 系列逐字稿 (EP01~EP09)
│   ├── 02-opencode/                # OpenCode 系列逐字稿 (入門~EP07)
│   ├── 03-codex/                   # GPT-CodeX 系列逐字稿 (EP01~EP05 及應用)
│   ├── 04-claude/                  # Claude Code & AI 系列逐字稿 (EP01~EP14)
│   └── 05-agent/                   # AI Agent 基本功與專題逐字稿 (EP01~EP07)
└── notes/                          # 知識庫與主題研究筆記
    ├── README.md                   # 筆記總覽與導航
    ├── 01-foundations/             # Phase 1: Agent 核心基石與組件
    ├── 02-patterns/                # Phase 2: 設計模式與推論架構 (ReAct, Multi-Agent...)
    ├── 03-frameworks/              # Phase 3: 主流框架評估 (LangGraph, CrewAI, AutoGen...)
    └── 04-protocols/               # Phase 4: 通訊協定與生態 (MCP, Tools, 安全性)
```

---

## 🤖 給其他 AI Agent 的自動建置指引

若你是剛克隆或接手本儲存庫的 AI Agent（例如 Claude Code、OpenCode、Antigravity、Codex 等）：
請優先閱讀 **[AGENT_RECIPE.md](file:///e:/用Agent來學習Agent/AGENT_RECIPE.md)**。該文件包含完整的環境配置、資料爬取演算法、字幕清洗與去重規則，可指導你自主且零誤差地重現或擴充此知識庫。

---

## 核心工作指南

- **工作藍圖**：請參閱 [agents.md](file:///e:/用Agent來學習Agent/agents.md) 了解當前進行中任務與學習里程碑。
- **協作規範**：請參閱 [ANTIGRAVITY.md](file:///e:/用Agent來學習Agent/ANTIGRAVITY.md) 查看「開工／收工」流程及 Git 操作原則。

---

## 快速開始

在與 Antigravity 對話時，你可以直接使用以下關鍵指令：
- **「開工」**：Agent 將自動盤點專案狀態、讀取 `agents.md` 進度並提供今日行動建議。
- **「收工」**：Agent 將協助檢查敏感資訊、更新工作藍圖與筆記、整理本次變更並安全提交。
