[🏠 **Main Repository**](../README.md) &nbsp;•&nbsp; [⏮️ **Karpathy's recipe**](../A%20Recipe%20for%20Training%20Neural%20Networks%20%28Karpathy%29/README.md) &nbsp;•&nbsp; [**Next module: Transfer learning** ⏭️](../PyTorch%20-%20Transfer%20Learning%20for%20Computer%20Vision/README.md)

---

# 📐 A Guide to Convolution Arithmetic for Deep Learning — Dumoulin & Visin (reference, Week 21)

### *The shape formulas and the animations that make padding and stride obvious*

[![Tag](https://img.shields.io/badge/Tag-REFERENCE-lightgrey?style=flat-square)](#)
[![Time](https://img.shields.io/badge/Time_budget-2_hrs-blue?style=flat-square)](#-the-study-path)
[![Paper](https://img.shields.io/badge/arXiv-1603.07285v2-b31b1b?style=flat-square)](https://arxiv.org/abs/1603.07285)

> [!NOTE]
> **Roadmap assignment:** the figures and the output-size formulas for standard convolution. **Skip:** the transposed-convolution chapters until you need them.
> **What you produce:** **ten output shapes computed by hand and verified in code.**

**Checked 25 Sep 2026:** [abstract](https://arxiv.org/abs/1603.07285) · [PDF](https://arxiv.org/pdf/1603.07285) · arXiv's [HTML version](https://arxiv.org/html/1603.07285v2) (latest is v2, Jan 2018) · the animations on GitHub: **https://github.com/vdumoulin/conv_arithmetic** — look at the GIFs there instead of the static figures.

---

## 🗺 The study path

| Step | Section | Time | Status |
| :-: | :--- | :-: | :-: |
| 1 | §1.1 Discrete convolutions, §1.2 Pooling | 20 min | ☐ |
| 2 | ⭐ §2 Convolution arithmetic — Relationships 1–6 | 50 min | ☐ |
| 3 | §3 Pooling arithmetic — Relationship 7 | 10 min | ☐ |
| 4 | §5.1 Dilated convolutions (skim) | 10 min | ☐ |
| 5 | ⭐ The 10 hand calculations + code check | 30 min | ☐ |
| | **Total** | **2 h** | |

---

- [ ] 1. **§1.1 Discrete convolutions** and **§1.2 Pooling** — what a kernel, a stride and zero-padding are, drawn out. Watch the GIFs *No padding, no strides* and *Padding, strides* in the GitHub repo. · 20 min
- [ ] 2. ⭐ **§2 Convolution arithmetic** — derive each relationship from the picture, not by memorising (i = input, k = kernel, s = stride, p = padding, o = output): · 50 min
  - §2.1 no padding, unit strides → **o = (i − k) + 1**
  - §2.2 zero padding, unit strides → **o = (i − k) + 2p + 1**; §2.2.1 **half ("same") padding** (k odd, p = ⌊k/2⌋ → o = i); §2.2.2 **full padding** (p = k − 1 → o = i + k − 1)
  - §2.3 no padding, non-unit strides → **o = ⌊(i − k)/s⌋ + 1**
  - §2.4 ⭐ zero padding, non-unit strides → **o = ⌊(i + 2p − k)/s⌋ + 1** — *the general formula; the other five are special cases*
- [ ] 3. **§3 Pooling arithmetic** → **o = ⌊(i − k)/s⌋ + 1** (pooling doesn't pad in the paper's setup). · 10 min
- [ ] 4. **§5.1 Dilated convolutions** — skim: effective kernel size k̂ = k + (k − 1)(d − 1). · 10 min
- [ ] 5. ⭐ Do the exercise below. · 30 min

**Skip:** §4 Transposed convolution arithmetic (all of 4.1–4.6) — you'll need it for decoders/U-Nets, not this year.

---

## 🧪 Exercise on your own data

Use **your own image size** — the resolution of the custom dataset you're collecting for Week 21's transfer learning (e.g. 224×224, or your raw photo size). For 10 configurations (mix stride 1/2, padding 0/"same"/full, kernel 1/3/5/7, one dilated), compute **o** by hand, then check with:

```python
import torch, torch.nn as nn
x = torch.zeros(1, 3, H, W)
print(nn.Conv2d(3, 16, kernel_size=k, stride=s, padding=p, dilation=d)(x).shape)
```

Finally, trace **ResNet-18's** first four layers (conv 7×7 s2 p3 → maxpool 3×3 s2 p1 → …) on your image size by hand, and check against `torchvision.models.resnet18()` with forward hooks.

---

## 🛠 What this module produces (from the roadmap)

- [ ] Ten output shapes computed by hand and verified in code (shares the table with the [CS231n shape drills](../Stanford%20CS231n%20-%20course%20notes/README.md#-exercise-on-your-own-data))
