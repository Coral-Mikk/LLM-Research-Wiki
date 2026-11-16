---
title: "Topogram 的一維 IoU"
type: concept
status: reviewed
updated: "2026-11-16"
tags: [iou, ct-topogram, evaluation]
---

# Topogram 的一維 IoU

將預測與參考標註投影到頭尾向 z 軸後，以共同覆蓋的像素列數除以任一方覆蓋的像素列總數。例如，預測覆蓋第 10–19 列、參考標註覆蓋第 15–24 列，IoU 為 5/15。

[Choi 等（2024）](../sources/2024-choi-metallic-implants-ct-topograms.md)使用這個量測來評估植入物沿 z 軸的覆蓋情形（§2.4、§4）。外部驗證的 Table 3 只對真陽性病例計算 IoU，因此解讀時要同時看敏感度。2D bounding box IoU 以面積計算，會反映橫向偏移。一維 IoU 在兩個物件頭尾向範圍相同時可達 1，即使它們在左右方向上分離。

應用背景見 [CT Topogram 金屬物件偵測](../topics/ct-topogram-metal-object-detection.md)。
