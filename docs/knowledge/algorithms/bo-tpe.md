---
title: "BO-TPE（Bayesian Optimization - Tree-structured Parzen Estimator）"
category: "Hyperparameter Optimization"
tags: ["Bayesian Optimization", "Hyperparameter Tuning"]
---

# BO-TPE（Bayesian Optimization - Tree-structured Parzen Estimator）

## 1. 基本概念

BO-TPE 是以貝葉斯最佳化（Bayesian Optimization）為基礎，並使用 Tree-structured Parzen Estimator（TPE）建立搜尋模型的超參數最佳化方法。它常用於在有限次模型訓練下，尋找表現較好的超參數組合。

## 2. 核心原理

TPE 會依據已觀察到的超參數與目標結果，分別估計較佳結果與其他結果所對應的參數分布，再利用這些分布選擇下一組值得評估的超參數，以逐步改善搜尋效率。

## 3. 主要特色

- 以機率模型輔助超參數搜尋。
- 可處理不同型態及條件式的搜尋空間。
- 透過已完成的試驗結果引導後續搜尋。

## 4. 應用情境

常用於機器學習模型的超參數調整。Meta-IDS 使用 BO-TPE 搜尋元學習器的適當超參數。

## 5. 優點與限制

**優點：** 相較於不利用歷史結果的盲目搜尋，可依既有試驗結果選擇後續候選參數。

**限制：** 搜尋仍需要多次模型評估，成本取決於每次訓練的時間；最佳化結果也受搜尋空間及目標指標設定影響。

## 6. 相關論文

- [Meta-IDS: Meta-Learning-Based Smart Intrusion Detection System for IoMT Network](../../papers/meta-ids-iomt-intrusion-detection.md)

## 7. 相關知識

- [Bat Algorithm（蝙蝠演算法）](bat-algorithm.md)
