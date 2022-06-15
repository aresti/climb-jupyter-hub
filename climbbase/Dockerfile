FROM jupyter/r-notebook:r-4.1.3

RUN python3 -m pip install jupyter-rsession-proxy

# install rstudio server
USER root
RUN apt-get update && \
    apt-get install -y gdebi-core && \
    wget https://download2.rstudio.org/server/bionic/amd64/rstudio-server-2022.02.2-485-amd64.deb && \
    gdebi --n rstudio-server-2022.02.2-485-amd64.deb
USER $NB_USER

# base conda packages
RUN conda install nb_conda_kernels

# files for home
ADD --chown=jovyan homesync /tmp/homesync
