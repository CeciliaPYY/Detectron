# Use Caffe2 image as parent image
FROM caffe2ai/caffe2:c2v0.8.0.cuda8.cudnn6.ubuntu16.04

# Install Python dependencies
RUN pip install numpy pyyaml matplotlib opencv-python>=3.0 setuptools Cython mock

# Install the COCO API
RUN git clone https://github.com/cocodataset/cocoapi.git
WORKDIR /cocoapi/PythonAPI
RUN make install

# Clone the Detectron repository
RUN git clone https://github.com/facebookresearch/detectron /detectron

# Set up Python modules
WORKDIR /detectron/lib
RUN make

# Build custom ops
RUN make ops

# Go to Detectron root
WORKDIR /detectron
