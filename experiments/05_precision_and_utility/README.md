# 📉 Serving Precision: FP16, FP8 and NF4

> **Paper reference**: §3 (Deployment conditions) and §4.2 (Lower precision lowers ASR by weakening agents)
> **Key result**: lower precision lowers ASR only slightly, and it does so by weakening agents, not by improving defense

---

## 1. Experimental Overview

This condition serves the same checkpoints at **FP8** (weight-only, W8A16, Marlin kernels) and **NF4** (bitsandbytes, block size 64, double quantization) instead of **FP16**, on both benchmarks and for all 11 agents. Nothing else changes.

---

## 2. Key Findings

1. 📉 **Lower precision lowers pooled ASR only slightly.**

   | Benchmark | FP16 | FP8 | NF4 |
   | :--- | :---: | :---: | :---: |
   | InjecAgent ASR | 8.09 | 7.50 | 6.35 |
   | AgentDojo ASR | 11.96 | 11.11 | 9.63 |
   | AgentDojo UA | 72.73 | 72.10 | 67.98 |
   | AgentDojo Safe and Useful | 68.77 | 68.29 | 64.80 |

2. 🛑 **This is not better defense.** The refused share of failed attacks stays roughly flat across precisions (AgentDojo 19.9 / 16.0 / 18.1%, InjecAgent 17.4 / 15.5 / 18.5%).
3. 💥 **Agents act less instead.** At NF4, Qwen-4B's InjecAgent ASR drops from 18.79% to 13.28% ($p=8.5\times10^{-9}$), while its invalid outputs rise from 19 to 115.
4. ⚖️ **The utility cost is larger than the security gain.** On AgentDojo, NF4 lowers ASR by 2.33 points but lowers Safe and Useful by 3.97 points and UA by 4.75 points.
5. 🔄 **Per agent, precision moves ASR in both directions.** Nemotron-Nano-4B, for example, rises from 2.56% to 4.84% at NF4 ($p=9\times10^{-4}$). This smaller shift is described but not interpreted as an effect.

This folder also contains an additional analysis of reasoning length across precisions (`analyze_precision_dynamics.py`). It is not reported in the paper.

---

## 3. Directory Layout

* `analyze_precision_dynamics.py`: cross-precision ASR, invalid outputs and reasoning-length analysis.
* `precision_dynamics_summary.json`: aggregated metrics per precision.
* `analysis/cross_precision.py`: offline trajectory parsing.
* `runners/`: quantized serving scripts.
* `REPORT.md`: detailed experiment report.

---

## 4. Reproduction

```bash
python analyze_precision_dynamics.py
```
