# Copyright (c) Jupyter Development Team.
# Distributed under the terms of the Modified BSD License.
ARG BASE_CONTAINER=jupyter/scipy-notebook
FROM $BASE_CONTAINER

LABEL maintainer="Choppy Team <pgx@fudan.edu.cn>"

# Set when building on Travis so that certain long-running build steps can
# be skipped to shorten build time.
ARG TEST_ONLY_BUILD

USER root

# Change conda environment path
RUN echo 'export CONDA_ENVS_PATH=/home/jovyan/.conda/envs' >> /etc/bashrc

USER $NB_UID

# Add bioconda channel for conda
RUN $CONDA_DIR/bin/conda config --system --prepend channels bioconda

# Add python packages that you wanted
RUN conda install --quiet --yes \
    'plotly=4.3.*' \
    && \
    conda clean --all -f -y && \
    fix-permissions $CONDA_DIR && \
    fix-permissions /home/$NB_USER
