# Compressed CNN surgery

This is a call for a simple research project on figuring out what is happening inside compressed convolutional nets (CNNs) using PyTorch. 

It is well known that some large networks in computer vision (e.g. ResNet50) can be extremely compressed (like quantized to 4 bit precision or with 90% of weights zeroed out) and still be fine-tuned to have almost the same accuracy as the original network before compression. What is happening to the internal representation of the network subject to this kind of extreme compresson? Somebody has to figure out!

## :memo: Where we I start?

### Step 1: Prepare compressed models in PyTorch (compressed finetuned checkpoints already available):

- [Distiller:](https://github.com/NervanaSystems/distiller) framework for CNN compression
- [NNCF:](https://github.com/openvinotoolkit/nncf_pytorch) compression framework with available model checkpoints

:rocket: 

### Step 2: Use some of the developed tools in PyTorch to analyze CNN internals:
- [flashtorch:](https://github.com/MisaOgura/flashtorch) saliency maps and activation maximization to visualize features in PyTorch
- [pytorch-cnn-visualizations:](https://github.com/utkuozbulak/pytorch-cnn-visualizations) filter & gradient visualizations (GradCAM etc.)
- [captum:](https://github.com/pytorch/captum) some more interpretability stuff
