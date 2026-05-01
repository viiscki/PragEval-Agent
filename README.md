# PragEval-Agent

> A multi-agent framework for large-scale pragmatic and cross-cultural evaluation of Large Language Models.
>
> 面向大语言模型的跨语言、跨文化语用能力测评系统。

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
![Status](https://img.shields.io/badge/status-WIP-orange)

---

## 🌏 Overview | 项目简介

**PragEval-Agent** is a multi-agent evaluation pipeline designed to systematically probe the **pragmatic competence** and **cultural tendencies** of Large Language Models (LLMs) across languages.

Inspired by the *Nature* paper *Cultural Tendencies in Generative AI* (2024), this project moves beyond surface-level semantic benchmarks and targets the **pragmatic layer** of language understanding — including indirect speech acts, politeness strategies, face-threatening acts, irony, metaphor, and implicature.

本项目受 *Nature* 论文 *Cultural Tendencies in Generative AI* 启发，致力于构建首个百万级中文 LLM 语用能力测评基准，量化模型在不同语言提示下的语用表现与文化倾向漂移。

---

## ✨ Key Features | 核心特性

- 🧩 **Five-Agent Pipeline**: Scenario Generator → Perturbator → Respondent → Pragmatic Judge → Meta-Reviewer
- 🌐 **Bilingual by Design**: Parallel Chinese & English prompts to detect cross-lingual cultural drift
- 📚 **Theory-Grounded**: Built on Grice's Cooperative Principle, Brown & Levinson's Politeness Theory, Leech's Maxims, and Hofstede's Cultural Dimensions
- 🔍 **Human-in-the-Loop**: AI scores validated against expert linguistic annotation (Cohen's Kappa)
- 📊 **Large-Scale**: Targeting 80K seed scenarios → 2.4M perturbed variants

---

## 🏗️ Architecture | 系统架构

```
┌──────────────────┐     ┌──────────────────┐     ┌──────────────────┐
│ Scenario         │     │ Perturbator      │     │ Respondent       │
│ Generator        │ ──▶ │ (context vars)   │ ──▶ │ (LLM under test) │
└──────────────────┘     └──────────────────┘     └──────────────────┘
                                                            │
                                                            ▼
                          ┌──────────────────┐     ┌──────────────────┐
                          │ Meta-Reviewer    │ ◀── │ Pragmatic Judge  │
                          │ (vs human anno.) │     │ (CoT, 5-dim)     │
                          └──────────────────┘     └──────────────────┘
```

| Agent | Role | Theoretical Basis |
|---|---|---|
| Scenario Generator | 生成 82 类语用情境 | Grice / B&L / Leech / Hofstede |
| Perturbator | 在权力、距离、紧迫度、文化四维度扰动 | Sociolinguistic variables |
| Respondent | 调用目标 LLM 双语作答 | — |
| Pragmatic Judge | 五维度 CoT 打分 | Pragmatic appropriateness |
| Meta-Reviewer | 与人工标注做 Kappa 对照 | Inter-rater reliability |

---

## 📂 Repository Structure | 目录结构

```
PragEval-Agent/
├── agents/              # 五个 Agent 的实现
│   ├── generator.py
│   ├── perturbator.py
│   ├── respondent.py
│   ├── judge.py
│   └── reviewer.py
├── prompts/             # Prompt 模板（中英双语）
├── data/
│   ├── seeds/           # 种子情境
│   ├── perturbed/       # 扰动变体
│   └── human_anno/      # 人工标注
├── evaluation/          # Kappa 计算与可视化
├── configs/             # 模型与实验配置
├── notebooks/           # 分析与可视化
├── results/             # 实验结果
└── README.md
```

---

## 🚧 Roadmap | 项目进度

- [x] Pilot study on 500 scenarios (Kappa = 0.71)
- [x] Five-agent pipeline prototype
- [ ] Scale to 80K seed scenarios
- [ ] Release **PragEval-CN** benchmark dataset
- [ ] Publish cross-cultural diagnostic white paper
- [ ] Submit to ACL / EMNLP 2026

---

## 📖 Citation | 引用

If you find this project useful, please consider citing:

```bibtex
@misc{prageval2026,
  title  = {PragEval-Agent: A Multi-Agent Framework for Pragmatic and Cross-Cultural Evaluation of LLMs},
  author = {Your Name},
  year   = {2026},
  url    = {https://github.com/YourUsername/PragEval-Agent}
}
```

---

## 🤝 Acknowledgements | 致谢

This project is potentially supported by the **Xiaomi MiMo Token Plan**.
本项目希望受小米 MiMo 百亿 Token 计划支持。

Inspired by:
> Tao, Y. et al. *Cultural Tendencies in Generative AI*. *Nature Human Behaviour* (2024).

Released under the [MIT License](LICENSE).# PragEval-Agent
A multi-agent framework for large-scale pragmatic and cross-cultural evaluation of LLMs.
