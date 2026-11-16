---
title: "Development and Validation of a Deep-Learning-Based Algorithm for Detecting and Classifying Metallic Implants in Abdominal and Spinal CT Topograms"
type: source
status: reviewed
updated: "2026-11-16"
tags: [ct-topogram, metallic-implants, segmentation, imar]
---

# Choi 等（2024）｜腹部與脊椎 CT Topogram 金屬植入物偵測

## 書目與讀取範圍

- Choi, M.-H., Jung, J.-Y., Peng, Z., Grosskopf, S., Suehling, M., Hofmann, C., & Pak, S. (2024). *Diagnostics*, 14(7), 668。
- [正式版 DOI](https://doi.org/10.3390/diagnostics14070668) · [原始 PDF](../../raw/papers/diagnostics-14-00668.pdf)
- 2026-11-16 收錄。閱讀範圍為正式版主文，獨立補充材料未納入。

## 研究問題與方法

作者以腹部及脊椎 CT Topogram 判斷髖部和脊椎金屬植入物，並估計其頭尾向範圍，作為自動選擇及套用 iterative metal artifact reduction（iMAR）的輸入。模型採類 U-Net 語意分割架構，將影像重採樣至 473 × 473 像素，搭配 ResNet-101 特徵擷取及多尺度池化，使用逐像素交叉熵訓練。原型軟體輸出植入物類別及其在 z 軸上的像素列範圍。見 §2.1–2.4。

## 資料與評估設定

- 髖部模型訓練使用 263 張標註 Topogram，脊椎模型使用 2,127 張。兩組訓練資料來源組成不同。見 §2.1。
- 外部驗證包括另一家醫院連續收集的 2,178 例腹部 CT（AP）及 515 例腰椎 CT（每例含 AP 與側位）。兩名放射科醫師獨立判讀植入物範圍，有分歧時共同達成共識。見 §2.2、§3.2.1、Table 2。
- 敏感度等指標分像素列與病人層級報告。IoU 量測 z 軸範圍重疊，外部 IoU 表只納入真陽性病例。見 §2.4、§3.2.5、Table 3。

## 主要結果

| 項目 | 結果與條件 | 原文位置 |
|---|---|---|
| 內部驗證 IoU | 脊椎 93.0%，髖部 96.2% | §3.1 |
| 腹部 AP，髖部植入物敏感度 | 像素列 78.1%，病人 97.3%（36/37） | §3.2.2、Figure 1b |
| 脊椎 AP，脊椎植入物敏感度 | 像素列 94.2%，病人 98.8% | §3.2.3、Figure 1c |
| 脊椎 AP，髖部植入物敏感度 | 像素列 88.6%，病人 94.1% | §3.2.3、Figure 1d |
| 脊椎側位，髖部植入物 | 作者未能訓練側位髖部偵測，外部驗證未檢出，敏感度 0% | §3.2.3、Figure 1f |
| 外部 z 軸 IoU | 真陽性病例中，模型與兩位讀者的 IoU 介於 0.912–0.977，側位髖部無模型 IoU | Table 3 |
| iMAR 重建時間 | 作者在 1,996 張 Topogram 的模擬中估計平均節省 27.4%（有植入物者） | 摘要、§3.3、Figure 3 |

## 錯誤、限制與解讀

- 骨水泥曾被誤判為脊椎金屬植入物，延伸到薦髂區的脊椎固定器械曾被誤判為髖部植入物，非典型固定系統曾漏檢。作者也記錄體外金屬結構等誤報來源。見 §3.2.4、Figure 2。
- 評估涵蓋同廠牌多台 CT。跨廠牌泛化仍待驗證，整合進 CT 主控台後的臨床效益也未實測。見 §4。
- 可用於支持 Topogram 具備金屬辨識資訊，以及投照方向需要獨立評估。本文測量 z 軸重疊，應保留指標名稱與評估層級，供後續與 YOLO 的 2D bounding box IoU、AP 及 mAP 並列理解。

## 相關頁面

- [CT Topogram 金屬物件偵測](../topics/ct-topogram-metal-object-detection.md)
- [Topogram 的一維 IoU](../concepts/topogram-row-wise-iou.md)
