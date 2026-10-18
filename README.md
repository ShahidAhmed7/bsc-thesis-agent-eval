# B.Sc. Thesis · LLM Agent Evaluation

[![Status](https://img.shields.io/badge/Paper-Under%20review%20at%20ARR-darkblue.svg)](#status)
[![arXiv](https://img.shields.io/badge/arXiv-coming%20soon-b31b1b.svg)](#status)
[![Thesis mark](https://img.shields.io/badge/Thesis%20mark-97.9%2F100-brightgreen.svg)](#)
[![License: MIT](https://img.shields.io/badge/License-MIT-lightgrey.svg)](LICENSE)

Code from my B.Sc. thesis in Computer Science and Engineering at BRAC University.
The thesis received a mark of **97.9/100**.

## Status

- **Paper:** under review at ACL Rolling Review (ARR), October 2026 cycle.
- **Preprint:** arXiv link coming soon.
<!-- After arXiv announces the paper, replace the line above with:
- **Preprint:** [arXiv:XXXX.XXXXX](https://arxiv.org/abs/XXXX.XXXXX)
and point the arXiv badge at the same link. -->

## Overview

Tool-using LLM agents read untrusted content such as emails, files and web pages.
An attacker can hide an instruction in that content and try to take over the agent's tool calls.
This project studies how small open-weight agents behave when that happens.
It runs agents on the InjecAgent and AgentDojo benchmarks, labels each trajectory with an LLM judge, and then changes one deployment setting at a time (system prompt, guardrail, serving precision) to see how behavior and task completion shift.

## Repository layout

| Folder | Contents |
| :--- | :--- |
| `experiments/01_baseline_runs` | Benchmark runs at FP16, FP8 and NF4 |
| `experiments/02_behavior_labeling` | LLM-judge labeling and the human agreement check |
| `experiments/03_system_prompt_conditions` | System prompt that permits vs. forbids injected instructions |
| `experiments/04_guardrail` | Explicit instruction-boundary guardrail |
| `experiments/05_precision_and_utility` | Precision effects and task completion |
| `analysis` | Scripts that produce the tables and statistics |
| `figures` | Plotting scripts and figures |
| `prompts` | System prompts and the judge prompt |
| `configs` | Provider config template (no real keys) |
| `data` | Not tracked in git. Download link will be added here |

## Authors

Farhan Zarif, Kazi Shahid Ahmed Galib, Synthia Akter Promi, Shabnam Sharmin Tarin, Ariyan Hossain, Sadif Ahmed, Dr. Farig Yousuf Sadeque

Department of Computer Science and Engineering, BRAC University

## Citation

A BibTeX entry will be added once the arXiv ID is assigned.

## License

[MIT](LICENSE)
