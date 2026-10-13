# 聲音的形狀 · 泡泡機器

[聲音的形狀](https://marskuan.github.io/sound-shape/) 的機器版：聲音不是從瀏覽器的麥克風來，而是從 Pico 上的兩顆 MAX9814 來，同時控制泡泡槍（兩顆伺服＋蠕動泵）。

這個 repo 是那個畫面的**備份副本**（`index.html`）。實際使用請開電腦上的 dashboard 提供的那份：

**<http://localhost:8765/3d>**

## 為什麼不是直接開 GitHub 的網址

網頁沒辦法直接讀 USB 上的 Pico／Nano，要靠電腦上的 `dashboard.py`。從 GitHub 開的網頁要連回 `127.0.0.1:8765`，但瀏覽器（尤其是 Chrome）會擋「公開網站連你自己電腦」這種連線，所以那條路不可靠。從 `localhost:8765` 開則是同一個來源，沒有這個問題。

## 怎麼用

1. 雙擊桌面的「泡泡槍」：在背景啟動 dashboard（不會跳出終端機視窗），再自動打開 `http://localhost:8765/3d`。
2. 不用的時候，雙擊「停止泡泡槍」。

## 安全

dashboard 只接受來自自己（`localhost`／`127.0.0.1:8765`）和 `https://marskuan.github.io` 的請求；其他網站的網頁沒辦法叫機器噴泡泡。
