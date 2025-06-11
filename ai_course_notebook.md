# Spring 2025: Foundations of AI: Neural Nets, LLMs & Gen AI

## Lab Libraries and Frameworks Overview

| Lab | Library / Framework | Why It Matters | Official GitHub Link |
|-----|---------------------|----------------|---------------------|
| **Lab 1: Gradient Descent** | PyTorch | Deep learning framework for neural networks. | https://github.com/pytorch/pytorch |
| | NumPy | Numerical computations and array operations. | https://github.com/numpy/numpy |
| | Matplotlib | Plotting and data visualization. | https://github.com/matplotlib/matplotlib |
| | Scikit-learn | Data preprocessing and ML tools. | https://github.com/scikit-learn/scikit-learn |
| **Lab 2: Activation Functions** | *(All libraries used previously in Lab 1)* | *(Already introduced in Lab 1)* | *(Refer to Lab 1 entries)* |
| **Lab 3: Logistic Regression** | Pandas | Data manipulation and tabular data operations. | https://github.com/pandas-dev/pandas |
| | TensorFlow | Alternative deep learning framework. | https://github.com/tensorflow/tensorflow |
| | Keras | High-level API for deep learning with TensorFlow backend. | https://github.com/keras-team/keras |
| | Seaborn | Statistical data visualization on top of Matplotlib. | https://github.com/mwaskom/seaborn |
| **Lab 4: PyTorch Homework** | rich | Beautiful formatting for terminal output. | https://github.com/Textualize/rich |
| | svlearn_hw | Custom internal helper library. | *(Not publicly available)* |
| **Lab 5** | *(Lab not provided / missing)* | *(No data available for this lab)* | *(N/A)* |
| **Lab 6: LR Schedulers** | torch.optim.lr_scheduler | Learning rate scheduling techniques. | https://github.com/pytorch/pytorch |
| | IPython.display | Display rich media in Jupyter notebooks. | https://github.com/ipython/ipython |
| **Lab 7: CNN vs FCN** | torchvision | Computer vision library with datasets and pretrained models. | https://github.com/pytorch/vision |
| **Lab 8 (Part 1): Tree CNN** | *(All libraries used previously in Labs 1/3)* | *(Previously covered: TF, NumPy, etc.)* | *(Refer to earlier labs)* |
| **Lab 8 (Part 2): Audio CNN** | joblib | Serialization and model persistence. | https://github.com/joblib/joblib |
| **Lab 9/10: Autoencoders** | Pillow | Image handling in Python. | https://github.com/python-pillow/Pillow |
| | SciPy | Advanced scientific computing. | https://github.com/scipy/scipy |
| | argparse | CLI argument parsing. | https://github.com/python/cpython/tree/main/Lib/argparse |
| | svlearn_autoencoders | Custom internal AE utility. | *(Not publicly available)* |
| **Lab 11 (Part 1): PINNs** | *(All libraries used previously)* | *(Matplotlib, NumPy, PyTorch, SciPy)* | *(See Lab 1 & 9)* |
| **Lab 11 (Part 2): GANs** | *(All libraries used previously)* | *(torch, torchvision, Pillow, etc.)* | *(See Lab 1, 7, 9)* |
| **Lab 12: Knowledge Distill.** | transformers | State-of-the-art NLP models (by HuggingFace). | https://github.com/huggingface/transformers |
| | tqdm | Progress bars for loops and training. | https://github.com/tqdm/tqdm |
| | svlearn_knowledge_distillation | Custom internal KD utility. | *(Not publicly available)* |
| **Lab 13-a: Mixture of Experts** | *(All libraries used previously)* | *(PyTorch, NumPy, Matplotlib)* | *(See Lab 1, 3)* |
| **Lab 13-b: Attention (Basics)** | *(All libraries used previously)* | *(Standard Python and Jupyter utilities)* | *(See prior entries)* |
| **Lab 14 (Part 1): Transformers** | Datasets (HF) | Dataset loading for NLP. | https://github.com/huggingface/datasets |
| **Lab 14 (Part 2): ViT** | *(All libraries used previously)* | *(Transformers, PyTorch)* | *(See Lab 12 & 14.1)* |
| **Lab 14 (Part 3): Diffusion** | diffusers | Pretrained diffusion models (HuggingFace). | https://github.com/huggingface/diffusers |
| | einops | Tensor reshaping and ops for vision/NLP. | https://github.com/arogozhnikov/einops |
| | ipywidgets | Interactive widgets in Jupyter. | https://github.com/jupyter-widgets/ipywidgets |
| | requests | For downloading resources via HTTP. | https://github.com/psf/requests |

## Tool Usage Across Labs

| Tool Name | Lab 1 | Lab 2 | Lab 3 | Lab 4 | Lab 5 | Lab 6 | Lab 7 | Lab 8.1 | Lab 8.2 | Lab 9/10 | Lab 11 | Lab 12 | Lab 13 | Lab 14 |
|-----------|-------|-------|-------|-------|-------|-------|-------|---------|---------|----------|--------|--------|--------|--------|
| PyTorch | ✅ | ✅ | ✅ | ✅ | ❌ | ✅ | ✅ | ❌ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| NumPy | ✅ | ✅ | ✅ | ✅ | ❌ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Matplotlib | ✅ | ✅ | ✅ | ❌ | ❌ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Scikit-learn | ✅ | ❌ | ✅ | ❌ | ❌ | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ | ✅ | ❌ | ✅ |
| Pandas | ❌ | ❌ | ✅ | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | ✅ | ✅ | ❌ | ❌ | ✅ |
| TensorFlow | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ |
| Keras | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| Seaborn | ❌ | ❌ | ✅ | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | ✅ |
| rich | ❌ | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| svlearn_hw | ❌ | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| torch.optim.lr_scheduler | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| IPython.display | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ | ✅ |
| torchvision | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ | ✅ | ✅ | ✅ | ❌ | ❌ | ✅ |
| joblib | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ |
| Pillow | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | ✅ | ✅ | ❌ | ❌ | ✅ |
| SciPy | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | ✅ | ❌ | ❌ | ❌ |
| argparse | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ |
| svlearn_autoencoders | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ |
| transformers | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ | ✅ |
| tqdm | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ | ✅ |
| svlearn_knowledge_dist... | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ | ❌ |
| Datasets (HF) | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ |
| diffusers | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ |
| einops | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ |
| ipywidgets | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ |
| requests | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ |