---
title: "LDA（Linear Discriminant Analysis，線性判別分析）"
category: "Feature Extraction"
tags: ["Dimensionality Reduction", "Classification", "Feature Extraction"]
---

# LDA（Linear Discriminant Analysis，線性判別分析）

## 1. 基本概念

線性判別分析（LDA）是一種有監督式的特徵抽取與降維方法，目標是尋找能讓不同類別更容易區分的低維投影空間。

## 2. 核心原理

LDA 尋找線性投影方向，使投影後的類別間差異相對較大、同一類別內部的分散程度相對較小，以保留有助於分類的資訊。

## 3. 主要特色

- 需要使用類別標籤資訊。
- 著重增加類別間可分性。
- 可用於降維，也可作為分類方法。

## 4. 應用情境

可用於分類前的特徵轉換及高維資料分析。Meta-IDS 使用 LDA 將高維資料轉換到較低維空間，同時盡可能保留不同類別的區別能力。

## 5. 優點與限制

**優點：** 可在降維時利用標籤資訊保留類別區別性，並降低後續模型輸入維度。

**限制：** 線性投影可能無法充分表達複雜非線性邊界；可取得的判別維度也受到類別數量限制。

## 6. 相關論文

- [Meta-IDS: Meta-Learning-Based Smart Intrusion Detection System for IoMT Network](../../papers/meta-ids-iomt-intrusion-detection.md)

## 7. 相關知識

- [RFE（遞迴特徵消除）](rfe.md)
