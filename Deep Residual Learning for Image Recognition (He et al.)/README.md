[🏠 **Main Repository**](../README.md) &nbsp;•&nbsp; [⏮️ **Transfer learning**](../PyTorch%20-%20Transfer%20Learning%20for%20Computer%20Vision/README.md)

---

# 📄 Deep Residual Learning for Image Recognition — He, Zhang, Ren, Sun, 2015 (optional, Week 21)

### *Your second research paper: why deeper networks got WORSE, and the one-line fix*

[![Tag](https://img.shields.io/badge/Tag-OPTIONAL-lightgrey?style=flat-square)](#)
[![Time](https://img.shields.io/badge/Time_budget-1.5_hrs-blue?style=flat-square)](#-the-study-path)
[![Paper](https://img.shields.io/badge/arXiv-1512.03385-b31b1b?style=flat-square)](https://arxiv.org/abs/1512.03385)

> [!NOTE]
> **Roadmap assignment:** Sections 1–3, especially the motivation and the **degradation problem**. **Skip:** the detailed ImageNet and COCO results tables.
> **What you produce:** a written explanation of **why a skip connection helps gradients flow**.

**Checked 25 Sep 2026:** [abstract](https://arxiv.org/abs/1512.03385) · [PDF](https://arxiv.org/pdf/1512.03385) (12 pages). arXiv doesn't offer a section-linked HTML version of this one, so use the section numbers below in the PDF.

---

## 🗺 The study path

| Step | Section | Time | Status |
| :-: | :--- | :-: | :-: |
| 1 | ⭐ Abstract + §1 Introduction + **Figure 1** | 25 min | ☐ |
| 2 | §2 Related Work (skim) | 5 min | ☐ |
| 3 | ⭐ §3.1 Residual Learning + §3.2 Identity Mapping by Shortcuts + **Figure 2** | 25 min | ☐ |
| 4 | §3.3 Network Architectures + §3.4 Implementation | 15 min | ☐ |
| 5 | §4.2 CIFAR-10 — just the plain vs residual training curves | 5 min | ☐ |
| 6 | Write the explanation | 15 min | ☐ |
| | **Total** | **1 h 30** | |

---

- [ ] 1. ⭐ **§1 Introduction** and **Figure 1** — a 56-layer plain network has **higher *training* error** than a 20-layer one. That rules out overfitting: the deeper net is simply *harder to optimise*. That's the **degradation problem**. · 25 min
- [ ] 2. **§2 Related Work** — skim only the paragraph on shortcut connections. · 5 min
- [ ] 3. ⭐ **§3.1 Residual Learning** — instead of learning H(x), learn **F(x) = H(x) − x**; if the identity is optimal, pushing F to zero is easy. **§3.2 Identity Mapping by Shortcuts** — y = F(x, {Wᵢ}) + x, adding **no parameters**; projection shortcuts when shapes differ. **Figure 2** is the building block — redraw it. · 25 min
- [ ] 4. **§3.3 Network Architectures** (plain vs residual, Figure 3 — skim the diagram) and **§3.4 Implementation** (batch norm after each conv, SGD settings). · 15 min
- [ ] 5. **§4.2 CIFAR-10 and Analysis** — look only at the plain vs ResNet training curves; they're your Week 21 build task 4 in the authors' hands. · 5 min
- [ ] 6. Write `why-skip-connections-help.md`. · 15 min

**Skip:** §4.1 ImageNet tables, §4.3 detection (PASCAL/COCO), the appendix.

---

## 🧪 Exercise on your own data

Your Week 21 build task 4, on **your** images (or CIFAR-10 if your dataset is too small): train a **20-layer plain** CNN and the same network **with skip connections**, same everything else. Plot training loss for both on one figure, and also plot the **gradient norm at the first layer** over training for both. The residual net's first-layer gradients should stay healthy — that plot is your explanation in one picture.

---

## 🛠 What this module produces (from the roadmap)

- [ ] `why-skip-connections-help.md` — using the chain rule: with y = F(x) + x, ∂y/∂x = ∂F/∂x + **I**, so the gradient always has a direct path back (the **+ I** can't vanish). Link your gradient-norm plot.
