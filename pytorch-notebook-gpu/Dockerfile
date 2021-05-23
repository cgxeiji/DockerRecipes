FROM pytorch/pytorch:latest

RUN apt-get update && apt-get install -y --no-install-recommends \
        libsm6 \
        libxext6 \
        libxrender-dev \
        software-properties-common \
        ffmpeg && \
    rm -rf /var/lib/apt/lists/*

RUN /opt/conda/bin/conda install -y nodejs opencv Cython scikit-learn matplotlib seaborn jupyter jupyterlab pandas pytest hypothesis && \
    /opt/conda/bin/conda install -c conda-forge tensorboardx && \
    /opt/conda/bin/conda clean -ya

RUN jupyter labextension install jupyterlab_tensorboard jupyterlab-plotly && \
    jupyter labextension install @jupyter-widgets/jupyterlab-manager plotlywidget

RUN pip install tensorflow-gpu jupyter_tensorboard torchvision scikit-image numpy gensim dgl plotly wordcloud transformers torchtext afinn

RUN mkdir -p /home/me && chmod 1777 /home/me

ENV HOME /home/me
ENV PATH="/usr/bin:${PATH}"

# tensorboard port
EXPOSE 6006

# jupyter notebook port
EXPOSE 8888

COPY start.sh /

CMD ["/start.sh"]
