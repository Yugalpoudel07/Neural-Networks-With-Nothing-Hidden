[🏠 **Main Repository**](../README.md) &nbsp;•&nbsp; [⏮️ **Karpathy Lecture 1**](../Neural%20Networks%20Zero%20to%20Hero%20%28Andrej%20Karpathy%29%20-%20Lecture%201/README.md) &nbsp;•&nbsp; [**Next module: Nielsen** ⏭️](../Neural%20Networks%20and%20Deep%20Learning%20%28Michael%20Nielsen%29/README.md)

---

# 📂 micrograd — Karpathy — source repository (reference, Week 19)

### *~150 lines to diff against yours — only AFTER your own engine passes its tests*

[![Tag](https://img.shields.io/badge/Tag-REFERENCE-lightgrey?style=flat-square)](#)
[![Time](https://img.shields.io/badge/Time_budget-1_hr-blue?style=flat-square)](#-the-study-path)
[![Repo](https://img.shields.io/badge/GitHub-karpathy%2Fmicrograd-181717?style=flat-square&logo=github)](https://github.com/karpathy/micrograd)

> [!NOTE]
> **Roadmap assignment:** read it once your version works, and diff the two. **Skip:** copying it.
> **What you produce:** a note on what you did differently and why.

> [!WARNING]
> **Do not open this before your engine passes its tests.** If you read it first, your "rebuild" becomes a memory test of someone else's code, and Gate 5 will show it.

**Checked 25 Sep 2026:** repo live at https://github.com/karpathy/micrograd — `micrograd/engine.py` is **94 lines**, `micrograd/nn.py` **60 lines** (the card's "~150 lines" still holds). The README now also points to **microgpt** (Feb 2026), a whole GPT in one dependency-free Python file built on an improved version of this engine — **save that for Month 6, Week 26.**

---

## 🗺 The study path

| Step | File | Time | Status |
| :-: | :--- | :-: | :-: |
| 1 | README (usage example + tests) | 5 min | ☐ |
| 2 | ⭐ `micrograd/engine.py` — the `Value` class | 25 min | ☐ |
| 3 | `micrograd/nn.py` — `Module`, `Neuron`, `Layer`, `MLP` | 15 min | ☐ |
| 4 | `test/test_engine.py` — how he tests against PyTorch | 5 min | ☐ |
| 5 | Write the diff note | 10 min | ☐ |
| | **Total** | **1 h** | |

- [ ] 1. 📄 [README](https://github.com/karpathy/micrograd#readme) — run the *Example usage* snippet against **your** engine: it should print `24.7041`, `138.8338`, `645.5773`. · 5 min
- [ ] 2. ⭐ 📄 [`micrograd/engine.py`](https://github.com/karpathy/micrograd/blob/master/micrograd/engine.py) — for each op, compare his `_backward` closure with yours. Look especially at `__pow__` (only int/float exponents), `relu`, and how `backward()` builds the topological order and seeds `self.grad = 1`. · 25 min
- [ ] 3. 📄 [`micrograd/nn.py`](https://github.com/karpathy/micrograd/blob/master/micrograd/nn.py) — `zero_grad()` living on `Module`; `Neuron(nonlin=...)`. · 15 min
- [ ] 4. 📄 [`test/test_engine.py`](https://github.com/karpathy/micrograd/blob/master/test/test_engine.py) — compare with your Part 6 tests. · 5 min
- [ ] 5. Write the note (below). · 10 min

**Skip:** `demo.ipynb` and `trace_graph.ipynb` (you already trained and drew your own).

---

## 🧪 Exercise on your own data

Run the Karpathy-lecture exercise (logistic regression built from `Value`s on 4 rows of your data) **twice** — once with your engine, once with `pip install micrograd`. Gradients must be identical. If they aren't, find out which engine is wrong using your numerical gradient checker.

---

## 🛠 What this module produces (from the roadmap)

- [ ] `my-engine-vs-micrograd.md` — a table: *op · mine · his · why different · which is better*. Plus one paragraph: what would have to change for tensors instead of scalars (Month 5 → PyTorch).
