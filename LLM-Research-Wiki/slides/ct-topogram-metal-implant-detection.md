# CT Topogram 金屬植入物偵測｜簡報逐頁稿

[研究筆記](../notes/ct-topogram-metal-implant-detection.md) · [HTML 簡報](../presentations/ct-topogram-metal-implant-detection/index.html)

預設為約 6–8 分鐘的短講，採臨床判讀型。

## 第 1 頁｜CT Topogram 金屬植入物偵測

- **畫面**　從植入物定位到掃描前複核的研究設計
- **來源**　[Choi 等（2024）｜Wiki 主題頁](../wiki/sources/2024-choi-metallic-implants-ct-topograms.md)
- **講者備註**　這次用已收錄的一篇研究，說明 Topogram 能提供什麼資訊，再對照我們的碩論規劃。

## 第 2 頁｜Topogram 能提供哪些植入物資訊？

- **畫面**　植入物類別與頭尾向範圍
- **研究物件**　髖部與脊椎金屬植入物
- **臨床用途**　把植入物類別與 z 軸範圍提供給迭代式金屬假影降低（iMAR）流程。
- **來源**　[Choi 等（2024）§2.1–2.4](../wiki/sources/2024-choi-metallic-implants-ct-topograms.md)
- **講者備註**　先說明模型輸出指向重建流程，接著引出碩論關注的正式掃描前複核。

## 第 3 頁｜從定位影像取得 z 軸範圍

- **畫面**　Topogram → 類 U-Net 語意分割 → 植入物類別與 z 軸範圍
- **訓練資料**　髖部 263 張｜脊椎 2,127 張標註 Topogram
- **外部驗證**　腹部 CT 2,178 例（AP），腰椎 CT 515 例（每例 AP 與側位）。兩位放射科醫師獨立判讀，分歧時達成共識。
- **來源**　[Choi 等（2024）§2.1–2.4、Table 2](../wiki/sources/2024-choi-metallic-implants-ct-topograms.md)
- **講者備註**　說明語意分割是中間步驟。最終輸出是頭尾方向的像素列範圍。

## 第 4 頁｜內部驗證的 z 軸 IoU 均超過 90%

- **畫面**　z 軸 IoU 衡量預測與參考頭尾向範圍的重疊
- **脊椎**　93.0%
- **髖部**　96.2%
- **圖表**　兩條水平長條，刻度 0–100%，條末直接標百分比。
- **來源**　[Choi 等（2024）§2.4、§3.1](../wiki/sources/2024-choi-metallic-implants-ct-topograms.md)
- **講者備註**　強調內部驗證與一維範圍。數值的解讀應保留座標維度。

## 第 5 頁｜臨床判讀要看投照方向與評估層級

- **畫面**　外部驗證｜敏感度
- **腹部 AP｜髖部**　病人層級 97.3%（36/37）｜像素列層級 78.1%
- **腰椎側位｜髖部**　作者未能訓練側位髖部偵測。外部驗證未檢出髖部植入物。
- **來源**　[Choi 等（2024）§3.2.2–3.2.3、Figure 1b／1f](../wiki/sources/2024-choi-metallic-implants-ct-topograms.md)
- **講者備註**　病人層級看有沒有找到，像素列層級看頭尾向範圍內的像素列有多少被找到。這兩個數值回答不同問題。

## 第 6 頁｜哪些情況需要人工複核？

- **畫面**　外部驗證的誤判案例
- **骨水泥**　曾被誤判為脊椎金屬植入物。
- **固定器械**　延伸至薦髂區曾被誤判為髖部植入物。非典型固定系統曾漏檢。
- **限制**　跨廠牌泛化與 CT 主控台整合後的臨床效益仍待驗證。
- **來源**　[Choi 等（2024）§3.2.4、Figure 2、§4](../wiki/sources/2024-choi-metallic-implants-ct-topograms.md)
- **講者備註**　補充跨廠牌泛化，以及整合至 CT 主控台後的臨床效益，仍需要驗證。

## 第 7 頁｜如何評估正式掃描前的金屬複核？

- **畫面**　碩論研究設計｜待驗證
- **模型與輸出**　規劃以 YOLO 定位 2D bounding box，並區分可移除與不可移除金屬。
- **評估分層**　按 AP、側位與物件類別檢視 AP、mAP、召回率及誤報。另評估每次檢查是否漏提醒。
- **來源**　[Wiki｜CT Topogram 金屬物件偵測、Topogram 的一維 IoU](../wiki/topics/ct-topogram-metal-object-detection.md)
- **講者備註**　收束到自己的研究問題。可移除物件的偵測與掃描前提醒表現需用本研究資料直接驗證。
