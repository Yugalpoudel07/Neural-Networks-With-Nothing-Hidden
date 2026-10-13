[🏠 **Main Repository**](../README.md) &nbsp;•&nbsp; [⏮️ **Convolution arithmetic**](../A%20Guide%20to%20Convolution%20Arithmetic%20for%20Deep%20Learning/README.md) &nbsp;•&nbsp; [**Next module: ResNet paper (optional)** ⏭️](../Deep%20Residual%20Learning%20for%20Image%20Recognition%20%28He%20et%20al.%29/README.md)

---

# 🖼 PyTorch — Transfer Learning for Computer Vision (Week 21)

### *Freeze the backbone or fine-tune the whole thing — done on YOUR images, not the tutorial's ants and bees*

[![Time](https://img.shields.io/badge/Time_budget-2_hrs-blue?style=flat-square)](#-the-study-path)
[![Version](https://img.shields.io/badge/PyTorch-2.14-EE4C2C?style=flat-square)](https://docs.pytorch.org/tutorials/beginner/transfer_learning_tutorial.html)

> [!NOTE]
> **Roadmap assignment:** all of it, **applied to your dataset rather than the tutorial's**. **Skip:** nothing.
> **What you produce:** your **three-row comparison table: from scratch vs feature extraction vs fine-tuning.**

> [!IMPORTANT]
> **Link change:** `pytorch.org/tutorials/beginner/transfer_learning_tutorial.html` now redirects to **https://docs.pytorch.org/tutorials/beginner/transfer_learning_tutorial.html**. The tutorial uses `models.resnet18(weights='IMAGENET1K_V1')` (the old `pretrained=True` is gone) and `datasets.ImageFolder`, so **your data must be laid out as** `data/<name>/{train,val}/<class>/*.jpg`.
> **Your dataset (roadmap Week 21):** a small custom image set — *ideally something from Nepal that nobody else's portfolio will have* (e.g. 2–4 classes of local foods, temples vs stupas, rice-field stages, number plates by province…). 100–300 images per class is enough.

---

## 🗺 The study path

| Step | Section | Time | Status |
| :-: | :--- | :-: | :-: |
| 1 | Intro + Load Data (on your folder) | 25 min | ☐ |
| 2 | Training the model + visualizing predictions | 20 min | ☐ |
| 3 | ⭐ Finetuning the ConvNet | 25 min | ☐ |
| 4 | ⭐ ConvNet as fixed feature extractor | 25 min | ☐ |
| 5 | Inference on custom images | 10 min | ☐ |
| 6 | ⭐ The three-row table | 15 min | ☐ |
| | **Total** | **2 h** | |

📄 https://docs.pytorch.org/tutorials/beginner/transfer_learning_tutorial.html

---

- [ ] 1. Intro (the two scenarios: *finetuning* vs *fixed feature extractor*) → [Load Data](https://docs.pytorch.org/tutorials/beginner/transfer_learning_tutorial.html#load-data) → [Visualize a few images](https://docs.pytorch.org/tutorials/beginner/transfer_learning_tutorial.html#visualize-a-few-images). Point `data_dir` at **your** folder. Note: train gets augmentation (`RandomResizedCrop`, flip), val doesn't; both use **ImageNet's mean/std** because the backbone was trained with them. · 25 min
- [ ] 2. [Training the model](https://docs.pytorch.org/tutorials/beginner/transfer_learning_tutorial.html#training-the-model) — the generic `train_model` with best-weights checkpointing and an LR scheduler; compare it with *your* Week 18 loop. [Visualizing the model predictions](https://docs.pytorch.org/tutorials/beginner/transfer_learning_tutorial.html#visualizing-the-model-predictions). · 20 min
- [ ] 3. ⭐ [Finetuning the ConvNet](https://docs.pytorch.org/tutorials/beginner/transfer_learning_tutorial.html#finetuning-the-convnet) — replace `model.fc` with `nn.Linear(num_ftrs, n_classes)`; **all** weights train. → [Train and evaluate](https://docs.pytorch.org/tutorials/beginner/transfer_learning_tutorial.html#train-and-evaluate). · 25 min
- [ ] 4. ⭐ [ConvNet as fixed feature extractor](https://docs.pytorch.org/tutorials/beginner/transfer_learning_tutorial.html#convnet-as-fixed-feature-extractor) — `param.requires_grad = False` for the backbone (the *Exclusion from the DAG* idea from the autograd intro); only the new `fc` trains. Note why it's ~2× faster per epoch. · 25 min
- [ ] 5. [Inference on custom images](https://docs.pytorch.org/tutorials/beginner/transfer_learning_tutorial.html#inference-on-custom-images) — predict on a photo you take today. · 10 min
- [ ] 6. ⭐ Build the table (below). · 15 min

**Skip:** *Further Learning* links (quantized transfer learning) for now.

---

## 🧪 Exercise on your own data (Week 21 build tasks 5 and 6)

Same split, same epochs, same augmentation, **3 seeds each** (5 if you have the GPU time):

| Approach | Trainable params | Time / epoch | Val accuracy (mean ± sd) |
| :--- | :-: | :-: | :-: |
| ResNet-18 **from scratch** (`weights=None`) | | | |
| **Feature extraction** (frozen backbone) | | | |
| **Full fine-tuning** | | | |

Then: open the **misclassified** validation images for your best model and sort them into *reasonable mistake* / *label error* / *model is wrong*. Put 6 of them in a grid in the README with one sentence each.

---

## 🛠 What this module produces (from the roadmap)

- [ ] The three-row comparison table on your own dataset — **"that table is the lesson"**
- [ ] A grid of misclassified images with your verdict on each
