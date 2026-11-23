---
title: "RFE（Recursive Feature Elimination，遞迴特徵消除）"
category: "Feature Selection"
tags: ["Feature Selection", "Dimensionality Reduction", "Machine Learning"]
---

# RFE（Recursive Feature Elimination，遞迴特徵消除）

## 1. 基本概念

RFE 是一種特徵選擇方法，透過反覆訓練模型並移除重要性較低的特徵，逐步找出對預測任務較有幫助的特徵子集合。

## 2. 核心原理

RFE 先使用指定的估計模型評估特徵重要性，再移除排名較低的特徵，重複此流程直到剩下指定數量的特徵或達到停止條件。

## 3. 主要特色

- 屬於包裹式（Wrapper）特徵選擇方法。
- 需要搭配可提供特徵重要性或權重的模型。
- 可設定保留的特徵數量。

## 4. 應用情境

適用於高維度資料、特徵冗餘較多的分類或預測任務。Meta-IDS 使用 RFE 移除較不重要的特徵，以降低後續模型的運算負擔。

## 5. 優點與限制

**優點：** 可依指定模型的預測能力選出特徵，並減少輸入維度。

**限制：** 反覆訓練模型可能耗費較多計算資源；結果會受到基礎模型及資料切分影響。

## 6. 相關論文

- [Meta-IDS: Meta-Learning-Based Smart Intrusion Detection System for IoMT Network](../../papers/meta-ids-iomt-intrusion-detection.md)

## 7. 相關知識

- [LDA（線性判別分析）](lda.md)
