This repo was created with the purpose of storing the files used in my Retinal Fluid Classification project.

1) OCTID.ipynb- code used to obtain results for the **OCTID** dataset
2) OCTDL_wrkspc- code used to obtain results for the **OCTDL** dataset

Results

1) Dataset preparation and model outcomes
   
A 4-class OCT dataset (CSR, DR, MH, NORMAL) was cleaned, standardized to 224×224 resolution, and split into a fixed validation set of 104 images. Three transformer architectures were trained on the same pipeline: ViT-Base, DeiT-Base, and MaxViT. ViT reached 97.12% accuracy, while DeiT and MaxViT both reached 98.08%, with DeiT achieving the best macro-F1 (0.976) and weighted-F1 (0.981), indicating strong class-balanced performance rather than majority-class dominance.

3) What the results actually mean
   
All three models achieved ROC–AUC > 0.98 for every disease class, with DeiT reaching up to 0.999–1.000, which means the learned representations separate retinal pathologies extremely well in feature space. NORMAL and CSR are detected almost perfectly, while MH and DR account for nearly all residual errors, reflecting genuine visual similarity in OCT scans rather than model instability. This suggests the pipeline is learning medically meaningful retinal structures without using any shortcuts.

4) Nuance in the results
Despite the high scores, the validation set is relatively small (104 images), so 1–2 misclassifications can change accuracy by ~1%, making differences between 97% and 98% statistically fragile. The early convergence of ViT and the near-saturated AUC values also suggest the dataset may be too clean or too easy, potentially inflating real-world performance. In practice, larger and noisier clinical datasets would likely reduce these metrics, especially for MH vs DR, which already forms the dominant confusion cluster.
