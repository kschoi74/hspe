# Human Shape and Pose Estimation

The HMR (End-to-end recovery of human shape and pose, CVPR 2018 by Angjoo Kanazawa, Michael J. Black, David W. Jacobs, Jitendra Malik) runs with python 2.7 on the linux system.

This version of HMR runs with python 3.6 on Windows.

### Requirements
- Anaconda env. of Python 3.6
- [TensorFlow](https://www.tensorflow.org/) tested on version 1.12

### Installation
#### Setup conda environment
Make an environment with python 3.6 in Anaconda.

Install numpy, scikit-image, pyopengl, py-opencv, bottleneck, tensorflow using Anaconda Packaging.

#### Install opendr
Download opendr from https://github.com/polmorenoc/opendr

In a terminal of the conda environment, go to the opendr folder. It has both opendr and chumpy folders.

Install both on the conda environment as

Move into opendr then,
```
  pip install .
```

This procedure installs chumpy (0.76) from PyPI, which does not work with opendr. So,
```
  pip uninstall chumpy
```
Move into chumpy then,
```
  pip install .
```
This install chumpy (0.66) that works with opendr.

ipdb & glfw should also be installed, but they are not in Anaconda Packaging.
```
  pip install ipdb
  pip install glfw
```
Opendr can be checked as
```
  python demo_fit_cube.py
```
It will pop some windows including cubes.

### Demo
Finally, move to the folder of this package.

1. Download the pre-trained models
```
wget https://people.eecs.berkeley.edu/~kanazawa/cachedir/hmr/models.tar.gz && tar -xf models.tar.gz
```

2. Run the demo
```
python -m demo --img_path data/coco1.png

```
