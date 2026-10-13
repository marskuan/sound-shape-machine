# 聲音的形狀 · 泡泡機器

[聲音的形狀](https://marskuan.github.io/sound-shape/) 的機器版：聲音來自 Pico 上的兩顆 MAX9814，同時控制泡泡槍（兩顆伺服＋蠕動泵）。

**網址：<https://marskuan.github.io/sound-shape-machine/>**

不用終端機、不用在電腦上跑任何程式：網頁自己用瀏覽器的 **Web Serial** 直接讀 Pico、對 Nano 下指令。

## 怎麼用

1. 用**電腦版 Chrome 或 Edge** 打開上面的網址（Firefox、Safari、手機都不支援 Web Serial）。
2. Pico 和 Nano 用 USB 接電腦。
3. **第一次**：按左上角「連接 Pico」，選 Pico 那個 COM 埠；再按「連接 Nano」，選 Nano 的。瀏覽器會記住，之後打開網頁會自己連上，USB 掉了重新插上也會自己重連。
4. 按「槍：暫停」（或空白鍵）開始。槍預設是暫停的。

**Pico 和 Nano 同時只能給一個程式用。** 如果狀態列寫「打不開：被別的程式佔住」，是因為電腦上的 `dashboard.py`（泡泡槍）還開著，請先關掉它。

## 兩種接法

| | 怎麼開 | 什麼時候用 |
|---|---|---|
| **USB 直連**（預設） | 打開 GitHub 網址 | 平常用這個 |
| dashboard.py | 雙擊桌面「泡泡槍」，開 `http://localhost:8765/3d` | 備用；Nano 的 USB 卡死時，dashboard 會請 Windows 自動重置它，網頁版做不到（要重新插拔） |

## 安全

- 網頁只在你的瀏覽器裡和你選的那兩個 USB 裝置說話，不上傳任何聲音。
- 泵有上限（PWM 115），連續轉 20 秒網頁會自己關掉，Nano 韌體在 1 秒沒收到指令時也會自己停。
- 一個網站只能存取你**明確選過**的 COM 埠。

## 內部

`index.html` 是單一檔案（Three.js 從 CDN 載入）。分析方法和 Python 版（`dashboard.py`）一致，並用同一段聲音逐塊對照過：音量、頻譜、音高、亮度、兩顆麥克風的方向（GCC-PHAT）、槍的動作、Nano 指令，數值相同。
