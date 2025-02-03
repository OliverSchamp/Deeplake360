# Use the NVIDIA PyTorch container as a base image
FROM nvcr.io/nvidia/pytorch:23.05-py3

ENV PYTHONDONTWRITEBYTECODE=1 
ENV PYTHONUNBUFFERED=1

# pip install the relevant modules
RUN pip install langchain==0.0.208 deeplake==3.9.27 openai==0.27.8 tiktoken

RUN pip install huggingface_hub==0.26

# pip install the standard modules
RUN pip install --no-cache-dir \
    numpy \
    pandas \
    jupyter \
    jupyterlab \
    notebook \
    tqdm \
    pillow \
    tensorflow \
    keras \
    google-api-python-client \
    pypdf \
    requests \
    newspaper3k \
    lxml_html_clean \
    langchain-openai \
    langchain-community

# pip install the linting modules
RUN pip install --no-cache-dir \
    pylint \
    pycodestyle \
    black

RUN pip install -U pillow==9.5.0

RUN pip install --upgrade --quiet  langchain-google-community

# Clean up package cache to reduce image size
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

