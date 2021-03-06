# Human Shape and Pose Estimation

The HMR (End-to-end recovery of human shape and pose, CVPR 2018 by Angjoo Kanazawa, Michael J. Black, David W. Jacobs, Jitendra Malik) runs with python 2.7 on the linux system.

This version of HMR runs with python 3.6 on Windows.

### Requirements
- Anaconda env. of Python 3.6
- [TensorFlow](https://www.tensorflow.org/) tested on version 1.12

### Installation
#### Setup conda environment
1. Make an environment with python 3.6 in Anaconda.
2. Install `numpy`, `scikit-image`, `pyopengl`, `py-opencv`, `bottleneck`, `tensorflow` using Anaconda Packaging.

#### Install opendr
1. Download `opendr` from https://github.com/polmorenoc/opendr

In a terminal of the conda environment, go to the opendr folder. It has both `opendr` and `chumpy` folders.

2. Correct `opendr/renderer.py` file

Uncomment line 484 to obtain normals in tn() method.

3. Install both on the conda environment by
moving into opendr then,
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

4. `ipdb` & `glfw` should also be installed, but they are not in Anaconda Packaging.
```
  pip install ipdb
  pip install glfw
```

Opendr can be checked as
```
  python demo_fit_cube.py
```
It will pop some windows including cubes.
If an error occurs in scipy, a simple modification is required.
You search for scipy in site-packages of your conda environment. Edit sputils.py at line 281 in scipy/sparse

```
new_shape = tuple(operator.index(arg) for arg in args)
```

changed to 
```
new_shape = tuple(operator.index(int(arg)) for arg in args)
```

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
