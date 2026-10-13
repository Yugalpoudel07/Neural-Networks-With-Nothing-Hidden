[🏠 **Main Repository**](../README.md) &nbsp;•&nbsp; [⏮️ **Learn the Basics**](../PyTorch%20-%20Learn%20the%20Basics/README.md) &nbsp;•&nbsp; [**Next module: Karpathy Lecture 1** ⏭️](../Neural%20Networks%20Zero%20to%20Hero%20%28Andrej%20Karpathy%29%20-%20Lecture%201/README.md)

---

# 🧮 PyTorch — A Gentle Introduction to torch.autograd (Week 19, day before your engine)

### *What PyTorch's autograd actually does — read it the day before you build your own*

[![Time](https://img.shields.io/badge/Time_budget-1_hr-blue?style=flat-square)](#-the-study-path)
[![Version](https://img.shields.io/badge/PyTorch-2.14-EE4C2C?style=flat-square)](https://docs.pytorch.org/tutorials/beginner/blitz/autograd_tutorial.html)

> [!NOTE]
> **Roadmap assignment:** all of it. **Skip:** nothing. **What you produce:** notes comparing this to your own engine.
> **When:** the day **before** you build your autograd engine in Week 19. The contrast is the lesson.

> [!IMPORTANT]
> **Link change:** `pytorch.org/tutorials/beginner/blitz/autograd_tutorial.html` now redirects to **https://docs.pytorch.org/tutorials/beginner/blitz/autograd_tutorial.html**.

---

## 🗺 The study path

| Step | Section | Time | Status |
| :-: | :--- | :-: | :-: |
| 1 | Background | 10 min | ☐ |
| 2 | Usage in PyTorch | 15 min | ☐ |
| 3 | ⭐ Differentiation in Autograd | 15 min | ☐ |
| 4 | Optional Reading — Vector Calculus using autograd | 5 min | ☐ |
| 5 | ⭐ Computational Graph + Exclusion from the DAG | 15 min | ☐ |
| | **Total** | **1 h** | |

📄 https://docs.pytorch.org/tutorials/beginner/blitz/autograd_tutorial.html

- [ ] 1. [Background](https://docs.pytorch.org/tutorials/beginner/blitz/autograd_tutorial.html#background) — forward propagation vs backward propagation, in two paragraphs. · 10 min
- [ ] 2. [Usage in PyTorch](https://docs.pytorch.org/tutorials/beginner/blitz/autograd_tutorial.html#usage-in-pytorch) — one training step with a pretrained ResNet: forward, `.backward()`, `optim.step()`. **Just read** — the model download isn't the point. · 15 min
- [ ] 3. ⭐ [Differentiation in Autograd](https://docs.pytorch.org/tutorials/beginner/blitz/autograd_tutorial.html#differentiation-in-autograd) — `Q = 3a³ − b²`; check `a.grad == 9a²` and `b.grad == −2b` **by hand first**. Note why `Q.backward()` needs `gradient=` when Q is a vector. · 15 min
- [ ] 4. [Optional Reading - Vector Calculus using autograd](https://docs.pytorch.org/tutorials/beginner/blitz/autograd_tutorial.html#optional-reading-vector-calculus-using-autograd) — the vector-Jacobian product. Skim: *autograd never builds the full Jacobian.* · 5 min
- [ ] 5. ⭐ [Computational Graph](https://docs.pytorch.org/tutorials/beginner/blitz/autograd_tutorial.html#computational-graph) — the DAG of `Function` objects, `grad_fn`, leaves vs roots, **the graph is recreated from scratch after each `.backward()`** — and [Exclusion from the DAG](https://docs.pytorch.org/tutorials/beginner/blitz/autograd_tutorial.html#exclusion-from-the-dag) (freezing parameters with `requires_grad=False` — exactly what Week 21's transfer learning does). · 15 min

---

## 🧪 Exercise on your own data

Take your Month 3 logistic-regression loss on 5 rows of your own data. Compute ∂loss/∂w three ways and assert they agree to 1e-6:
1. your **hand-derived** formula (Xᵀ(p − y)/n),
2. your **Month 1 numerical gradient checker**,
3. **PyTorch autograd** (`w.requires_grad_(True)`, `loss.backward()`, `w.grad`).

Then print `loss.grad_fn`, `loss.grad_fn.next_functions`, … and draw the graph by hand. Keep the drawing — tomorrow you'll build the thing that makes it.

---

## 🛠 What this module produces (from the roadmap)

- [ ] `autograd-vs-my-engine.md` — started today (what PyTorch does), finished after your engine works (what you did the same / differently: scalar vs tensor nodes, how the graph is stored, how the topological order is found, when gradients accumulate)
