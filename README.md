# thesis_word
### Bones fracturing classification

# TensorFlow Object Detection Setup Guide

This guide outlines the steps to set up TensorFlow Object Detection with Anaconda on Windows.

## Prerequisites

- Anaconda installed
- CUDA Toolkit downloaded and installed based on Python version
- cuDNN downloaded and copied to the appropriate CUDA Toolkit directory
- TensorFlow installed
- Git installed

## Steps

1. Install Anaconda from [here](https://www.anaconda.com/products/distribution).

2. Follow the instructions provided in the [TensorFlow GPU installation guide](https://www.tensorflow.org/install/source_windows#gpu) to determine the specific Python version with CUDA support.

3. Download the CUDA Toolkit based on the Python version and set the path location to `C:/`.

4. Check if the CUDA bin is already set in the environment path.

5. Download cuDNN based on the Python version from [here](https://developer.nvidia.com/rdp/cudnn-archive).

6. Unzip the cuDNN file and copy all files to `C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.2` (or appropriate CUDA version).

7. Create a new Conda environment:
    ```
    conda create -n tfod python==3.8 -y
    activate tfod
    ```

8. Install TensorFlow based on the specific CUDA version:
    ```
    pip install tensorflow==2.10.0
    ```

9. Check if the GPU is working using the provided code snippet.

10. Clone the TensorFlow model repository to your project directory and maintain a Git ignore policy:
    ```
    git clone https://github.com/tensorflow/models.git
    ```

11. Download Protocol Buffers (protoc) library from [here](https://github.com/protocolbuffers/protobuf/releases). Choose the appropriate version for Windows.

12. Create a folder named "Google Protobuf" in `C:\Program Files` and paste the unzipped protoc files. Set the environment path to `C:\Program Files\Google Protobuf\bin` in Windows environment variables.

13. Open Anaconda command prompt and navigate to `TensorFlow\models\research`. Run:
    ```
    protoc object_detection/protos/*.proto --python_out=.
    ```

14. Install necessary dependencies:
    ```
    pip install cython
    pip install git+https://github.com/philferriere/cocoapi.git#subdirectory=PythonAPI
    ```

15. Run the following commands from within `TensorFlow\models\research` using Git Bash:
    ```
    cp object_detection/packages/tf2/setup.py .
    python -m pip install .
    pip install protobuf==3.20.0
    python object_detection/builders/model_builder_tf2_test.py
    ```

16. Your setup should be complete and ready to use for TensorFlow Object Detection.