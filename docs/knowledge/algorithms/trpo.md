---
title: "Trust Region Policy Optimization（TRPO）"
category: "Reinforcement Learning"
tags: ["Policy Optimization", "Deep Reinforcement Learning"]
---

# Trust Region Policy Optimization（TRPO）

## 1. 基本概念

TRPO 是一種策略最佳化（Policy Optimization）方法，應用於強化學習。其核心目標是在更新策略時限制新舊策略之間的變化幅度，避免一次更新過大而使學習表現不穩定。

## 2. 核心原理

TRPO 以信賴區域（Trust Region）的概念限制策略更新，通常透過限制新舊策略分布之間的差異，讓每次更新維持在一定範圍內，再改善期望獎勵。這使策略能逐步更新，而不是任由一次更新大幅改變行為。

## 3. 主要特色

- 屬於策略梯度與策略最佳化方法。
- 透過信賴區域限制策略更新幅度。
- 常用於連續或複雜決策問題。
- 可直接學習狀態到行動的策略。

## 4. 應用情境

可用於機器人控制、連續控制及需要從環境互動中學習決策的問題。在網路切片資源分配研究中，TRPO 用於學習是否接受不同類型的使用者服務請求。

## 5. 優點與限制

**優點：** 限制策略更新幅度，有助於避免過大的更新造成訓練不穩定。

**限制：** 實作與計算相對複雜；其訓練仍依賴環境互動與獎勵設計，並非所有問題都能直接套用。

## 6. 相關論文

- [Deep Reinforcement Learning for Online Resource Allocation in Network Slicing](../../papers/deep-reinforcement-learning-network-slicing.md)

## 7. 相關知識

- [Lyapunov Optimization](lyapunov-optimization.md)
