[🏠 **Main Repository**](../README.md) &nbsp;•&nbsp; [⏮️ **Nielsen**](../Neural%20Networks%20and%20Deep%20Learning%20%28Michael%20Nielsen%29/README.md) &nbsp;•&nbsp; [**Next module: Karpathy's recipe** ⏭️](../A%20Recipe%20for%20Training%20Neural%20Networks%20%28Karpathy%29/README.md)

---

# 🎓 Stanford CS231n — course notes (Weeks 19–21)

### *Five written modules — backprop, the three "Neural Networks" parts, and ConvNets — plus the case study that ties them together*

[![Time](https://img.shields.io/badge/Time_budget-8_hrs-blue?style=flat-square)](#-the-study-path)
[![Site](https://img.shields.io/badge/cs231n.github.io-live_(Spring_2026)-8C1515?style=flat-square)](https://cs231n.github.io/)

> [!NOTE]
> **Roadmap assignment:** Backpropagation; Neural Networks Part 1, 2 and 3; the Convolutional Networks module. **Skip:** the assignments (this plan gives you better ones) and the modules on detection and segmentation.
> **What you produce:** notes, plus your **convolution shape drills**.

> [!IMPORTANT]
> **Link check (25 Sep 2026) — the card said "CHECK before use":** https://cs231n.github.io/ is **live** and lists Spring 2026 assignments; the note URLs haven't moved. One addition inside the 8 hours: **"Putting it together: Minimal Neural Network Case Study"** — a 2-layer network in ~50 lines of NumPy, which is exactly Week 19 build task 3 on a toy dataset.

---

## 🗺 The study path

| Part | Week | Module | Time | Status |
| :-: | :-: | :--- | :-: | :-: |
| 1 | 19 | ⭐ Backpropagation, Intuitions | 1 h 15 | ☐ |
| 2 | 19 | Minimal Neural Network Case Study *(bridge)* | 45 min | ☐ |
| 3 | 19 | Neural Networks Part 1: Setting up the Architecture | 1 h | ☐ |
| 4 | 20 | Neural Networks Part 2: Setting up the Data and the Loss | 1 h 15 | ☐ |
| 5 | 20 | ⭐ Neural Networks Part 3: Learning and Evaluation | 1 h 30 | ☐ |
| 6 | 21 | ⭐ Convolutional Neural Networks (+ transfer-learning note) | 2 h 15 | ☐ |
| | | **Total** | **8 h** | |

---

### Part 1 — ⭐ Backpropagation, Intuitions · 1 h 15 *(Week 19)*
📄 https://cs231n.github.io/optimization-2/

- [ ] 1. [Introduction](https://cs231n.github.io/optimization-2/#intro), [Simple expressions, interpreting the gradient](https://cs231n.github.io/optimization-2/#grad), [Compound expressions, chain rule, backpropagation](https://cs231n.github.io/optimization-2/#backprop) — the circuit diagrams. · 15 min
- [ ] 2. [Intuitive understanding of backpropagation](https://cs231n.github.io/optimization-2/#intuitive) and [Modularity: Sigmoid example](https://cs231n.github.io/optimization-2/#sigmoid) — each gate only needs its **local** gradient. · 15 min
- [ ] 3. [Backprop in practice: Staged computation](https://cs231n.github.io/optimization-2/#staged) — cache forward values, reuse them backwards. · 10 min
- [ ] 4. ⭐ [Patterns in backward flow](https://cs231n.github.io/optimization-2/#patterns) — **add distributes, max routes, multiply swaps.** Memorise these three. · 10 min
- [ ] 5. ⭐ [Gradients for vectorized operations](https://cs231n.github.io/optimization-2/#mat) — the **dimension-analysis trick**: `dW = dD @ X.T` is the only arrangement whose shapes work. This is how you write the backward pass for a linear layer in Gate 5 Q2. · 25 min

---

### Part 2 — Minimal Neural Network Case Study *(bridge)* · 45 min *(Week 19)*
📄 https://cs231n.github.io/neural-networks-case-study/

- [ ] Read it **after** your paper derivation and **before** your MNIST network. Type the softmax classifier, then the 2-layer network, on the spiral data. Compare its `dscores = probs; dscores[range(N), y] -= 1` with your $\delta^L = a^L - y$.

---

### Part 3 — Neural Networks Part 1: Setting up the Architecture · 1 h *(Week 19)*
📄 https://cs231n.github.io/neural-networks-1/

- [ ] 1. [Quick intro](https://cs231n.github.io/neural-networks-1/#quick) and [Modeling one neuron](https://cs231n.github.io/neural-networks-1/#intro) → [Single neuron as a linear classifier](https://cs231n.github.io/neural-networks-1/#classifier). · 15 min
- [ ] 2. ⭐ [Commonly used activation functions](https://cs231n.github.io/neural-networks-1/#actfun) — sigmoid (saturates, not zero-centred), tanh, **ReLU (and dying ReLUs)**, Leaky ReLU, Maxout. Gate 5 Q3 (vanishing gradients) starts here. · 20 min
- [ ] 3. [Layer-wise organization](https://cs231n.github.io/neural-networks-1/#layers), [Example feed-forward computation](https://cs231n.github.io/neural-networks-1/#feedforward), [Representational power](https://cs231n.github.io/neural-networks-1/#power), [Setting number of layers and their sizes](https://cs231n.github.io/neural-networks-1/#arch). · 25 min

**Skip:** [Biological motivation and connections](https://cs231n.github.io/neural-networks-1/#bio).

---

### Part 4 — Neural Networks Part 2: Data and Loss · 1 h 15 *(Week 20)*
📄 https://cs231n.github.io/neural-networks-2/

- [ ] 1. [Data Preprocessing](https://cs231n.github.io/neural-networks-2/#datapre) — mean subtraction and normalisation; **compute statistics on training data only** (Month 4's leak, again). Skim PCA/whitening. · 15 min
- [ ] 2. ⭐ [Weight Initialization](https://cs231n.github.io/neural-networks-2/#init) — why all-zero init fails (symmetry), calibrating variance with 1/√n, **He init for ReLU** (Week 20 build task 4). · 20 min
- [ ] 3. [Batch Normalization](https://cs231n.github.io/neural-networks-2/#batchnorm) — the short paragraph. · 5 min
- [ ] 4. ⭐ [Regularization](https://cs231n.github.io/neural-networks-2/#reg) — L2 / weight decay, max-norm, **dropout (inverted dropout)**. · 20 min
- [ ] 5. [Loss functions](https://cs231n.github.io/neural-networks-2/#losses) — classification losses; skim attribute classification and regression. · 15 min

---

### Part 5 — ⭐ Neural Networks Part 3: Learning and Evaluation · 1 h 30 *(Week 20)*
📄 https://cs231n.github.io/neural-networks-3/

- [ ] 1. ⭐ [Gradient checks](https://cs231n.github.io/neural-networks-3/#gradcheck) — **centred** differences, **relative** error thresholds (1e-7 good, 1e-2 wrong), kinks, and turning off dropout while checking. Upgrade your Month 1 checker with these rules. · 20 min
- [ ] 2. [Before learning: sanity checks](https://cs231n.github.io/neural-networks-3/#sanitycheck) — **loss at init should be ln(10) ≈ 2.302 for 10 classes**; overfit a tiny subset. · 10 min
- [ ] 3. ⭐ [Babysitting the learning process](https://cs231n.github.io/neural-networks-3/#baby) — [Loss function](https://cs231n.github.io/neural-networks-3/#loss) curves (learning rate too high/low), [Train/Val accuracy](https://cs231n.github.io/neural-networks-3/#accuracy) (overfitting gap), [Ratio of weights:updates](https://cs231n.github.io/neural-networks-3/#ratio) (~1e-3), [Activation / Gradient distributions](https://cs231n.github.io/neural-networks-3/#distr). **Reading a training curve like an X-ray** — Week 20. · 20 min
- [ ] 4. ⭐ [Parameter updates](https://cs231n.github.io/neural-networks-3/#update) → [SGD and bells and whistles](https://cs231n.github.io/neural-networks-3/#sgd) (momentum, Nesterov), [Annealing the learning rate](https://cs231n.github.io/neural-networks-3/#anneal), [Per-parameter adaptive learning rate methods](https://cs231n.github.io/neural-networks-3/#ada) (Adagrad → RMSprop → **Adam**). Write each update rule in NumPy. · 25 min
- [ ] 5. [Hyperparameter optimization](https://cs231n.github.io/neural-networks-3/#hyper) — random search beats grid search; search the learning rate on a **log** scale. · 10 min
- [ ] 6. [Model Ensembles](https://cs231n.github.io/neural-networks-3/#ensemble). · 5 min

**Skip:** [Second order methods](https://cs231n.github.io/neural-networks-3/#second), [First-layer Visualizations](https://cs231n.github.io/neural-networks-3/#vis).

---

### Part 6 — ⭐ Convolutional Neural Networks · 2 h 15 *(Week 21)*
📄 https://cs231n.github.io/convolutional-networks/

- [ ] 1. [Architecture Overview](https://cs231n.github.io/convolutional-networks/#overview) — 3-D volumes of neurons. · 10 min
- [ ] 2. ⭐ [Convolutional Layer](https://cs231n.github.io/convolutional-networks/#conv) — local connectivity, **spatial arrangement: output size = (W − F + 2P)/S + 1**, parameter sharing, the animated demo, and **"implementation as matrix multiplication" (im2col)** — the idea behind your fast vectorised convolution (Week 21 build task 1). · 50 min
- [ ] 3. [Pooling Layer](https://cs231n.github.io/convolutional-networks/#pool), [Normalization Layer](https://cs231n.github.io/convolutional-networks/#norm), [Fully-connected layer](https://cs231n.github.io/convolutional-networks/#fc). · 15 min
- [ ] 4. [Converting FC layers to CONV layers](https://cs231n.github.io/convolutional-networks/#convert) — skim. · 5 min
- [ ] 5. [ConvNet Architectures](https://cs231n.github.io/convolutional-networks/#architectures) → [Layer Patterns](https://cs231n.github.io/convolutional-networks/#layerpat), [Layer Sizing Patterns](https://cs231n.github.io/convolutional-networks/#layersizepat), ⭐ [Case studies](https://cs231n.github.io/convolutional-networks/#case) (LeNet → AlexNet → ZF → GoogLeNet → VGGNet → **ResNet**), [Computational Considerations](https://cs231n.github.io/convolutional-networks/#comp) (VGG's memory, worked out). · 40 min
- [ ] 6. 📄 [Transfer Learning](https://cs231n.github.io/transfer-learning/#tf) — the short note on *when* to freeze vs fine-tune (by dataset size and similarity). Read it before the PyTorch transfer-learning tutorial. · 15 min

**Skip:** *Understanding and Visualizing CNNs*, *Recurrent Neural Networks* (that's Month 6), and all assignments.

---

## 🧪 Exercise on your own data

**Convolution shape drills (the deliverable):** for **10 configurations** of your own choosing (input size, kernel size, stride, padding, channels), compute by hand: output height/width, number of weights, number of biases, and multiply-adds. Then build each as `nn.Conv2d` and check `out.shape` and `sum(p.numel() for p in layer.parameters())`. Put the table in this folder as `conv-shape-drills.md`. At least three rows should be ones where the formula isn't a whole number — what does PyTorch do?

---

## 🛠 What this module produces (from the roadmap)

- [ ] Notes for the five modules (one file each here)
- [ ] `conv-shape-drills.md` — 10 configurations, hand vs PyTorch
- [ ] Your upgraded gradient checker (centred differences + relative error)
