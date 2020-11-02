# Compressed CNN surgery

This is a call/repo for a simple research project on figuring out what is happening inside compressed convolutional nets (CNNs) using PyTorch. 

It is well known that some large neural networks in computer vision (e.g. ResNet50) can be compressed to a large extent (like quantized to 4 bit precision or with 90% of weights zeroed out) and still be fine-tuned to have almost the same accuracy as the original network before compression. What is happening to the internal representation of the network subject to this kind of extreme compression? Somebody has to figure out!

## :memo: Where do we start?

### Step 1: Prepare compressed models in PyTorch (compressed finetuned checkpoints already available for many cases)

- [Distiller:](https://github.com/NervanaSystems/distiller) framework for CNN compression
- [NNCF:](https://github.com/openvinotoolkit/nncf_pytorch) compression framework with available model checkpoints

:rocket: 

### Step 2: Choose some of the developed tools in PyTorch to analyze CNN internals

- [flashtorch:](https://github.com/MisaOgura/flashtorch) saliency maps and activation maximization to visualize features in PyTorch
- [pytorch-cnn-visualizations:](https://github.com/utkuozbulak/pytorch-cnn-visualizations) filter & gradient visualizations (GradCAM etc.)
- [captum:](https://github.com/pytorch/captum) some more interpretability stuff
- [CCA:](https://github.com/google/svcca) numerical metrics of internal representations similarity from Google

:straight_ruler: :triangular_ruler:

### Step 3: Reproduce the same diagnostic visualizations from the analysis tools, but for the compressed models

1. Create new Jupyter Notebooks in a cloud service like [Google Colab](https://colab.research.google.com/notebooks/intro.ipynb) or locally
1. Decide which exact Deep Neural Network (DNN) model from **Step 1** you will use for your experiments: it should be available in both compressed and non-compressed variants, which were pre-trained on the same dataset
1. Find several (e.g. 10) images, which you will use as network input to visualize and compare internal representations
1. Using the tools from **Step 2**, get internal network representations for your images for compressed and non-compressed version of DNN from **Step 1**
1. Compare the obtained metrics either visually or numerically

:chart_with_upwards_trend: :microscope: :bar_chart:

## Example script and notebook

We provide a starter traning script and a notebook for a ResNet18 model trained on CIFAR10 with INT8 compression. Activation maximization maps are visualized for the original and int8 compressed models in the **features_resnet18_cifar10_int8_vs_fp32** notebook via the *flashtorch* package. INT8 compression is done via the *nncf* package. Training of the uncompressed and compressed models on CIFAR10 can be reproduced with the **train_resnet18_cifar10** script. You can download the checkpoint files [here](https://drive.google.com/drive/folders/1IAkkKgYsNhpFxsh7J469-P6ivwyI-bRF?usp=sharing).

## What's next?

ML engineers and data scientists from industrial companies will review your work and help you to formulate conclusions. You can include this work in your portfolio as scientific research of compressed deep neural networks.

The key point of this work is that almost any statistically significant result is valuable for the science and industry:
* if internal representations are the same for compressed and non-compressed networks, then it can be accounted and monitored during the further development of the optimization algorithms;
* if internal representations are not the same, then it will also be accounted and monitored during the further development.

:clipboard: Your obtained results can be published in a blog or scientific report/paper. We can even try to write such report with your co-authorship.

Invest your time into interesting problems in DNN research and get knowledge, practical experience, and portfolio points back!

:handshake: :mortar_board:
