# fgoai-app 下載

這裡是 fgoai-app 的發布點，只放各版本的下載檔與更新資訊，不含原始碼。

fgoai-app 是 Windows 上的 FGO 自動周回工具，透過 Robotmon 操作手機或模擬器上的遊戲，支援台服和日服。

## 下載

到 [Releases](https://github.com/Mobotmon/fgoai-release/releases/latest) 下載最新的 `fgoai-app-<版本>-<時間>.zip`。

## 需要準備

- Windows 電腦
- 裝了 Robotmon 的 Android 手機或模擬器，並在 Mobotmon 的腳本清單載入 `com.cooper.fgoai`
- 已安裝並登入的 `claude` CLI

adb 已經附在下載檔裡，不用另外安裝。

## 第一次安裝

1. 把 zip 解壓縮到任何位置，會得到一個 `fgoai-app` 資料夾。
2. 執行裡面的 `fgoai-app.exe`。
3. 照同一個資料夾裡的 `fgoai使用教學.pdf` 完成環境檢查和第一次掃描。

## 更新

1. 關掉 fgoai-app。
2. 下載新版的 zip。
3. 刪掉舊的 `fgoai-app` 資料夾，把新版解壓縮到原來的位置。
4. 執行新的 `fgoai-app.exe`。

你的設定和玩家資料放在 `%LOCALAPPDATA%\fgoai-app`，不在程式資料夾裡，所以刪掉舊資料夾不會影響它們。

如果 fgoai-app 提示 Robotmon 上的工具包是舊版，到 Mobotmon 的腳本清單更新 `com.cooper.fgoai`。

## 移除

刪掉 `fgoai-app` 資料夾。要連設定和玩家資料一起清掉，再刪 `%LOCALAPPDATA%\fgoai-app`。

## 問題回報

在這個 repo 開 [Issue](https://github.com/Mobotmon/fgoai-release/issues)，寫上版本號和發生了什麼事，並附上 fgoai-app 產生的問題報告。
