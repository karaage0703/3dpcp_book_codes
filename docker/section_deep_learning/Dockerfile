FROM pytorch/pytorch:1.11.0-cuda11.3-cudnn8-devel

RUN apt-key adv --fetch-keys https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/3bf863cc.pub
RUN apt-key adv --fetch-keys https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/7fa2af80.pub
RUN apt-get update && apt install libx11-6 libgl1-mesa-dev -y && apt-get clean
RUN conda install pyg -c pyg -y && conda clean -ya
RUN conda install nodejs "h5py<3.2" jupyterlab ipywidgets tensorboard -c conda-forge -y && conda clean -ya
RUN pip install open3d==0.14.1

RUN jupyter nbextension enable --py --sys-prefix widgetsnbextension

ENTRYPOINT jupyter notebook --NotebookApp.token="" --NotebookApp.password="" --NotebookApp.notebook_dir="/workspace" --ip 0.0.0.0 --allow-root --no-browser --port 8888 & /bin/bash
