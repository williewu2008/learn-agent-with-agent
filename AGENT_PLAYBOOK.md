# 🤖 Agent 自主部署與專案重現手冊 (Agent Self-Replication Recipe)

> **本文件受眾**：專為接收指令之 AI Agent（Google Antigravity、Claude Code、OpenCode、ChatGPT Codex 等）所撰寫。
> **核心使命**：任何人的 AI Agent 只要完整閱讀本手冊，便能在全新電腦上，自主檢測環境、安裝必要套件、設定全域行為規範、並完整重現專案中的所有工具鏈與知識庫。

---

## 🧭 目錄 (Table of Contents)

1. [Agent 執行契約與安全邊界](#1-agent-執行契約與安全邊界)
2. [系統前置環境自動檢測 (System Prerequisites)](#2-系統前置環境自動檢測-system-prerequisites)
3. [跨 Agent 全域設定自動安裝 (Global Configuration)](#3-跨-agent-全域設定自動安裝-global-configuration)
   - 3.1 語音輸入文字正規化（受控區塊）
   - 3.2 語音回覆規範 (Edge-TTS 行內播放)
4. [專案虛擬環境與核心工具包 (Python Core Toolkit)](#4-專案虛擬環境與核心工具包-python-core-toolkit)
5. [影音知識庫管線自動化 (Video Subtitles Pipeline)](#5-影音知識庫管線自動化-video-subtitles-pipeline)
6. [標準協作工作流 (開工／收工規範)](#6-標準協作工作流-開工收工規範)
7. [驗證核對清單 (Verification Checklist)](#7-驗證核對清單-verification-checklist)

---

## 1. Agent 執行契約與安全邊界

當任何 AI Agent 接到「在電腦上重現本專案」之指令時，必須嚴格遵守以下安全規範：

1. **使用者層級與路徑動態解析**：
   - 使用 `$HOME`（Windows 為 `C:\Users\<當前使用者>`）動態判斷使用者目錄，**嚴禁硬編碼**特定個人使用者名稱。
2. **受控區塊更新（Upsert）**：
   - 修改各 Agent 的全域設定檔時，必須保留起訖標記，保留使用者原有其他設定，**絕不可無差別整檔覆蓋**。
   - 修改任何既有檔案前，強制建立帶時間戳記的備份檔（如 `原檔名.bak-YYYYMMDD-HHmmss`）。
3. **安全邊界與隱私保護**：
   - 嚴格禁止讀取、輸出、顯示或提交任何 API Key、Token、密碼或個資。
   - 版本控制 stage 必須精確指定相關檔案，**嚴禁無差別執行 `git add .`**。

---

## 2. 系統前置環境自動檢測 (System Prerequisites)

Agent 請先於終端機執行檢測腳本，若缺少工具則透過 Windows 原生套件管理員 (`WinGet`) 安裝：

```powershell
# 1. 檢測並安裝 uv (現代化高速 Python 套件管理)
if (-not (Get-Command "uv" -ErrorAction SilentlyContinue)) {
    Write-Output "正在安裝 uv..."
    winget install --id astral-sh.uv -e --accept-package-agreements --accept-source-agreements
}

# 2. 檢測並安裝影音工具鏈 (yt-dlp 與 ffmpeg)
if (-not (Get-Command "yt-dlp" -ErrorAction SilentlyContinue)) {
    Write-Output "正在安裝 yt-dlp..."
    winget install --id yt-dlp.yt-dlp -e --accept-package-agreements --accept-source-agreements
}

# 3. 重新載入當前 Shell 的 PATH 環境變數
$env:Path = [System.Environment]::GetEnvironmentVariable("Path","Machine") + ";" + [System.Environment]::GetEnvironmentVariable("Path","User")
```

---

## 3. 跨 Agent 全域設定自動安裝 (Global Configuration)

### 3.1 語音輸入文字正規化 (受控區塊規範)

將下列受控區塊注入當前電腦已安裝之 Agent 使用者全域設定檔：
- **Codex**：`~/.codex/AGENTS.md`
- **AntiGravity / Gemini**：`~/.gemini/config/AGENTS.md` 以及 `~/.gemini/GEMINI.md`
- **Claude Code**：`~/.claude/rules/voice-input-normalization.md`（或 `~/.claude/CLAUDE.md`）
- **OpenCode**：`~/.config/opencode/instructions/voice-input-normalization.md`（並在 `opencode.json` 加入索引）

```markdown
<!-- BEGIN:SENSEBAR_VOICE_INPUT_NORMALIZATION_V1 -->
## 語音輸入文字正規化

使用者可能以語音輸入，文字中可能出現同音錯字、詞界切分錯誤、標點遺失、英文工具名稱音譯，以及路徑或指令辨識錯誤。

- 先依對話上下文理解使用者最合理的原意，不要逐字死讀。
- 明顯且不影響實際行動的小錯字，直接理解並繼續，不要逐項糾正或打斷使用者。
- 工具名稱可能被音譯或誤辨識。例如在 AI Agent 情境中，`Call Desk` 可能是 `Codex`、`Cloud Code` 可能是 `Claude Code`、`scheme` 可能是 `Skill`。這些只是語境提示，不得在所有情況下強制替換。
- 如果模糊內容會影響實際行動，例如人名、檔名、路徑、指令、工具名稱、數字、日期、金額或核心需求，而且無法從上下文可靠判斷，先用一句話確認理解，再執行。
- 不要默默把關鍵資訊改成猜測版本後直接執行。
- 不要捏造使用者沒有說過的數值、路徑、日期、名稱或授權。
- 回覆時使用自然、修正後的語意即可；除非使用者詢問，否則不必列出所有辨識錯字。
<!-- END:SENSEBAR_VOICE_INPUT_NORMALIZATION_V1 -->
```

### 3.2 語音回覆規範 (Edge-TTS 行內播放)

在 AntiGravity 全域技能庫（`~/.gemini/config/skills/07-voice/`）配置語音模組：
- **預設聲音**：`zh-TW-YunJheNeural`（穩重男聲）。
- **備用聲音**：`zh-TW-HsiaoChenNeural`（活潑女聲）。
- **播放方式**：調用 Windows `PresentationCore.MediaPlayer` 行內播放，**絕不彈出外部播放器視窗**。
- **講稿規格**：精簡（100–250 字）、數字一律轉為中文字、只講核心結論與下一步。

---

## 4. 專案虛擬環境與核心工具包 (Python Core Toolkit)

本專案採用 `uv` 建立乾淨獨立的虛擬環境，不污染全域 Python。

### 4.1 一鍵初始化虛擬環境與安裝套件

於專案根目錄執行：

```powershell
powershell.exe -NoProfile -ExecutionPolicy Bypass -File ".\install_windows.ps1"
```

此腳本將自動完成：
1. 以 Python 3.12 建立專案本機環境：`.\.venv`。
2. 依 `requirements-core.txt` 安裝 10 大核心文件處理套件（Word、Excel、PowerPoint、PDF、圖片處理、圖表繪製、QR Code 與文件轉 Markdown）。
3. 安裝 `edge-tts`（提供語音合成能力）。
4. 執行 `.\.venv\Scripts\python.exe verify_core.py` 進行 10/10 核心冒煙測試。

---

## 5. 影音知識庫管線自動化 (Video Subtitles Pipeline)

專案已收錄三師爸頻道 61 部 AI Agent 系列影音教學。若需在全新環境重新抓取或擴充：

1. **讀取設定指南**：參閱 [`AGENT_RECIPE.md`](AGENT_RECIPE.md)。
2. **抓取清單**：使用 `yt-dlp --flat-playlist` 提取頻道影片列表，篩選出 5 大模組（AntiGravity、OpenCode、Codex、Claude、Agent）。
3. **字幕下載與去重清洗**：
   - 提取 VTT / SRT 字幕。
   - 執行滑動視窗比對演算法，去除 YouTube 自動字幕的連續跑馬燈滾動重複文字。
   - 生成帶時間戳與純文字段落的雙格式 Markdown 文件至 `subtitles/`。
4. **NotebookLM 整合**：匯出純網址清單 `urls.txt`，供使用者一鍵貼入 NotebookLM 生成雙主持人語音深度對話（Audio Overview）。

---

## 6. 標準協作工作流 (開工／收工規範)

每套 Agent 接手本專案時，必須配合使用者的標準指令週期：

### 🌅 開工流程 (Start of Work)
當使用者提到「開工」或開始新任務時：
1. 讀取專案規範 `ANTIGRAVITY.md` 與藍圖 `agents.md`。
2. 檢查 `git status` 與最近的 commit 紀錄。
3. 彙整回報當前進度與建議的下一步。

### 🌇 收工流程 (End of Work)
當使用者提到「收工」或階段性任務告一段落時：
1. **敏感資料檢查**：確保無 API Key、Token 遺留。
2. **同步專案筆記**：更新 `agents.md` 工作看板與決策日誌。
3. **精準 Stage**：明確列出要提交的檔案名稱，**嚴禁 `git add .`**。
4. **語意化提交**：經使用者確認後進行 Commit 與 Push。

---

---

## 7. 跨電腦技能與設定同步 (chezmoi 整合)

若使用者有多台工作裝置（如辦公室桌機、出差筆電、副機），推薦使用 **chezmoi** 管理並同步各 Agent 的技能與全域規範：

- **核心概念**：以 Git 私有儲存庫為中心，精準宣告式納入，避免污染與金鑰外洩。
- **詳細手冊**：參閱 [`CHEZMOI_AGENT_SYNC_GUIDE.md`](CHEZMOI_AGENT_SYNC_GUIDE.md)。
- **核心指令**：
  - 電腦 A（納入）：`chezmoi add ~\.gemini\config\skills`，提交並推送至 GitHub。
  - 電腦 B（更新）：`chezmoi update` 一鍵拉取並自動套用最新技能與設定。

---

## 8. 驗證核對清單 (Verification Checklist)

Agent 在回報「專案重現完成」前，必須依序自我查核：

- [ ] `uv`、`yt-dlp`、`ffmpeg` 終端機能正常調用。
- [ ] 專案專屬 `.venv` 存在，且 `.\.venv\Scripts\python.exe verify_core.py` 輸出 `CORE_OK: 10/10`。
- [ ] `edge-tts` 已裝入 `.venv` 且語音合成測試成功。
- [ ] 已安裝的 Agent 全域設定檔（Codex、Gemini、Claude、OpenCode）皆已寫入語音正規化受控區塊。
- [ ] 61 部影音逐字稿知識庫完整存在於 `subtitles/`。
- [ ] 具備 chezmoi 跨裝置同步手冊 [`CHEZMOI_AGENT_SYNC_GUIDE.md`](CHEZMOI_AGENT_SYNC_GUIDE.md)。
- [ ] Git 狀態乾淨，且無任何機密外洩。

