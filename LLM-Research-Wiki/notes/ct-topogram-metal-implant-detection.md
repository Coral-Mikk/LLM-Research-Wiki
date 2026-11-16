# CT Topogram 金屬植入物偵測

整理日期 2026-11-16

## 研究問題

能否從 CT 正式掃描前取得的 Topogram 判斷金屬植入物位置？這些證據如何用於設計可移除與不可移除金屬物件的掃前複核研究？

## Wiki 證據

- Choi 等以類 U-Net 偵測髖部與脊椎植入物，輸出植入物類別與 z 軸範圍，供 iMAR 使用。[來源筆記 §2.1–2.4](../wiki/sources/2024-choi-metallic-implants-ct-topograms.md)
- 內部驗證的 z 軸 IoU 為脊椎 93.0%、髖部 96.2%。[一維 IoU](../wiki/concepts/topogram-row-wise-iou.md)衡量頭尾向範圍重疊。[來源筆記 §2.4、§3.1](../wiki/sources/2024-choi-metallic-implants-ct-topograms.md)
- 腹部 AP 的髖部植入物外部驗證敏感度，病人層級為 97.3%（36/37），像素列層級為 78.1%。腰椎側位的髖部模型未能訓練，外部驗證未檢出該類植入物。[來源筆記 §3.2.2–3.2.3、Figure 1](../wiki/sources/2024-choi-metallic-implants-ct-topograms.md)
- 骨水泥與延伸至薦髂區的固定器械曾造成誤判，非典型固定系統曾漏檢。跨廠牌泛化與 CT 主控台整合後的臨床效益仍待驗證。[來源筆記 §3.2.4、Figure 2、§4](../wiki/sources/2024-choi-metallic-implants-ct-topograms.md)

## 碩論研究設計

以 YOLO 預測 2D bounding box 並判斷可移除性。建議依投照方向與類別分開報告結果，檢查漏檢、誤報及每次檢查是否漏提醒。Choi 等的數據可支持 Topogram 植入物定位的可行性。可移除金屬物件的偵測成效仍需直接驗證。[Wiki 主題頁](../wiki/topics/ct-topogram-metal-object-detection.md)

[簡報逐頁稿](../slides/ct-topogram-metal-implant-detection.md) · [HTML 簡報](../presentations/ct-topogram-metal-implant-detection/index.html)

## 建議參考文獻（待收錄）

| 文獻 | 可補足的問題 | 全文 |
|---|---|---|
| Kufel 等（2023），*Chest X-ray Foreign Objects Detection Using Artificial Intelligence* | 可比較 YOLO 在投影影像上如何標註與偵測體外異物和植入物。 | [下載出版社 PDF](https://www.mdpi.com/2077-0383/12/18/5841/pdf?version=1694154054) · [DOI](https://doi.org/10.3390/jcm12185841) |
| Hogeweg 等（2013），*Foreign object detection and removal to improve automated analysis of chest radiographs* | 可作為投影影像異物偵測與錯誤分析的方法參考。 | [下載 PDF](https://delft.care/wp-content/uploads/Foreign-object-detection-and-removal-to-improve-automated-analysis.pdf) |
| Xue 等，*Foreign Object Detection in Chest X-rays* | 可參考如何針對投影影像上小型衣物異物設計偵測。 | [下載 NLM 全文 PDF](https://lhncbc.nlm.nih.gov/LHC-publications/PDF/pub9258.pdf) |
