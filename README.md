# RL-Tutorial：视觉语言模型强化学习源码精读合集

这是个人的 VLM-RL 学习仓库。每个子文件夹是一个开源项目的完整镜像（保留上游 git 历史），我在代码中添加中文注释与阅读笔记，不改变任何训练逻辑。所有学术与工程 credit 归原作者。

## 子项目

| 目录 | 来源 | 定位 | 一句话 |
|---|---|---|---|
| [MAYE](./MAYE) | [GAIR-NLP/MAYE](https://github.com/GAIR-NLP/MAYE) | 教学透明 | 从零手写 Reinforce++，只用 Transformers + FSDP2 + vLLM，单文件 recipe 讲清原理 |
| [EasyR1](./EasyR1) | [hiyouga/EasyR1](https://github.com/hiyouga/EasyR1) | 生产框架 | 基于 veRL + Ray + vLLM SPMD，支持 GRPO/DAPO/Reinforce++/RLOO 等 7 种算法 |
| [VLM-R1](./VLM-R1) | [om-ai-lab/VLM-R1](https://github.com/om-ai-lab/VLM-R1) | 任务工程化 | 基于 open-r1 改造的 GRPO 训练，落地检测、定位、GUI 等任务 |

## 推荐阅读路径

**MAYE（原理）→ EasyR1（框架化）→ VLM-R1（任务特化）**

1. **MAYE**：代码量最小，训练循环、奖励、优势估计都在一个 recipe 文件里，适合建立直觉。注意它名字叫 PPO 但实际是 Reinforce++（无 critic，优势 = 白化折扣回报）。
2. **EasyR1**：看同一个 Reinforce++ 在生产框架里如何拆成 actor/rollout/worker，以及 HybridEngine 如何让训练和 vLLM 推理共享权重。
3. **VLM-R1**：看 GRPO 的完整实现（组内相对优势），以及奖励函数如何按任务定制（REC 的 IoU 奖励、OVD 的长度/加权/余弦变体）。

## 各项目 License

- MAYE：MIT
- EasyR1：Apache-2.0
- VLM-R1：Apache-2.0

各子目录中的原始 README、LICENSE 与引用信息均完整保留。
