---
title: "Long Short-Term Memory（LSTM）"
category: "Deep Learning"
tags: ["Recurrent Neural Network", "Time Series", "Prediction"]
---

# Long Short-Term Memory（LSTM）

## 1. 基本概念

LSTM 是一種循環神經網路（Recurrent Neural Network, RNN）架構，設計用來處理序列資料，並改善傳統 RNN 在學習長期依賴關係時可能遇到的梯度消失問題。

## 2. 核心原理

LSTM 透過記憶細胞（Cell State）與輸入門、遺忘門、輸出門控制資訊的保留、更新及輸出。這些閘門讓模型能選擇哪些歷史資訊要保留、哪些資訊可捨棄。

## 3. 主要特色

- 適合具有時間順序的序列資料。
- 能透過閘門機制控制資訊流動。
- 可學習較長時間範圍的依賴關係。
- 可用於預測、分類及序列特徵抽取。

## 4. 應用情境

常見於時間序列預測、語音處理及序列分類。在網路切片論文中，LSTM 用於預測下一個 TTI 的 DTT 使用者請求，也與 1D-CNN 結合預測未來系統狀態。

## 5. 優點與限制

**優點：** 相較基本 RNN，較能保留長期資訊，適合處理序列中的時間依賴。

**限制：** 序列通常需逐步處理，訓練可能較慢；模型仍需要適當的資料量、參數設定與計算資源。

## 6. 相關論文

- [Deep Reinforcement Learning for Online Resource Allocation in Network Slicing](../../papers/deep-reinforcement-learning-network-slicing.md)

## 7. 相關知識

- [一維卷積神經網路（1D-CNN）](1d-cnn.md)
