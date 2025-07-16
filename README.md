# Visual Question Answering (VQA)

A deep learning project for answering questions about images using multimodal models that combine **computer vision** and **natural language processing**. This work compares multiple model architectures using the [VQA v2 dataset](https://visualqa.org/) and COCO images.

---

## What This Project Does

This project implements and compares several Visual Question Answering (VQA) models based on different combinations of image and text encoders:

- Uses **Vision Transformer (ViT)** and **ResNet50** to extract image features.
- Encodes questions with:
  - **LSTM**: Simple sequential model.
  - **LSTM with Attention**: Adds spatial attention for enhanced interpretability.
  - **1D CNN**: Captures local n-gram features from questions.
  - **RNN**: Baseline recurrent model with fewer parameters.
- Multimodal fusion via **element-wise multiplication** of image and text embeddings.
- Final answer prediction using a two-layer **MLP classifier**.
- Uses **contrastive learning (SimCLR)** and **CLIP normalization** to improve image embeddings.
- Evaluation via training loss, validation accuracy, and confusion matrices.

---

## Models Implemented

| Image Encoder | Text Encoder     | Notes                                |
| ------------- | ---------------- | ------------------------------------ |
| ViT (CLIP)    | LSTM             | Strong baseline                      |
| ViT (CLIP)    | LSTM + Attention | Best performing overall              |
| ViT (CLIP)    | 1D CNN           | Strong and fast model                |
| ViT (CLIP)    | RNN              | Simple, lower performance            |
| ResNet50      | All 4 above      | For comparison with traditional CNNs |

---

## Results Summary

- **ViT + LSTM + Attention** achieved the highest accuracy (~58%).
- **ResNet-based** models were generally weaker than ViT.
- All models showed **some overfitting**, especially with small datasets.
- **Attention** helped improve complex reasoning.
- **CLIP-normalized inputs** and **SimCLR augmentations** boosted performance.

---

## References

- [VQA Dataset](https://visualqa.org/)
- [CLIP (ViT)](https://arxiv.org/abs/2103.00020)
- [SimCLR](https://arxiv.org/abs/2002.05709)
- [Show, Ask, Attend, and Answer](https://arxiv.org/abs/1704.03162)

---

## Conclusion

This project demonstrates that transformer-based visual representations (ViT) combined with attention-based LSTM models outperform traditional CNN and RNN pipelines in VQA tasks. Richer embeddings and semantic alignment are key to better multimodal understanding.
