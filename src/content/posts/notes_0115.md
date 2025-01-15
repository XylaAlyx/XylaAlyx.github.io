---
title: 1月15日笔记
date: 2025-01-15
lastMod: 2025-01-15
category: 日记
tags: [ROS, MCU]
---

## 上午

- 广工框架学习使用
- 仿真控制joint速度/位置
  <!-- ros_control 控制示例 -->
  [控制示例视频](https://docimg5.docs.qq.com/image/AgAABsy7q125VT50kBxPsY19A3PBcvZM.gif?w=7248&h=2160&type=image/gif)
  <!-- ![Alt Text](https://media.giphy.com/media/vFKqnCdLPNOKc/giphy.gif) -->

---

## 下午

- 梳理技能挑战赛流程

### 运球赛流程：

```mermaid
graph TD
    %% 运球赛流程
    A[运球赛开始] --> B[ 3分区内装球, 机器人上只有1个篮球]
    B --> C[起点准备: 机器人移动到S&E点]
    C --> D[按顺序运球: 依次运球到每个必达点]
    D --> E{是否成功完成区段?}
    E -->|是| F[进入下一区段]
    E -->|否| G{选择重试或跳过?}
    G -->|重试| H[从区段起点重新运球]
    G -->|跳过| I[跳过该区段, 后续不得再次运球]
    F --> J{是否完成所有区段?}
    J -->|是| K[返回S&E点, 比赛结束]
    J -->|否| D
    K --> L[记录剩余时间, 每秒记1分]
```

### 投篮赛流程：

```mermaid
graph TD
    %% 投篮赛流程
    M[投篮赛开始] --> N[装球: 3分区内装球, 机器人上只有1个篮球]
    N --> O{是否选择扣篮?}
    O -->|是| P[在限制区内起跳扣篮, 最多2次, 每次成功记7分]
    O -->|否| Q[直接进入投篮]
    P --> Q
    Q --> R[在2分区或3分区投篮, 覆盖标记]
    R --> S{是否完成所有标记投篮?}
    S -->|是| T[进入定点投篮]
    S -->|否| U[转到另一标记处投篮]
    U --> R
    T --> V[在任意标记处定点投篮, 直到时间结束]
    V --> W[注意: 前一个球接触篮筐或落地前不得投出下一个球]
    W --> X[装球辅助: 参赛队员可在场地内装球, 但不得接触机器人]
    X --> Y[比赛结束]
```

<!-- ![svg](../../assets/signature.svg) -->

<mermaidSVG />
<!-- tried to embed an .astro to embed a mermaidSVG  .... -->

> ## 框架移植思考 (TODO)
>
> - 底盘仿真实践
> - 一些常用的电机导入？
> - **URDF的制作**？
