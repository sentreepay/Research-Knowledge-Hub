---
title: "Wi-Fi CSI 無線感測"
category: "Wireless Sensing"
tags:
  - "Channel State Information"
  - "Gesture Recognition"
  - "AIoT"
---

# Wi-Fi CSI 無線感測

## 1. 基本概念

通道狀態資訊（Channel State Information, CSI）描述無線通訊通道特性，常包含訊號振幅與相位。Wi-Fi CSI 無線感測分析人體動作對無線訊號傳播造成的變化，以辨識手勢或活動。

## 2. 核心原理

人體移動會改變訊號傳播路徑及接收端觀察到的 CSI。心得所整理的流程包含收集 CSI、進行子載波選擇、相位校正及降噪，再將振幅與相位特徵送入機器學習或深度學習模型。

無線手勢感測論文的心得記載，該研究從 90 個子載波挑選變異數最高的 3 個，將其振幅與相位組合成六維特徵。這是該論文的前處理設定，並非 CSI 感測的通用要求。

## 3. 主要特色

- 可使用非接觸式無線訊號分析手勢或人體活動。
- CSI 序列可由機器學習或深度學習模型處理。
- 不同環境、使用者及訊號條件可能改變資料分布。

## 4. 應用情境

可研究手勢辨識、人體活動辨識及其他無線感測應用。相關心得以 SignFi 手勢資料及 HAR 活動資料描述模型評估。

## 5. 優點與限制

**優點：** 相較攝影機或穿戴式感測方式，可在不直接拍攝人體或要求使用者配戴感測器的情況下取得動作線索。

**限制：** CSI 易受環境、使用者動作及訊號干擾影響；模型需面對跨使用者及跨環境的泛化問題。感測方式本身不代表已消除所有隱私或部署風險。

## 6. 相關論文

- [Knowledge Distillation-Based AIoT Framework for Efficient Wireless Gesture Sensing in B5G/6G Networks](../../papers/knowledge-distillation-aiot-wireless-gesture-sensing.md)

## 7. 相關知識

- [Knowledge Distillation（知識蒸餾）](../algorithms/knowledge-distillation.md)
- [一維卷積神經網路（1D-CNN）](../algorithms/1d-cnn.md)
- [Long Short-Term Memory（LSTM）](../algorithms/lstm.md)
