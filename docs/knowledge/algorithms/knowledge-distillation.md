---
title: "Knowledge Distillation（知識蒸餾）"
category: "Machine Learning"
tags:
  - "Model Compression"
  - "Teacher-Student"
  - "Deep Learning"
---

# Knowledge Distillation（知識蒸餾）

## 1. 基本概念

知識蒸餾（Knowledge Distillation, KD）是將較大教師模型（Teacher Model）所學資訊轉移至較小學生模型（Student Model）的訓練方式，常用於降低模型部署所需的參數與運算資源。

## 2. 核心原理

學生模型可學習教師模型的輸出機率（Soft Targets），從中取得類別間的相對資訊。另一種方式是比對教師與學生模型的中間特徵表示。兩種目標可組成聯合損失，並調整各損失的權重。

在無線手勢感測論文的心得中，輸出蒸餾稱為 Response-based KD；中間特徵蒸餾則透過 Bottleneck Layer 的 Feature Matching Loss 實作。此為該研究的具體設計，並非所有 KD 方法都採相同架構。

## 3. 主要特色

- 可用較小學生模型學習教師模型的分類資訊。
- Soft Targets 保留教師模型對不同類別的機率分布。
- 特徵蒸餾可對齊模型中間表示。
- 蒸餾方式及損失設計須依教師、學生模型與任務調整。

## 4. 應用情境

可用於希望將已訓練模型部署至運算、記憶體或電力受限裝置的情境。無線手勢感測論文以聯合輸出與特徵蒸餾訓練輕量化 CSI 分類學生模型。

## 5. 優點與限制

**優點：** 可降低學生模型的模型大小或計算負擔，並以教師輸出或特徵作為額外訓練訊號。

**限制：** 蒸餾不保證學生模型一定保留教師模型的所有表現；結果會受模型架構、訓練目標及資料影響。比較模型效果時仍須依實驗設定及評估指標判讀。

## 6. 相關論文

- [Knowledge Distillation-Based AIoT Framework for Efficient Wireless Gesture Sensing in B5G/6G Networks](../../papers/knowledge-distillation-aiot-wireless-gesture-sensing.md)

## 7. 相關知識

- [一維卷積神經網路（1D-CNN）](1d-cnn.md)
- [Wi-Fi CSI 無線感測](../systems/wifi-csi-wireless-sensing.md)
