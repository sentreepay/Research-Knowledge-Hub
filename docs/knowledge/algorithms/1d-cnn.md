---
title: "一維卷積神經網路（1D-CNN）"
category: "Deep Learning"
tags: ["CNN", "Sequence Data", "Feature Extraction"]
---

# 一維卷積神經網路（1D-CNN）

## 1. 基本概念

1D-CNN 是卷積神經網路的一種形式，卷積核沿著單一維度滑動，常用來擷取序列資料中的局部模式。

## 2. 核心原理

模型透過一維卷積核對輸入序列的局部區段進行運算，產生特徵圖；再依網路設計使用啟動函數、池化或其他層，逐步形成較高階的特徵表示。

## 3. 主要特色

- 卷積運算沿單一維度進行。
- 能擷取鄰近時間點或序列位置的局部特徵。
- 權重共享可降低參數量。
- 可與其他模型架構結合。

## 4. 應用情境

可用於時間序列分類、感測器訊號分析及序列特徵擷取。在網路切片論文中，1D-CNN 與 LSTM 結合，用於預測未來系統狀態。

## 5. 優點與限制

**優點：** 適合擷取局部模式，卷積運算可有效處理序列特徵。

**限制：** 單靠局部卷積不一定能掌握很長距離的依賴關係，通常需透過更深層架構、擴張卷積或其他模型補足。

## 6. 相關論文

- [Deep Reinforcement Learning for Online Resource Allocation in Network Slicing](../../papers/deep-reinforcement-learning-network-slicing.md)

## 7. 相關知識

- [Long Short-Term Memory（LSTM）](lstm.md)
