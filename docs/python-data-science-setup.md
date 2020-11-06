# Python for Data Science

![Python packages](../assets/python-package.png?raw=true)

## Install dependencies

```bash
# Leave Python virtual environment
deactivate

# Install Graphviz - Keras dependency
brew install Graphviz
```

## Create a Python virtual environment

```bash
# Example using Python 3.7.6
pyenv shell 3.7.6
mkvirtualenv py376
pip install --upgrade pip
```

## Install TensorFlow

[TensorFlow](https://www.tensorflow.org) is an end-to-end open source platform for machine learning.

```bash
# Activate the virtual environment
workon py376

# Install TensorFlow
pip install tensorflow
```

## Install Keras

[Keras](https://keras.io) is a high-level neural networks API, written in Python and capable of running on top of TensorFlow, CNTK, or Theano.

```bash
# Activate the virtual environment
workon py376

# Install Keras
pip install h5py pydot keras
```

## Install Python scientific libraires

```bash
# Activate the virtual environment
workon py376

# Install libraries
pip install numpy \
            pandas \
            scipy \
            pillow \
            scikit-learn \
            scikit-image \
            sk-video
```

## Install basic libraires

```bash
# Activate the virtual environment
workon py376

# Install libraries
pip install autopep8 \
            Cython \
            ipykernel \
            progressbar2 \
            pydocstyle \
            pylint \
            pytest \
            requests
```

## Install Matplotlib

```bash
# Activate the virtual environment
workon py376

# Install Matplotlib
pip install ipympl matplotlib

# Fix Matplotlib backend
mkdir -p "${HOME}/.config/matplotlib"
echo "backend : TkAgg" > "${HOME}/.config/matplotlib/matplotlibrc"
```

## Install Jupyter Lab

1. Install Node

    ```bash
    # Leave Python virtual environment
    deactivate

    # Install Node
    brew install node
    ```

2. Install Jupyter Lab

    ```bash
    # Activate Python environment
    workon py376

    # Install Jupyterlab
    pip install jupyterlab jupyterlab-git jupyter-tensorboard jupytext
    ```

3. Install Jupyter Lab extensions

    ```bash
    # Activate Python environment
    workon py376

    # Install extensions
    jupyter labextension install @jupyterlab/toc
    jupyter labextension install @jupyterlab/git
    jupyter serverextension enable --py jupyterlab_git
    jupyter labextension install jupyterlab_tensorboard
    jupyter labextension install jupyterlab-jupytext
    jupyter labextension install @jupyter-widgets/jupyterlab-manager
    jupyter labextension install jupyter-matplotlib

    # Check extensions status
    jupyter labextension list
    ```
