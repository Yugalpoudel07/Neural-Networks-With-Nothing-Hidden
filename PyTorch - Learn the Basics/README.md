[🏠 **Main Repository**](../README.md) &nbsp;•&nbsp; [**Next module: Gentle intro to autograd** ⏭️](../PyTorch%20-%20A%20Gentle%20Introduction%20to%20torch.autograd/README.md)

---

# 🔥 PyTorch — Learn the Basics (Week 18)

### *Eight short pages, in order, until you can write the training loop from memory*

[![Time](https://img.shields.io/badge/Time_budget-6_hrs-blue?style=flat-square)](#-the-study-path)
[![Version](https://img.shields.io/badge/PyTorch-2.14-EE4C2C?style=flat-square)](https://docs.pytorch.org/tutorials/beginner/basics/intro.html)
[![Steps](https://img.shields.io/badge/Steps-9_parts-purple?style=flat-square)](#-the-study-path)

> [!NOTE]
> **Roadmap assignment:** the full *Learn the Basics* sequence plus the Quickstart. **Skip:** the advanced deployment tutorials for now.
> **What you produce:** **a training loop you can write from memory.**

> [!IMPORTANT]
> **Link change:** PyTorch moved its tutorials. `pytorch.org/tutorials/...` now **redirects (302)** to **`docs.pytorch.org/tutorials/...`**. Links below use the new address. Docs show **PyTorch 2.14** (series last updated Jan 2026). Every page has a **"Run in Google Colab"** button if your laptop has no GPU.
>
> **Two Week 18 topics the sequence doesn't cover well** — `reshape` vs `view` vs `permute`, and why `zero_grad()` exists — are handled in Part 2's bridge and Part 7's ⭐.

---

## 🗺 The study path

| Part | Page | Time | Status |
| :-: | :--- | :-: | :-: |
| 1 | Quickstart (the whole workflow once, fast) | 30 min | ☐ |
| 2 | Tensors (+ bridge: Tensor Views) | 1 h | ☐ |
| 3 | Datasets & DataLoaders | 50 min | ☐ |
| 4 | Transforms | 15 min | ☐ |
| 5 | Build the Neural Network | 40 min | ☐ |
| 6 | Automatic Differentiation | 30 min | ☐ |
| 7 | ⭐ Optimizing Model Parameters (the training loop) | 1 h | ☐ |
| 8 | Save and Load the Model | 15 min | ☐ |
| 9 | ⭐ The loop from memory | 1 h | ☐ |
| | **Total** | **6 h** | |

📄 Index: https://docs.pytorch.org/tutorials/beginner/basics/intro.html

---

### Part 1 — Quickstart · 30 min
📄 https://docs.pytorch.org/tutorials/beginner/basics/quickstart_tutorial.html

- [ ] Run it top to bottom once without stopping to study: [Working with data](https://docs.pytorch.org/tutorials/beginner/basics/quickstart_tutorial.html#working-with-data) → [Creating Models](https://docs.pytorch.org/tutorials/beginner/basics/quickstart_tutorial.html#creating-models) → [Optimizing the Model Parameters](https://docs.pytorch.org/tutorials/beginner/basics/quickstart_tutorial.html#optimizing-the-model-parameters) → [Saving Models](https://docs.pytorch.org/tutorials/beginner/basics/quickstart_tutorial.html#saving-models) → [Loading Models](https://docs.pytorch.org/tutorials/beginner/basics/quickstart_tutorial.html#loading-models). Parts 2–8 slow down on each piece.

---

### Part 2 — Tensors · 1 h *(Week 18 build task 1: 20 tensor exercises)*
📄 https://docs.pytorch.org/tutorials/beginner/basics/tensorqs_tutorial.html

- [ ] 1. [Initializing a Tensor](https://docs.pytorch.org/tutorials/beginner/basics/tensorqs_tutorial.html#initializing-a-tensor) and [Attributes of a Tensor](https://docs.pytorch.org/tutorials/beginner/basics/tensorqs_tutorial.html#attributes-of-a-tensor) — `shape`, `dtype`, `device`. · 10 min
- [ ] 2. ⭐ [Operations on Tensors](https://docs.pytorch.org/tutorials/beginner/basics/tensorqs_tutorial.html#operations-on-tensors) — moving to GPU (`.to(device)`), indexing, `torch.cat`, `@` vs `*`, and **in-place ops (`_` suffix) — and why they're discouraged with autograd.** · 20 min
- [ ] 3. [Bridge with NumPy](https://docs.pytorch.org/tutorials/beginner/basics/tensorqs_tutorial.html#bridge-with-numpy) — `.numpy()` and `torch.from_numpy()` **share memory**: change one, the other changes. · 10 min
- [ ] 4. **Bridge — Tensor Views:** 📄 https://docs.pytorch.org/docs/stable/tensor_view.html — which ops return a *view* (shared memory) and which a copy. The rule to remember: `view` needs contiguous memory and fails otherwise; `reshape` works always (copying if it must); `permute`/`transpose` return a non-contiguous view, so `x.permute(...).view(...)` errors and needs `.contiguous()` or `reshape`. · 20 min

---

### Part 3 — Datasets & DataLoaders · 50 min
📄 https://docs.pytorch.org/tutorials/beginner/basics/data_tutorial.html

- [ ] 1. [Loading a Dataset](https://docs.pytorch.org/tutorials/beginner/basics/data_tutorial.html#loading-a-dataset) and [Iterating and Visualizing the Dataset](https://docs.pytorch.org/tutorials/beginner/basics/data_tutorial.html#iterating-and-visualizing-the-dataset). · 15 min
- [ ] 2. ⭐ [Creating a Custom Dataset for your files](https://docs.pytorch.org/tutorials/beginner/basics/data_tutorial.html#creating-a-custom-dataset-for-your-files) — the three methods `__init__`, `__len__`, `__getitem__`. You'll write one for your own images in Week 21. · 20 min
- [ ] 3. [Preparing your data for training with DataLoaders](https://docs.pytorch.org/tutorials/beginner/basics/data_tutorial.html#preparing-your-data-for-training-with-dataloaders) and [Iterate through the DataLoader](https://docs.pytorch.org/tutorials/beginner/basics/data_tutorial.html#iterate-through-the-dataloader) — `batch_size`, `shuffle=True` for training only. · 15 min

---

### Part 4 — Transforms · 15 min
📄 https://docs.pytorch.org/tutorials/beginner/basics/transforms_tutorial.html

- [ ] [ToImage() and ToDtype()](https://docs.pytorch.org/tutorials/beginner/basics/transforms_tutorial.html#toimage-and-todtype) and [Lambda Transforms](https://docs.pytorch.org/tutorials/beginner/basics/transforms_tutorial.html#lambda-transforms). (The page now uses `torchvision.transforms.v2`; older tutorials say `ToTensor()`.)

---

### Part 5 — Build the Neural Network · 40 min
📄 https://docs.pytorch.org/tutorials/beginner/basics/buildmodel_tutorial.html

- [ ] 1. [Get Device for Training](https://docs.pytorch.org/tutorials/beginner/basics/buildmodel_tutorial.html#get-device-for-training) and ⭐ [Define the Class](https://docs.pytorch.org/tutorials/beginner/basics/buildmodel_tutorial.html#define-the-class) — `nn.Module`, `__init__`, `forward`. **Never call `model.forward(x)` directly — call `model(x)`.** · 15 min
- [ ] 2. [Model Layers](https://docs.pytorch.org/tutorials/beginner/basics/buildmodel_tutorial.html#model-layers) — `nn.Flatten`, `nn.Linear`, `nn.ReLU`, `nn.Sequential`, `nn.Softmax`. Note the model returns **logits**; softmax is applied only for reading probabilities. · 15 min
- [ ] 3. [Model Parameters](https://docs.pytorch.org/tutorials/beginner/basics/buildmodel_tutorial.html#model-parameters) — `named_parameters()`; count them. · 10 min

---

### Part 6 — Automatic Differentiation · 30 min
📄 https://docs.pytorch.org/tutorials/beginner/basics/autogradqs_tutorial.html

- [ ] 1. [Tensors, Functions and Computational graph](https://docs.pytorch.org/tutorials/beginner/basics/autogradqs_tutorial.html#tensors-functions-and-computational-graph) and [Computing Gradients](https://docs.pytorch.org/tutorials/beginner/basics/autogradqs_tutorial.html#computing-gradients). · 15 min
- [ ] 2. [Disabling Gradient Tracking](https://docs.pytorch.org/tutorials/beginner/basics/autogradqs_tutorial.html#disabling-gradient-tracking) (`torch.no_grad()`, `detach()`) and [More on Computational Graphs](https://docs.pytorch.org/tutorials/beginner/basics/autogradqs_tutorial.html#more-on-computational-graphs) (the graph is rebuilt every forward pass). · 15 min

**Skip:** *Optional Reading: Tensor Gradients and Jacobian Products* — the [Gentle Introduction](../PyTorch%20-%20A%20Gentle%20Introduction%20to%20torch.autograd/README.md) covers it.

---

### Part 7 — ⭐ Optimizing Model Parameters · 1 h *(the most important page)*
📄 https://docs.pytorch.org/tutorials/beginner/basics/optimization_tutorial.html

- [ ] 1. [Hyperparameters](https://docs.pytorch.org/tutorials/beginner/basics/optimization_tutorial.html#hyperparameters) — epochs, batch size, learning rate. · 5 min
- [ ] 2. ⭐ [Optimization Loop](https://docs.pytorch.org/tutorials/beginner/basics/optimization_tutorial.html#optimization-loop) → [Loss Function](https://docs.pytorch.org/tutorials/beginner/basics/optimization_tutorial.html#loss-function) (`nn.CrossEntropyLoss` takes **logits** — it combines log-softmax + NLL; Gate 5 Q5) → [Optimizer](https://docs.pytorch.org/tutorials/beginner/basics/optimization_tutorial.html#optimizer) — read the three steps: `optimizer.zero_grad()` (**"Gradients by default add up"**), `loss.backward()`, `optimizer.step()`. · 25 min
- [ ] 3. ⭐ [Full Implementation](https://docs.pytorch.org/tutorials/beginner/basics/optimization_tutorial.html#full-implementation) — `train_loop` with `model.train()`, `test_loop` with `model.eval()` + `torch.no_grad()`. Type it, don't paste it. · 30 min

---

### Part 8 — Save and Load the Model · 15 min
📄 https://docs.pytorch.org/tutorials/beginner/basics/saveloadrun_tutorial.html

- [ ] [Saving and Loading Model Weights](https://docs.pytorch.org/tutorials/beginner/basics/saveloadrun_tutorial.html#saving-and-loading-model-weights) — `state_dict()`, and `weights_only=True` on load. Skim [Saving and Loading Models with Shapes](https://docs.pytorch.org/tutorials/beginner/basics/saveloadrun_tutorial.html#saving-and-loading-models-with-shapes).

---

### Part 9 — ⭐ The loop from memory · 1 h *(Week 18 build task 3)*

- [ ] Close every tab. In an empty file, write: `Dataset` → `DataLoader` → `nn.Module` → loss + optimizer → `train_loop` (train mode, zero_grad, forward, loss, backward, step) → `val_loop` (eval mode, no_grad) → **early stopping** on validation loss → **checkpoint** the best `state_dict`. Run it. Diff it against the tutorial. Repeat tomorrow until the diff is empty.

---

## 🧪 Exercise on your own data (Week 18 build tasks 2 and 4)

1. **Re-implement your Month 3 logistic regression in PyTorch** (`nn.Linear(d, 1)` + `nn.BCEWithLogitsLoss`) on the same data. The coefficients must match your NumPy version (same learning rate, same epochs, full-batch). Write down precisely what the framework removed.
2. **Break it three times on purpose** and record each symptom in a new `failure-log.md` (keep it all year):
   - remove `optimizer.zero_grad()` → what does the loss curve do?
   - use `nn.MSELoss` instead of cross-entropy → what changes?
   - forget `model.eval()` with a dropout layer → why do validation scores wobble?

---

## 🛠 What this module produces (from the roadmap)

- [ ] A training loop you can write from memory (Part 9 — commit each attempt)
- [ ] 20 tensor exercises (reshape, broadcasting, indexing)
- [ ] `failure-log.md` started with three entries
