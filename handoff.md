# 交接檔（handoff.md）

> 任何 Agent、任何電腦接手前**必讀**；收工時**必更新**。本檔只放交接必需的精簡資訊，詳細脈絡放專案藍圖或 Obsidian（若有 L3）。

## ⏯️ 目前做到哪
- 整合三師爸 EP06 跨電腦專案管理三技能（`project-init`, `startup`, `shutdown`）進所有 Agent 全域技能庫：
  - **AntiGravity / AntiGravity 2**：`~/.gemini/config/skills/`
  - **ChatGPT App (Codex)**：`~/.codex/skills/`
  - **OpenCode**：`~/.config/opencode/skills/`
- 自動綁定 GitHub 帳號 (`williewu2008`)，並納入標準範本庫 (`templates/`)。
- 完成跨電腦技能與全域設定同步手冊 [`CHEZMOI_AGENT_SYNC_GUIDE.md`](CHEZMOI_AGENT_SYNC_GUIDE.md)。
- 專案藍圖正式由 `agents.md` 重構更名為跨平台開放標準全大寫 [`AGENTS.md`](AGENTS.md)。
- 跨 Agent 全域安裝 `mathruffian-dot/rdq-skill`（RDQ 需求探索四象限法技能）至 AntiGravity、Codex、OpenCode 與 Claude Code。

## 🚦 目前狀態
- 良好運行中。四大 Agent 均具備跨電腦工作流（EP06 三技能）與動工前需求訪談規格化能力（RDQ 技能）。

## ➡️ 下一步
1. 另一台電腦使用 `chezmoi update` 驗證一鍵同步更新。
2. 啟動 Phase 1.1 核心基石：探討 Agent 核心定義與自主性光譜。

## ⚠️ 注意事項
- chezmoi 遠端倉庫（`williewu2008/dotfiles`）已設定完畢，並以 `.chezmoiignore` 排除敏感 Token 與快取。
- 專案藍圖檔名嚴格保持全大寫 `AGENTS.md`，避免 Mac/Linux 平台大小寫識別問題。

## 🕐 最後更新
- 時間：2026-10-12 01:05
- 更新者：AntiGravity @ SSNB0168
- Git push：待推（等待使用者確認收工 commit）



