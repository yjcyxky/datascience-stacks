# Copyright (c) Jupyter Development Team.
# Distributed under the terms of the Modified BSD License.
ARG BASE_CONTAINER=jupyter/r-notebook
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

# Add r packages that you wanted
RUN conda install --quiet --yes \
    'cookiecutter' \
    'bioconductor-maftools=2.2.*' \
    'r-glmnet=2.*' \
    'r-survival=2.44_1.1' \
    'r-survminer=0.4.*' \
    'bioconductor-complexheatmap=2.2.*' \
    'r-survivalroc=1.0.*' \
    'bioconductor-clusterprofiler=3.14.*' \
    'bioconductor-survcomp=1.36.*' \
    'r-rms=5.*' \
    'r-e1071=1.*' \
    'r-plot3d=1.1.*' \
    'bioconductor-sva=3.34.*' \
    'r-factominer=2.0*' \
    'r-factoextra=1.0.*' \
    'bioconductor-copynumber=1.26*' \
    'r-mcpcounter=1.1*' \
    'r-forestplot=1.9*' \
    'r-comparec=1.3*' \
    'r-circlize=0.4.*' \
    'bioconductor-affy=1.64.*' \
    'bioconductor-limma=3.42.*' \
    'bioconductor-impute=1.60*' \
    'bioconductor-geoquery=2.54*' \

    'r-gridgraphics=0.4*' \
    'r-ggpubr=0.2.*' \
    'r-data.table=1.12.*' \
    'r-wgcna=1.68*'\
    'bioconductor-mygene=1.22*' \
    'r-annotables=v0.1.*' \
    'bioconductor-pathview=1.26*' \
    'r-ggiraph=0.7*' \
    'r-scatterplot3d=0.3*' \
    'r-base=3.6.*' \
    'r-dendextend=1.12*' \
    'r-colorspace=1.4*' \
    'r-ggcorrplot=0.1.*' \
    'r-ggdendro=0.1*' \
    'r-gplots=3.0.*' \
    'r-gmodels=2.18.*' \
    'r-survrm2=1.0*' \
    'r-nmf=0.21*' \
    'bioconductor-biomart=2.42.*' \
    'r-keras=2.2.*' \
    'r-tensorflow=2.0.*' \
    'r-plotly=4.9.*' \
   'r-shinyjs=1.0*' \
    'r-shinydashboard=0.7.*' \
    'r-shinycssloaders=0.2*' \
    'r-shinywidgets=0.5*' \
    'r-rlang=0.3*' \
    'r-rcolorbrewer=1.1*' \
    'r-lattice=0.20_38' \
    'r-scales=1.0*' \
    'r-leaflet=2.0*' \
    && \
    conda clean --all -f -y && \
    fix-permissions $CONDA_DIR && \
    fix-permissions /home/$NB_USER
