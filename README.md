# 🧠 Neural Networks, With Nothing Hidden

A neural network with no framework: backpropagation derived by hand, a mini autograd engine, and a pure-NumPy MLP trained on MNIST, with every gradient checked numerically. Then PyTorch training loops, a 5-seed ablation study, CNNs with NumPy convolution, ResNet skip connections and transfer learning.

[![Study guides](https://img.shields.io/badge/Study_guides-10%20of%2010-brightgreen?style=flat-square)](#-learning-roadmap--curriculum-status)
[![From scratch](https://img.shields.io/badge/From--scratch_algorithms-0%20of%202-blue?style=flat-square)](#-what-this-repo-will-build--week-by-week)
[![Gate 5](https://img.shields.io/badge/Gate_5-not_attempted-lightgrey?style=flat-square)](#-gate-5--closed-book-90-minutes-non-negotiable)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)](LICENSE)
[![Focus](https://img.shields.io/badge/Focus-Derive%20%C2%B7%20Backprop%20%C2%B7%20Train%20%C2%B7%20Convolve-purple?style=flat-square)](#)

**Month 5 of 12 · Weeks 18–22 · 150 hours** — Theory 7.5 h · Maths 4.5 h · Implementation 7.5 h · Project 7.5 h · Assessment 3 h per week.

---

## 🎯 The Goal, in Simple Words

Deep learning has a reputation for being mysterious. **It isn't.** A neural network is layers of the maths I already did in Month 3's logistic regression, stacked up, with Month 1's chain rule used to work out how to adjust every layer at once.

This month I build one **with no framework at all** — pure NumPy, every gradient worked out by hand. It's harder than following a PyTorch tutorial. It's also the reason that afterwards, **nothing in deep learning will confuse me**.

> [!WARNING]
> **Week 19 is the most important week of the entire twelve months.** Protect it. Schedule nothing else that week. Don't let a bad week push it into a buffer. Every week after Week 19 assumes it.

---

## 🔄 The Month at a Glance

```text
  WEEK 18                  WEEK 19  ★ the key week            WEEK 20                  WEEK 21
  ┌────────────────┐      ┌──────────────────────────┐       ┌────────────────┐       ┌────────────────────┐
  │ PYTORCH AS A   │ ───► │ BACKPROP FROM SCRATCH    │ ────► │ MAKING NETS    │ ────► │ CNNs & TRANSFER    │
  │ TOOL           │      │ paper → autograd engine  │       │ ACTUALLY TRAIN │       │ LEARNING           │
  │ tensors, loop, │      │ → NumPy MLP on MNIST     │       │ optimizers,    │       │ NumPy conv, ResNet │
  │ zero_grad()    │      │ → same net in PyTorch    │       │ init, norm,    │       │ skip, my own Nepal │
  │                │      │ FROM-SCRATCH #7 and #8   │       │ 5-seed ablation│       │ image dataset      │
  └────────────────┘      └──────────────────────────┘       └────────────────┘       └────────────────────┘
   PyTorch basics          Nielsen ch 2 (pen first)            CS231n NN 2 & 3          CS231n ConvNets
   Nielsen ch 1            autograd intro → Karpathy L1        Karpathy's recipe        Conv arithmetic
                           → micrograd source · CS231n         ■ GATE 5 (end of W19)    Transfer learning · ResNet
  WEEK 22 — BUFFER (or Week 19 again, if Gate 5 failed)
```

---

## 🗺 Learning Roadmap & Curriculum Status

Every module folder has a **study guide** (`README.md`): the exact sections to read with deep links, time per step adding up to the card's budget, what to skip, an exercise on my own data, and what the module produces.

| Week | Module | Tag | Primary Source | Core Focus | Budget | Status |
| :-: | :--- | :-: | :--- | :--- | :-: | :-: |
| 18 | **[PyTorch — Learn the Basics](PyTorch%20-%20Learn%20the%20Basics/README.md)** | MUST | PyTorch 2.14 tutorials | Tensors, DataLoader, `nn.Module`, the training loop from memory | 6 h | 📋 Study guide ready |
| 19 | **[PyTorch — A Gentle Introduction to torch.autograd](PyTorch%20-%20A%20Gentle%20Introduction%20to%20torch.autograd/README.md)** | MUST | PyTorch tutorials | What autograd does — the day before building my own | 1 h | 📋 Study guide ready |
| 19 | **[Neural Networks: Zero to Hero — Lecture 1](Neural%20Networks%20Zero%20to%20Hero%20%28Andrej%20Karpathy%29%20-%20Lecture%201/README.md)** | MUST | Andrej Karpathy | Building micrograd; then rebuilding it with the video closed | 8 h | 📋 Study guide ready |
| 19 | **[micrograd — source repository](micrograd%20%28Karpathy%29%20-%20source%20repository/README.md)** | REFERENCE | Andrej Karpathy | Diff against my engine — only after mine works | 1 h | 📋 Study guide ready |
| 18–19 | **[Neural Networks and Deep Learning](Neural%20Networks%20and%20Deep%20Learning%20%28Michael%20Nielsen%29/README.md)** | MUST | Michael Nielsen | Ch 1–2: backprop's four equations, with a pen | 5 h | 📋 Study guide ready |
| 19–21 | **[Stanford CS231n — course notes](Stanford%20CS231n%20-%20course%20notes/README.md)** | MUST | Stanford CS231n | Backprop, NN Parts 1–3, ConvNets | 8 h | 📋 Study guide ready |
| 20 | **[A Recipe for Training Neural Networks](A%20Recipe%20for%20Training%20Neural%20Networks%20%28Karpathy%29/README.md)** | MUST | Andrej Karpathy | A checklist for when a model won't train | 1.5 h | 📋 Study guide ready |
| 21 | **[A Guide to Convolution Arithmetic](A%20Guide%20to%20Convolution%20Arithmetic%20for%20Deep%20Learning/README.md)** | REFERENCE | Dumoulin & Visin | Output-size formulas; 10 shapes by hand | 2 h | 📋 Study guide ready |
| 21 | **[PyTorch — Transfer Learning for Computer Vision](PyTorch%20-%20Transfer%20Learning%20for%20Computer%20Vision/README.md)** | MUST | PyTorch tutorials | Freeze vs fine-tune, on my own images | 2 h | 📋 Study guide ready |
| 21 | **[Deep Residual Learning for Image Recognition](Deep%20Residual%20Learning%20for%20Image%20Recognition%20%28He%20et%20al.%29/README.md)** | OPTIONAL | He et al. (2015) | The degradation problem and skip connections | 1.5 h | 📋 Study guide ready |

**Resources ≈ 34–36 h across five weeks** (the roadmap header says ~34 h; the ten cards' budgets add up to 36 h, including the optional ResNet paper). **The other ~115 hours are derivation, implementation, debugging and experiments.**

> [!NOTE]
> **Changes found on 25 Sep 2026:** PyTorch tutorials moved from `pytorch.org/tutorials` to **`docs.pytorch.org/tutorials`** (old links redirect); the transfer-learning tutorial now uses `weights='IMAGENET1K_V1'` and `transforms.v2`. CS231n notes are live (Spring 2026). The micrograd README now points to **microgpt** (Feb 2026) — saved for Month 6. The Karpathy folder drops the colon from *Neural Networks: Zero to Hero* (Windows can't use `:` in folder names).

---

## 🛠 What This Repo Will Build — week by week

### Week 18 — PyTorch, used as a tool

*Learn:* tensors, reshaping, moving to GPU · **`reshape` vs `view` vs `permute`** · **autograd** · **why `optimizer.zero_grad()` exists** (gradients pile up by default) · `nn.Module` · `Dataset` and `DataLoader` · **the standard training loop, from memory**.

- [ ] Twenty tensor exercises: reshaping, broadcasting, indexing
- [ ] **Re-implement Month 3's logistic regression in PyTorch** — same data, same result; write down what the framework removed
- [ ] The training loop from scratch: training pass, validation pass, early stopping, checkpoint saving
- [ ] **Three bugs on purpose** — forget `zero_grad()`, wrong loss, model left in training mode during evaluation. **Start `failure-log.md` and keep it all year.**

### Week 19 — BACKPROPAGATION FROM SCRATCH · **FROM-SCRATCH #7 and #8** · ■ GATE 5

*Learn:* the forward pass · **backpropagation = the chain rule, applied backwards, efficiently** · gradients of a linear layer, sigmoid, tanh, ReLU, and **softmax + cross-entropy combined** · **vanishing and exploding gradients** · weight initialisation.

- [ ] **Paper first, before any editor is opened:** a 2-layer network, forward pass, then ∂loss/∂(every weight and bias) by hand. Photograph it.
- [ ] **A mini autograd engine** (~150 lines): follow Karpathy's video, then **close it and rebuild from my own notes**
- [ ] **A full neural network in pure NumPy** — forward, backward, updates, no PyTorch — **above 95% on MNIST**: `____ %`
- [ ] **Every gradient checked** against Month 1's numerical gradient checker; every disagreement debugged
- [ ] The same network in PyTorch — **same results**

### Week 20 — Making networks actually train

*Learn:* sigmoid → tanh → ReLU → GELU · **SGD → momentum → Adam** · **the learning rate** and how to find one · batch size · **batch norm, layer norm** · dropout, weight decay, early stopping · **reading a training curve like an X-ray**.

- [ ] **An ablation study on Fashion-MNIST** — change one thing at a time: optimizer, normalization, dropout rate, initialisation
- [ ] **Every configuration × 5 seeds, mean ± sd.** Any difference smaller than the variation **is not a real difference** — say so explicitly
- [ ] Learning-rate range test: loss vs learning rate, find the sweet spot
- [ ] **Break things deliberately:** all-zero init, learning rate 10, a deep net with no normalization — diagnose each from the curve alone; add all to `failure-log.md`
- [ ] **Set up Weights & Biases or MLflow now** — every run from here on is tracked

| Ablation (Fashion-MNIST, 5 seeds) | Val accuracy (mean ± sd) |
| :--- | :-: |
| Baseline | `____` |
| Optimizer: SGD vs momentum vs Adam | `____` |
| Normalization: none vs batch norm | `____` |
| Dropout: 0 vs 0.2 vs 0.5 | `____` |
| Initialisation: default vs He vs zeros | `____` |

### Week 21 — Convolutional networks and transfer learning

*Learn:* convolution — one filter reused everywhere · **convolution arithmetic by hand** · pooling, channels, 1×1 convs · LeNet → AlexNet → VGG → **ResNet (skip connections)** · **transfer learning** · data augmentation, and when it hurts.

- [ ] **2-D convolution in NumPy** — loops first, then vectorised; tested against PyTorch; speedup recorded: `____×`
- [ ] Output shapes by hand for 10 configurations, verified in code
- [ ] A CNN on CIFAR-10 that beats a plain network baseline — **with the parameter count of both**
- [ ] A ResNet skip connection: a deep network with and without it — **the difference in the training curves**
- [ ] **Transfer learning on my own image dataset** (ideally from Nepal): the **three-row table** — from scratch · feature extraction · full fine-tuning
- [ ] Look at the images the model got wrong. Are the mistakes reasonable?

### Week 22 — BUFFER WEEK

For: repeating Week 19 if Gate 5 failed · finishing the transfer-learning project · consolidating · or rest.

---

## 🚧 Gate 5 — closed book, 90 minutes. Non-negotiable.

1. **Derive backpropagation for a 2-layer network with cross-entropy loss, on a blank page.** All weight and bias gradients.
2. Write the backward pass for a linear layer plus ReLU in NumPy — empty editor, 30 minutes.
3. Explain vanishing gradients and name three fixes.
4. Explain what `zero_grad()` does and what happens without it.
5. Explain why softmax and cross-entropy are combined into one operation in practice.

**Pass = 4 out of 5.** If I fail, the Week 22 buffer goes here and I repeat Week 19. No exceptions — this is the load-bearing wall of the whole plan.

Result: `__ / 5` · Date: `____`

> This month has **no public project** — P3 ships in Month 6 ([Shipping-Models-and-Building-Transformers](https://github.com/Yugalpoudel07/Shipping-Models-and-Building-Transformers)) and serves this month's Week 21 model.

---

## ✅ End of Month 5 — I must have

- [ ] **A photographed paper derivation of backpropagation**
- [ ] My own autograd engine, working
- [ ] A pure-NumPy neural network above 95% on MNIST
- [ ] NumPy convolution, tested against PyTorch
- [ ] **An ablation study with mean ± standard deviation across 5 seeds**
- [ ] Transfer-learning comparison table on my own dataset
- [ ] Four documented failure modes in `failure-log.md`
- [ ] Experiment tracking running on every run
- [ ] **Gate 5 passed**
- [ ] 22 lab-notebook entries

> [!WARNING]
> **The trap this month:** watching Karpathy's video and *feeling* like I understand backpropagation. That feeling is not the same as knowing it — Gate 5 will find out, and so will an interviewer. **Paper derivation before the video; rebuild the code with the video closed.**

---

## 🔗 How This Repo Connects to the Others

```text
   MONTH 1 · Mathematics-for-Data-Science       Chain rule                  ─►  backpropagation, layer by layer
                                                Numerical gradient checker  ─►  checking every gradient in Week 19
   MONTH 3 · Machine-Learning-Built-by-Hand     Logistic gradient (p − y)   ─►  δ at the softmax + cross-entropy output
                                                Softmax regression          ─►  the network's last layer
   MONTH 4 · The-Models-That-Win-Real-Problems  5 seeds, mean ± sd          ─►  the Week 20 ablation
                                                Leak-free preprocessing     ─►  normalisation stats from training data only
   NEXT  · Shipping-Models-and-Building-Transformers (Month 6): serve the Week 21 model; RNNs, attention, a small GPT
```

---

## 📂 Repository Organization

```text
Neural-Networks-With-Nothing-Hidden/
├── PyTorch - Learn the Basics/                                  # Week 18: the training loop from memory (6 h)
├── PyTorch - A Gentle Introduction to torch.autograd/           # Week 19: the day before my engine (1 h)
├── Neural Networks Zero to Hero (Andrej Karpathy) - Lecture 1/  # Week 19: micrograd, then rebuild (8 h)
├── micrograd (Karpathy) - source repository/                    # Week 19: diff after mine works (1 h)
├── Neural Networks and Deep Learning (Michael Nielsen)/         # Weeks 18–19: ch 1–2 with a pen (5 h)
├── Stanford CS231n - course notes/                              # Weeks 19–21: backprop, NN 1–3, ConvNets (8 h)
├── A Recipe for Training Neural Networks (Karpathy)/            # Week 20: my training checklist (1.5 h)
├── A Guide to Convolution Arithmetic for Deep Learning/         # Week 21: shape formulas (2 h)
├── PyTorch - Transfer Learning for Computer Vision/             # Week 21: on my own images (2 h)
├── Deep Residual Learning for Image Recognition (He et al.)/    # Week 21: optional paper (1.5 h)
├── LICENSE                                                      # MIT License
└── README.md                                                    # You are here
```

The autograd engine, the NumPy network, the ablation, the NumPy convolution and `failure-log.md` get added as they're built.

---

## 🚀 Navigation & Study Guide

* **Week 19 order is fixed:** Nielsen ch 2 with a pen → autograd intro → Karpathy L1 (coding along) → **rebuild with it closed** → micrograd source → CS231n backprop + case study → MNIST in NumPy.
* **Week 20:** CS231n NN Parts 2–3 give the knobs; Karpathy's recipe gives the order to turn them in.
* **Week 21:** CS231n ConvNets → conv arithmetic drills → transfer learning on my own dataset → ResNet paper if there's time.
* **150% rule:** if any resource takes more than 1.5× its budget, stop — the resource is wrong or a prerequisite is missing.

---

*Authored as part of the Data Science Journey. Continuously updated as new modules are completed.*
