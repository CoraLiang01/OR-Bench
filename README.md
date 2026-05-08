# Overview

Recent large language models can often generate mathematical formulations and optimization code from natural-language descriptions. However, existing datasets remain fragmented across domains, modeling languages, and evaluation protocols, and many benchmarks evaluate only a single stage of the pipeline, such as formulation generation or code generation. OR-Bench addresses this gap with a unified benchmark for automatic optimization modeling with large language models. Each instance pairs a natural-language optimization problem with aligned references, including input data files, a LaTeX mathematical formulation, Gurobi Python code, an LP file, the optimal objective value, and the optimal solution. OR-Bench is built around the hardest instances in our collection: every problem in the benchmark remains unsolved by all three frontier LLMs in our evaluation. The dataset therefore evaluates whether an LLM can move from text to model to code to solution in a unified and genuinely challenging setting.

## What the Dataset Contains

Each instance in the dataset includes the following fields:

| Field | Description |
|---|---|
| `Problem ID` | Unique problem identifier |
| `Text Description` | Natural-language optimization problem description |
| `Domain` | Application domain |
| `Dataset Address` | Path(s) to the input data files |
| `Optimal Value` | Ground-truth optimal objective value |
| `Optimal Solution` | Ground-truth optimal decision variable values |

This schema is designed to support evaluation across multiple representation levels of the same optimization task.

## Benchmark Scope

The dataset covers a broad range of optimization problems arising in operations research, management science, and analytics applications. Based on the current examples, domains include:

- Supply Chain Planning

- Revenue Management

- Capital Budgeting

- Facility Location Problem

- Production Planning

- Diet Optimization

- Others

The dataset includes both **continuous** and **integer** optimization problems, and spans multiple model classes such as:

- Linear Programming (LP)

- Mixed-Integer Linear Programming (MILP)

- Binary Integer Programming (BIP)


## Evaluation

Because each sample includes multiple references, the dataset supports several complementary evaluation metrics.

### Possible evaluation dimensions

- **Formulation Accuracy**  

  Whether the generated mathematical model captures the correct objective, variables, and constraints.

- **Code Executability**  

  Whether the generated solver code runs successfully.

- **Canonical Model Correctness**  

  Whether the generated LP or equivalent canonical model is optimal.

- **Objective Accuracy**  

  Whether the solved objective matches the ground-truth `Optimal Value`.

- **Solution Accuracy**  

  Whether the returned decision variables match the ground-truth `Optimal Solution`, up to numerical tolerance or equivalent reformulation.

- **End-to-End Solved Rate**  

  Whether the model successfully goes from text and data to a correct final optimization result.

<!-- ## Example Use

A typical task is:

> Given a natural-language optimization problem and its associated data files, generate a correct optimization model and solve it. -->
