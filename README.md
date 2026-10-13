# 聲音的形狀 · 泡泡機器

[聲音的形狀](https://marskuan.github.io/sound-shape/) 的機器版：聲音不是從瀏覽器的麥克風來，而是從 Pico 上的兩顆 MAX9814 來，同時控制泡泡槍（兩顆伺服＋蠕動泵）。

**網址：<https://marskuan.github.io/sound-shape-machine/>**

## 這個網頁自己做不到什麼

網頁沒辦法直接讀 USB 上的 Pico／Nano，所以**電腦上要有 `dashboard.py` 在跑**，網頁是連回「這台電腦」的 `127.0.0.1:8765` 拿資料、送指令。沒有人在跑它的人打開這個網址，只會看到「連不上」。

## 怎麼用

1. 雙擊桌面的「泡泡槍」（背景啟動 dashboard，不會跳出終端機視窗，再自動打開這個網頁）。
2. 第一次瀏覽器可能會問「要不要允許存取本機網路」，按允許。
3. 不用的時候，雙擊「停止泡泡槍」。

直接開 <http://localhost:8765/3d> 也一樣（dashboard 自己提供同一份網頁）。

## 安全

dashboard 只接受來自自己（`localhost`／`127.0.0.1:8765`）和 `https://marskuan.github.io` 的請求；其他網站的網頁沒辦法叫機器噴泡泡。
