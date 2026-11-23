---
title: "XGBoost"
category: "Machine Learning"
tags: ["Gradient Boosting", "Ensemble Learning", "Classification"]
---

# XGBoost

## 1. 基本概念

XGBoost（Extreme Gradient Boosting）是一種梯度提升決策樹方法，透過逐步建立多個弱模型並加以組合，形成具預測能力的集成模型。

## 2. 核心原理

XGBoost 以加法方式逐步加入新的樹模型，每一輪著重改善目前模型的預測誤差，並透過正則化等設計控制模型複雜度。它可用於分類與迴歸任務。

## 3. 主要特色

- 以梯度提升方式組合多棵樹。
- 支援正則化以控制模型複雜度。
- 可處理分類及迴歸任務。
- 常用於結構化表格資料。

## 4. 應用情境

常用於風險預測、分類及表格資料建模。在 Meta-IDS 中，XGBoost 被設定為元學習器，接收第一層弱學習器的預測結果並整合成最終分類。

## 5. 優點與限制

**優點：** 在結構化資料上通常具有良好表現，並提供多種控制模型複雜度的機制。

**限制：** 仍需調整超參數；模型集成後的解釋性通常不如單一簡單模型，且不代表一定能在所有資料集勝出。

## 6. 相關論文

- [Meta-IDS: Meta-Learning-Based Smart Intrusion Detection System for IoMT Network](../../papers/meta-ids-iomt-intrusion-detection.md)

## 7. 相關知識

- [Meta-Learning（元學習）](meta-learning.md)
