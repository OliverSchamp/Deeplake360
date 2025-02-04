# Use the NVIDIA PyTorch container as a base image
FROM nvcr.io/nvidia/pytorch:23.05-py3

ENV PYTHONDONTWRITEBYTECODE=1 
ENV PYTHONUNBUFFERED=1

RUN apt-get update -y && apt upgrade -y

RUN apt-get install -y libnss3

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
    langchain-community \
    langchain-text-splitters \
    pyvis \
    unstructured==0.16.17 \
    selenium==4.28.1 \
    nltk \
    sentence_transformers===2.2.2

# pip install the linting modules
RUN pip install --no-cache-dir \
    pylint \
    pycodestyle \
    black

RUN pip install -U pillow==9.5.0

RUN pip install --upgrade --quiet  langchain-google-community

RUN apt-get install -y wget unzip

# Set up the Chrome PPA

RUN wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -

RUN echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list

# Update the package list and install chrome

RUN apt-get update -y

RUN apt-get install -y google-chrome-stable

# Set up Chromedriver Environment variables

ENV CHROMEDRIVER_VERSION 2.19

ENV CHROMEDRIVER_DIR /chromedriver

RUN mkdir $CHROMEDRIVER_DIR

# Download and install Chromedriver

RUN wget -q --continue -P $CHROMEDRIVER_DIR "http://chromedriver.storage.googleapis.com/$CHROMEDRIVER_VERSION/chromedriver_linux64.zip"

RUN unzip $CHROMEDRIVER_DIR/chromedriver* -d $CHROMEDRIVER_DIR

# Put Chromedriver into the PATH

ENV PATH $CHROMEDRIVER_DIR:$PATH

# Clean up package cache to reduce image size
RUN apt clean && rm -rf /var/lib/apt/lists/*

