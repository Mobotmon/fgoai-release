# CLAUDE.md

## 這個 repo 是什麼

fgoai-app 的發布用 repo，公開，網址 `https://github.com/Mobotmon/fgoai-release`。使用者從這裡的 Releases 下載程式；之後程式的自動更新也從這裡讀版本資訊和下載檔。

- 原始碼在另一個 repo：本機 `C:\code\robotmon\fgoai`（引擎 `engine/`、介面 `app/`、裝置端工具包 `kit/`）。兩個 repo 完全分開，這裡不放原始碼，也不放它的 commit 歷史。
- 裝置端工具包（kit，`com.cooper.fgoai`）不在這裡發布，它走 `robotmon-scripts`。

## 這裡放什麼

| 位置 | 內容 |
|---|---|
| git 內容 | 只有 `README.md`（給使用者看的首頁）、這份 `CLAUDE.md` 和 `.gitignore` |
| Releases 的附件 | 每一版的 `fgoai-app-<版本>-<打包時間>.zip`，之後加上 `latest.json` |

**zip 不進 git**，只當 release 的附件上傳。不要 `git add` 任何 zip 或解開的程式。

## 發布一版的流程

1. 打包在原始碼 repo 做：跑 `C:\code\robotmon\fgoai\dev_tools\1_打包引擎成zip（升版）.bat`，產生這個 repo 根目錄的 `fgoai-app-<版本>-<打包時間>.zip`（每版 kit 也打包到這裡的 `kit/V<版號>/`；兩者都被 `.gitignore` 擋掉，不進 git）。這一步不是這個 repo 的工作，由使用者或 fgoai 那邊的 agent 做。
2. 在這裡開 release：tag 用 `v<版本>`（例如 `v0.1.10`），跟打包的版號一致；附件是那個 zip。指令：
   `gh release create v<版本> <zip 路徑> --repo Mobotmon/fgoai-release --title "v<版本>" --notes "<更新說明>"`
3. 先給少數人測試的版本勾成 pre-release（`--prerelease`）：`releases/latest` 不會指到它，一般使用者不會收到。

**建立 release 等於對外發布，一定要使用者明確下令才做**，更新說明也要先給使用者看過。

## 自動更新（還沒做，2026-11-11 規劃中）

規劃：程式啟動時讀固定網址 `https://github.com/Mobotmon/fgoai-release/releases/latest/download/latest.json`，有新版就提示，下載 zip、驗證 sha256 後換掉程式資料夾。

- 這條網址會寫死在程式裡，所以 **repo 的擁有者和名稱（`Mobotmon/fgoai-release`）不能改**，附件檔名 `latest.json` 也不能改。
- `latest.json` 的欄位還沒定案（預計有版號、zip 檔名、sha256、更新說明），由原始碼 repo 的打包工具產生。定案前不要自己發明格式上傳。
- 程式端的檢查更新、資料格式版號、啟動前備份都在原始碼 repo 實作，不在這裡。

## 發布管道

- 第一次發布預計放 Google Drive（使用者 2026-11-11），之後的更新才走這裡的 Releases。兩邊是同一個 zip。
- 玩家資料在使用者電腦的 `%LOCALAPPDATA%\fgoai-app`，不在程式資料夾，更新不會動到它。README 的更新步驟是照這個前提寫的；原始碼 repo 改了資料位置或更新方式，README 要跟著改。

## 規則

- 回覆使用者一律用繁體中文；README 也是繁體中文，對象是一般玩家，不寫開發細節。
- 不要改 `C:\code\robotmon\fgoai` 的檔案；那邊需要配合的事回報給使用者。
- 不自行 `git push`，不自行建立、修改或刪除 release 和 tag。
- README 寫到的功能要是已經發布的版本真的有的；還沒做的（例如一鍵更新）不要先寫。
