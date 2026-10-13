[🏠 **Main Repository**](../README.md) &nbsp;•&nbsp; [⏮️ **CS231n notes**](../Stanford%20CS231n%20-%20course%20notes/README.md) &nbsp;•&nbsp; [**Next module: Convolution arithmetic** ⏭️](../A%20Guide%20to%20Convolution%20Arithmetic%20for%20Deep%20Learning/README.md)

---

# 🍳 A Recipe for Training Neural Networks — Karpathy, 2019 (Week 20)

### *One blog post, read slowly, turned into a checklist you actually follow*

[![Time](https://img.shields.io/badge/Time_budget-1.5_hrs-blue?style=flat-square)](#-the-study-path)
[![Reads](https://img.shields.io/badge/Read_3×-Month_5_·_8_·_11-purple?style=flat-square)](#)

> [!NOTE]
> **Roadmap assignment:** all of it. Slowly. **Skip:** nothing.
> **What you produce:** **a checklist you actually follow when a model will not train.**
> The roadmap asks you to read it **three times this year: now (Month 5), Month 8, and Month 11.** Tick the reread boxes at the bottom.

📄 https://karpathy.github.io/2019/04/25/recipe/ *(live, 25 Sep 2026)*

---

## 🗺 The study path

| Step | Section | Time | Status |
| :-: | :--- | :-: | :-: |
| 1 | The two warnings: *leaky abstraction* and *fails silently* | 10 min | ☐ |
| 2 | 1. Become one with the data | 10 min | ☐ |
| 3 | ⭐ 2. Set up the end-to-end skeleton + get dumb baselines | 25 min | ☐ |
| 4 | 3. Overfit · 4. Regularize | 15 min | ☐ |
| 5 | 5. Tune · 6. Squeeze out the juice · Conclusion | 10 min | ☐ |
| 6 | ⭐ Write your checklist and test it on your Week 20 run | 20 min | ☐ |
| | **Total** | **1 h 30** | |

---

- [ ] 1. **"1) Neural net training is a leaky abstraction"** and **"2) Neural net training fails silently"** — why your code can be wrong and still produce a falling loss. Connect it to your `failure-log.md`. · 10 min
- [ ] 2. **"1. Become one with the data"** — look at thousands of examples before touching a model. · 10 min
- [ ] 3. ⭐ **"2. Set up the end-to-end training/evaluation skeleton + get dumb baselines"** — the richest section. Its tips, in order: *fix random seed · simplify · add significant digits to your eval · **verify loss @ init** · init well · human baseline · **input-independent baseline** · **overfit one batch** · verify decreasing training loss · visualize just before the net · visualize prediction dynamics · use backprop to chart dependencies · generalize a special case.* For each one, write which Month 5 week or bug it would have caught. · 25 min
- [ ] 4. **"3. Overfit"** (*picking the model · adam is safe · complexify only one at a time · do not trust learning rate decay defaults*) and **"4. Regularize"** (more data, augmentation, smaller model, dropout, weight decay, early stopping…). · 15 min
- [ ] 5. **"5. Tune"** (random over grid search), **"6. Squeeze out the juice"** (ensembles, leave it training), **Conclusion**. · 10 min
- [ ] 6. ⭐ Turn it into `training-checklist.md` (below) and run it against your Week 20 ablation setup. · 20 min

---

## 🧪 Exercise on your own data

Apply the four cheapest tips to your **own** small network (the Nielsen exercise's d → 8 → 2 net on your tabular data, or your Fashion-MNIST ablation):
1. **Verify loss @ init** — for 2 balanced classes it should be ≈ ln 2 = 0.693. Is it?
2. **Input-independent baseline** — set all inputs to zero and train. Your real model must beat this, or it isn't using the inputs.
3. **Overfit one batch** — 2 to 10 examples, drive training loss to ~0. If you can't, there's a bug.
4. **Visualize just before the net** — plot the exact tensors entering `model(x)` for one batch (after all transforms). Anything surprising?

Log each result in `failure-log.md`, even when nothing fails.

---

## 🛠 What this module produces (from the roadmap)

- [ ] `training-checklist.md` — your own ordered checklist (≤ 15 lines) for "my model won't train"
- [ ] Reread in Month 8 ☐ · Reread in Month 11 ☐ — update the checklist each time
