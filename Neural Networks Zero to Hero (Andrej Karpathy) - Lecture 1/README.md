[🏠 **Main Repository**](../README.md) &nbsp;•&nbsp; [⏮️ **Gentle intro to autograd**](../PyTorch%20-%20A%20Gentle%20Introduction%20to%20torch.autograd/README.md) &nbsp;•&nbsp; [**Next module: micrograd source** ⏭️](../micrograd%20%28Karpathy%29%20-%20source%20repository/README.md)

---

# 🧠 Neural Networks: Zero to Hero — Andrej Karpathy — Lecture 1 (Week 19)

### *"The spelled-out intro to neural networks and backpropagation: building micrograd" — watch once coding along, then rebuild with the video closed*

[![Time](https://img.shields.io/badge/Time_budget-8_hrs-blue?style=flat-square)](#-the-study-path)
[![Video](https://img.shields.io/badge/Video-2h25m-red?style=flat-square&logo=youtube)](https://www.youtube.com/watch?v=VMj-3S1tku0)
[![Split](https://img.shields.io/badge/Split-2.5h_watch_·_5.5h_rebuild-purple?style=flat-square)](#-the-study-path)

> [!NOTE]
> **Roadmap assignment:** watch it once while coding along. Then **close it and rebuild the whole engine from your own notes.** The rebuild is where the learning is. **Skip:** nothing in Lecture 1 (later lectures come in Week 25).
> **What you produce:** **your own autograd engine, in your own repo, with tests.**
> **Folder name:** the card title *Neural Networks: Zero to Hero* has a colon, which Windows doesn't allow in folder names, so the folder drops it.

> [!IMPORTANT]
> **Order in Week 19 (don't swap it):** ① paper derivation of backprop for a 2-layer network (Nielsen ch 2) → ② the [Gentle Introduction to autograd](../PyTorch%20-%20A%20Gentle%20Introduction%20to%20torch.autograd/README.md) → ③ this video, coding along → ④ **rebuild with the video closed** → ⑤ only then [micrograd's source](../micrograd%20%28Karpathy%29%20-%20source%20repository/README.md).
>
> **Links (checked 25 Sep 2026):** course page https://karpathy.ai/zero-to-hero.html · video https://www.youtube.com/watch?v=VMj-3S1tku0 (2h25m) · notebooks https://github.com/karpathy/nn-zero-to-hero/tree/master/lectures/micrograd · exercises: linked in the video description.
> Chapter times below come from the video's chapter list; if a jump lands a few seconds off, use the chapters under the video player.

---

## 🗺 The study path

| Part | What | Time | Status |
| :-: | :--- | :-: | :-: |
| 1 | Watch + code: derivatives and the `Value` object (0:00–0:32) | 40 min | ☐ |
| 2 | Watch + code: manual backprop, a neuron (0:32–1:09) | 45 min | ☐ |
| 3 | Watch + code: automatic backward, topological sort, the reuse bug (1:09–1:39) | 35 min | ☐ |
| 4 | Watch + code: PyTorch comparison, MLP, training (1:39–2:25) | 30 min | ☐ |
| 5 | ⭐ **Rebuild the engine — video closed** | 2 h | ☐ |
| 6 | ⭐ Tests against PyTorch + the numerical gradient checker | 1 h 30 | ☐ |
| 7 | ⭐ MLP on top of your engine, trained on a toy dataset | 1 h 30 | ☐ |
| 8 | Explain it out loud, recorded | 30 min | ☐ |
| | **Total** (2 h 30 watching · 5 h 30 rebuilding) | **8 h** | |

---

### Parts 1–4 — Watch once, coding along · 2 h 30

**Part 1 · 40 min**
- [ ] [micrograd overview](https://www.youtube.com/watch?v=VMj-3S1tku0&t=25s) — what you're about to build in ~150 lines.
- [ ] [Derivative of a simple function with one input](https://www.youtube.com/watch?v=VMj-3S1tku0&t=488s) and […with multiple inputs](https://www.youtube.com/watch?v=VMj-3S1tku0&t=852s) — the numerical derivative `(f(x+h) − f(x))/h`: **your Month 1 gradient checker**, live.
- [ ] ⭐ [Starting the core `Value` object and its visualization](https://www.youtube.com/watch?v=VMj-3S1tku0&t=1149s) — `data`, `_prev`, `_op`, and later `grad` and `_backward`.

**Part 2 · 45 min**
- [ ] ⭐ [Manual backpropagation example #1: simple expression](https://www.youtube.com/watch?v=VMj-3S1tku0&t=1930s) — the chain rule, node by node. **Pause and compute every `grad` on paper before he does.**
- [ ] [Preview of a single optimization step](https://www.youtube.com/watch?v=VMj-3S1tku0&t=3070s).
- [ ] ⭐ [Manual backpropagation example #2: a neuron](https://www.youtube.com/watch?v=VMj-3S1tku0&t=3172s) — tanh's local derivative 1 − tanh².

**Part 3 · 35 min**
- [ ] [Implementing the backward function for each operation](https://www.youtube.com/watch?v=VMj-3S1tku0&t=4142s).
- [ ] ⭐ [Implementing the backward function for a whole expression graph](https://www.youtube.com/watch?v=VMj-3S1tku0&t=4652s) — **topological sort**.
- [ ] ⭐ [Fixing a backprop bug when one node is used multiple times](https://www.youtube.com/watch?v=VMj-3S1tku0&t=4948s) — gradients must **accumulate (`+=`)**. This is the *same reason* PyTorch needs `zero_grad()`.
- [ ] [Breaking up a tanh, exercising with more operations](https://www.youtube.com/watch?v=VMj-3S1tku0&t=5225s).

**Part 4 · 30 min**
- [ ] [Doing the same thing but in PyTorch: comparison](https://www.youtube.com/watch?v=VMj-3S1tku0&t=5971s).
- [ ] [Building out a neural net library (MLP) in micrograd](https://www.youtube.com/watch?v=VMj-3S1tku0&t=6235s), the tiny dataset + loss, collecting parameters, and [gradient descent, training the network](https://www.youtube.com/watch?v=VMj-3S1tku0&t=7272s) — including the **forgot-to-zero-the-grad bug** he makes on camera.
- [ ] Skim the summary, the [walkthrough of the full micrograd code](https://www.youtube.com/watch?v=VMj-3S1tku0&t=8206s), and PyTorch's real tanh backward.

---

### Part 5 — ⭐ Rebuild the engine, video closed · 2 h
- [ ] From **your notes only**: a `Value` class with `+`, `*`, `**`, `tanh` (or `relu`), `exp`, `__neg__`/`__sub__`/`__truediv__`, `__radd__`/`__rmul__`, and `backward()` with a topological sort. Where you get stuck, write the question down — **don't** reopen the video until you've tried for 15 minutes.

### Part 6 — ⭐ Tests · 1 h 30
- [ ] `pytest` tests comparing every op's gradient against **PyTorch** (the same idea as micrograd's own tests) **and** against your **Month 1 numerical gradient checker**. Include the "node used twice" case (`b = a + a`).

### Part 7 — ⭐ An MLP on your engine · 1 h 30
- [ ] `Neuron`, `Layer`, `MLP` classes with `parameters()`; train on a toy 2-D dataset (e.g. `sklearn.datasets.make_moons`) and plot the decision boundary. Zero the grads every step.

### Part 8 — Explain it · 30 min
- [ ] Record yourself (phone, no notes) explaining: what `_backward` stores, why topological order, why `+=`, and how this connects to `optimizer.zero_grad()`. Roadmap loop step 5.

---

## 🧪 Exercise on your own data

Take **4 rows × 3 columns** of your own tabular data with a yes/no target. Build logistic regression **out of your `Value` objects** (w·x + b → sigmoid → binary cross-entropy). Call `backward()` and compare every `w.grad` with your Month 3 hand-derived gradient Xᵀ(p − y)/n. They must match — same maths, now computed automatically.

---

## 🛠 What this module produces (from the roadmap)

- [ ] **Your own autograd engine, in this repo, with passing tests** (from-scratch #7)
- [ ] An MLP trained on it, with a decision-boundary plot
- [ ] A recorded 5-minute explanation (link it in the lab notebook)
