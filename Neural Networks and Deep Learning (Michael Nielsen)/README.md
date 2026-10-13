[🏠 **Main Repository**](../README.md) &nbsp;•&nbsp; [⏮️ **micrograd source**](../micrograd%20%28Karpathy%29%20-%20source%20repository/README.md) &nbsp;•&nbsp; [**Next module: CS231n notes** ⏭️](../Stanford%20CS231n%20-%20course%20notes/README.md)

---

# 📖 Neural Networks and Deep Learning — Michael Nielsen (Weeks 18–19)

### *Chapters 1 and 2 — the clearest written derivation of backpropagation, worked with a pen*

[![Time](https://img.shields.io/badge/Time_budget-5_hrs-blue?style=flat-square)](#-the-study-path)
[![Chapters](https://img.shields.io/badge/Chapters-1_and_2-purple?style=flat-square)](http://neuralnetworksanddeeplearning.com/)
[![Cost](https://img.shields.io/badge/Cost-Free_online-brightgreen?style=flat-square)](http://neuralnetworksanddeeplearning.com/)

> [!NOTE]
> **Roadmap assignment:** Chapters 1 and 2 only. **Chapter 2 is the backpropagation derivation — work through it with a pen.** **Skip:** Chapters 3–6 for now.
> **What you produce:** **your photographed paper derivation of backprop for a 2-layer network** (Week 19 build task 1).
>
> *Where Karpathy gives you code intuition, Nielsen gives you the mathematics. Do both.* Nielsen **before** the video.

> [!IMPORTANT]
> **Checked 25 Sep 2026:** the book is live at `http://neuralnetworksanddeeplearning.com/` (plain http, as the roadmap has it). Its code (`network.py`) is **Python 2.7** — **read** it to see the structure, then write your own NumPy version rather than trying to run his.
> **Notation to watch:** Nielsen writes weights as $w^l_{jk}$ (**to** neuron j **from** neuron k) and uses the quadratic cost in Ch 1–2. Your Week 19 network uses **cross-entropy + softmax**, where the output error simplifies to $\delta^L = a^L - y$ — the same "predicted − actual" as Month 3's logistic regression.

---

## 🗺 The study path

| Part | Week | What | Time | Status |
| :-: | :-: | :--- | :-: | :-: |
| 1 | 18 | Ch 1 — Using neural nets to recognize handwritten digits | 2 h | ☐ |
| 2 | 19 | ⭐ Ch 2 — How the backpropagation algorithm works (pen and paper) | 3 h | ☐ |
| | | **Total** | **5 h** | |

---

### Part 1 — Chapter 1 · 2 h *(Week 18)*
📄 http://neuralnetworksanddeeplearning.com/chap1.html

- [ ] 1. [Perceptrons](http://neuralnetworksanddeeplearning.com/chap1.html#perceptrons) and [Sigmoid neurons](http://neuralnetworksanddeeplearning.com/chap1.html#sigmoid_neurons) — why a smooth activation makes small changes in weights produce small changes in output (so learning is possible). · 30 min
- [ ] 2. [The architecture of neural networks](http://neuralnetworksanddeeplearning.com/chap1.html#the_architecture_of_neural_networks) and [A simple network to classify handwritten digits](http://neuralnetworksanddeeplearning.com/chap1.html#a_simple_network_to_classify_handwritten_digits). · 20 min
- [ ] 3. ⭐ [Learning with gradient descent](http://neuralnetworksanddeeplearning.com/chap1.html#learning_with_gradient_descent) — cost function, gradient descent, **stochastic** gradient descent and mini-batches. Do the one-variable exercise in your head. · 30 min
- [ ] 4. [Implementing our network to classify digits](http://neuralnetworksanddeeplearning.com/chap1.html#implementing_our_network_to_classify_digits) — read `network.py` (`feedforward`, `SGD`, `update_mini_batch`). **Don't run it**; note the shapes of `weights[l]` and `biases[l]`. · 30 min
- [ ] 5. [Toward deep learning](http://neuralnetworksanddeeplearning.com/chap1.html#toward_deep_learning). · 10 min

---

### Part 2 — ⭐ Chapter 2, with a pen · 3 h *(Week 19, before any editor is opened)*
📄 http://neuralnetworksanddeeplearning.com/chap2.html

- [ ] 1. [Warm up: a fast matrix-based approach to computing the output from a neural network](http://neuralnetworksanddeeplearning.com/chap2.html#warm_up_a_fast_matrix-based_approach_to_computing_the_output_from_a_neural_network) — $a^l = \sigma(w^l a^{l-1} + b^l)$. **Write the shape of every matrix** for a 784-30-10 network. · 20 min
- [ ] 2. [The two assumptions we need about the cost function](http://neuralnetworksanddeeplearning.com/chap2.html#the_two_assumptions_we_need_about_the_cost_function), then the Hadamard product section right after it. · 15 min
- [ ] 3. ⭐ [The four fundamental equations behind backpropagation](http://neuralnetworksanddeeplearning.com/chap2.html#the_four_fundamental_equations_behind_backpropagation) — **BP1–BP4**. Copy each onto paper and write one plain-English sentence under each. · 45 min
- [ ] 4. ⭐ [Proof of the four fundamental equations (optional)](http://neuralnetworksanddeeplearning.com/chap2.html#proof_of_the_four_fundamental_equations_%28optional%29) — **not optional for you.** Prove BP1 and BP2 yourself with the chain rule, then do the exercise to prove BP3 and BP4. **This is your Gate 5 question 1.** · 40 min
- [ ] 5. [The backpropagation algorithm](http://neuralnetworksanddeeplearning.com/chap2.html#the_backpropagation_algorithm) — the 5-step algorithm, and the mini-batch version. · 15 min
- [ ] 6. [The code for backpropagation](http://neuralnetworksanddeeplearning.com/chap2.html#the_code_for_backpropagation) — map each line of `backprop()` to BP1–BP4. · 20 min
- [ ] 7. [In what sense is backpropagation a fast algorithm?](http://neuralnetworksanddeeplearning.com/chap2.html#in_what_sense_is_backpropagation_a_fast_algorithm) — one backward pass vs a million forward passes (the numerical checker). · 10 min
- [ ] 8. [Backpropagation: the big picture](http://neuralnetworksanddeeplearning.com/chap2.html#backpropagation_the_big_picture) — skim. · 15 min

---

## 🧪 Exercise on your own data

Before MNIST, derive and implement on **your own** tabular data (the yes/no target from Month 3):
1. **Paper:** a 2-layer network, d → 8 (ReLU) → 2 (softmax), cross-entropy loss. Write $\delta^2$, $\partial L/\partial W^2$, $\partial L/\partial b^2$, $\delta^1$, $\partial L/\partial W^1$, $\partial L/\partial b^1$ with shapes. Photograph it.
2. **NumPy:** implement exactly those six lines. Check every gradient with your numerical gradient checker (relative error < 1e-7).
3. **Compare:** does it beat your Month 3 logistic regression on validation? Report 5 seeds, mean ± sd. If it doesn't, write why (small tabular data often doesn't need hidden layers — an honest finding).

---

## 🛠 What this module produces (from the roadmap)

- [ ] **The photographed paper derivation of backprop for a 2-layer network** (in the lab notebook)
- [ ] BP1–BP4 in your own words, one sentence each
