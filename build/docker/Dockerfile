FROM knowengdev/base_image:11_09_2016
MAINTAINER Jing Ge<jingge2@illinois.edu>

ENV SRC_LOC /home

# Install the latest knpackage
RUN pip3 install -I knpackage

# Clone from github
RUN git clone https://github.com/KnowEnG-Research/Phenotype_Prediction_Pipeline.git ${SRC_LOC}

# Set up working directory
WORKDIR ${SRC_LOC}
