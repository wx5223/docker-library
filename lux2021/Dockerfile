FROM pytorch/pytorch:1.9.0-cuda10.2-cudnn7-runtime
#RUN pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
RUN pip install ipython traitlets --upgrade
RUN pip install jupyter jupyter_contrib_nbextensions nbformat
RUN jupyter contrib nbextension install --system
RUN jupyter notebook --generate-config
RUN mkdir /jupyter
#RUN cp /etc/apt/sources.list /etc/apt/sources.list.bak;sed -i 's#http://archive.ubuntu.com#https://mirrors.163.com#g' /etc/apt/sources.list;sed -i 's#http://security.ubuntu.com#https://mirrors.163.com#g' /etc/apt/sources.list;apt-get update

# nvm environment variables
ENV NVM_DIR /usr/local/nvm
ENV NODE_VERSION 14.16.0

# basic setups
RUN apt-get update && apt-get install -y -q --no-install-recommends \
        apt-transport-https \
        ca-certificates \
        curl \
        wget \
        software-properties-common

# install nvm
# https://github.com/creationix/nvm#install-script
RUN curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.31.2/install.sh | bash

# install node and npm
RUN . $NVM_DIR/nvm.sh \
    && nvm install $NODE_VERSION \
    && nvm alias default $NODE_VERSION \
    && nvm use default

# add node and npm to path so the commands are available
ENV NODE_PATH $NVM_DIR/v$NODE_VERSION/lib/node_modules
ENV PATH $NVM_DIR/versions/node/v$NODE_VERSION/bin:$PATH

# confirm installation
RUN node -v
RUN npm -v

# install lux ai
RUN npm i -g @lux-ai/2021-challenge@latest --unsafe-perm=true --allow-root
RUN npm i -g lux-ai-vis --unsafe-perm=true --allow-root

# install python packages
RUN pip install numpy
RUN pip install scipy

RUN pip install git+https://github.com/glmcdona/LuxPythonEnvGym.git
RUN pip install kaggle-environments -U

