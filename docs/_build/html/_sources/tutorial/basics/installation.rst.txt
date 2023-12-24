.. _installation:

Installation
===================================================================

SAPIEN-IPC relies on `SAPIEN 3 <https://sapien.ucsd.edu/>`_ (the physics-based simulator) and `Warp <https://github.com/NVIDIA/warp>`_ (the Python framework for CUDA programming). In this tutorial, we will give some simple instructions on how to install these dependencies and then install SAPIEN-IPC. For further details, please refer to the official documentation of these libraries. 

Requirements
-------------------------------------------------------------------

* Linux: Ubuntu 18.04+, Centos 7+, Arch'
* Python 3.7.x-3.11.x
* GCC 7.2 upwards
* CUDA Toolkit 11.5 or higher
* PyTorch that is compatible with your CUDA platform
* Git LFS installed (https://git-lfs.github.com/)


Step 1: Clone SAPIEN-IPC repo recursively
-------------------------------------------------------------------

First, clone our repo recursively so that the submodule ``warp_`` is cloned:

.. todo::

    SAPIEN-IPC is not publicly released yet. We will release it to the following link soon. 

.. code-block:: shell

    git clone --recurse-submodules git@github.com:Rabbit-Hu/sapienipc.git
    cd sapienipc
    pip install -r requirements.txt

The submodule ``warp_`` is a slightly modified fork of the original Warp library. 


Step 2: Install our fork of Warp
-------------------------------------------------------------------

Then build our fork of Warp in the `warp_` submodule, specifying your cuda path. 

.. code-block:: shell

    cd warp_
    python build_lib.py --cuda_path /usr/local/cuda  # Replace with your CUDA path 

Install the Warp package into your python environment:

.. code-block:: shell

    pip install -e .


Step 3: Install SAPIEN
-------------------------------------------------------------------

Use pip to install the latest SAPIEN 3 wheel from `SAPIEN Nightly Release <https://github.com/haosulab/SAPIEN/releases/tag/nightly>`_. Look for your own Python version. 

The installation command should look like this:

.. code-block:: shell

    pip install https://github.com/haosulab/SAPIEN/releases/download/nightly/sapien-3.0.0.dev{version_name}.whl  # Replace with the latest link


See the `SAPIEN <https://github.com/haosulab/SAPIEN>`_ repo for reference.


Step 4: Install SAPIEN-IPC
-------------------------------------------------------------------

.. code-block:: shell

    cd ..  # change to the "sapienipc" directory
    pip install -e .

You can verify your installation by running an example (display is required).

.. code-block:: shell

    python examples/example_fall.py


