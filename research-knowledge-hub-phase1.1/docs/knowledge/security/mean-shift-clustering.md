---
title: "Mean Shift Clustering（平均飄移分群）"
category: "Clustering"
tags: ["Unsupervised Learning", "Anomaly Detection", "Intrusion Detection"]
---

# Mean Shift Clustering（平均飄移分群）

## 1. 基本概念

Mean Shift 是一種以資料密度為基礎的非監督式分群方法，透過尋找資料分布中的密度高點，將資料聚集到不同群集。

## 2. 核心原理

方法會在特徵空間中選定一個位置，依核函數與頻寬計算鄰近資料的加權平均，並反覆將位置移向局部密度較高的方向。多個起始位置最後可能收斂至相同密度峰值，形成群集。

## 3. 主要特色

- 不必事先指定群集數量。
- 以資料分布的密度峰值形成群集。
- 結果會受到頻寬等參數設定影響。

## 4. 應用情境

可用於影像分割、資料分群及異常探索。Meta-IDS 將 Mean Shift 用於分析網路流量資料分布，找出正常行為與可能的未知攻擊。

## 5. 優點與限制

**優點：** 不需要預先指定群集數量，能依資料密度結構形成群集。

**限制：** 頻寬設定會顯著影響結果；高維資料或大型資料集可能增加計算負擔，且分群結果本身不等於攻擊分類結論。

## 6. 相關論文

- [Meta-IDS: Meta-Learning-Based Smart Intrusion Detection System for IoMT Network](../../papers/meta-ids-iomt-intrusion-detection.md)

## 7. 相關知識

- [偏差分類器（Biased Classifiers）](biased-classifiers.md)
