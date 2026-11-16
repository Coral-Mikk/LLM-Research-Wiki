---
title: "CT Topogram 金屬物件偵測"
type: topic
status: draft
updated: "2026-11-16"
tags: [ct-topogram, object-detection, medical-ai]
---

# CT Topogram 金屬物件偵測

## 研究問題

能否利用正式掃描前取得的 CT Topogram，定位可移除與不可移除金屬物件，協助放射師在正式掃描前複核？

## 目前證據

[Choi 等（2024）](../sources/2024-choi-metallic-implants-ct-topograms.md)用類 U-Net 模型定位並辨識髖部與脊椎植入物。其輸出是供 iMAR 使用的植入物類別與 z 軸範圍。本研究規劃以 YOLO 預測 2D bounding box 並判斷可移除性，臨床決策是正式掃描前複核。Choi 等可引為 Topogram 金屬辨識及外部驗證的先例。可移除金屬的辨識表現仍需直接驗證。

## 評估設計的待答問題

- AP 與側位分開統計各類物件的樣本數、漏檢與誤報。Choi 等在側位髖部組的訓練與驗證結果顯示，整體成績可能掩蓋特定投照與類別的資料缺口。
- 在錯誤分析中記錄高密度材料、投影重疊與非典型物件外觀。掃描範圍內的可移除物件，可另外評估每次檢查是否有漏提醒。
- 若原型需要顯示與預定掃描範圍的關係，可探索額外的[一維 IoU](../concepts/topogram-row-wise-iou.md)。2D 物件定位與分類仍按各類 AP、mAP 與召回率呈現。
