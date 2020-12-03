FROM jupyter/minimal-notebook

WORKDIR /work

USER root
COPY ./package.list .
RUN apt-get update
RUN cat package.list | grep -vE "^\s*#" | xargs apt-get install -y
RUN rm ./package.list
# install python 3.7.9
RUN apt install -y make build-essential libssl-dev zlib1g-dev \
    libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev \
    libncursesw5-dev xz-utils tk-dev libffi-dev liblzma-dev python-openssl\
    git

USER jovyan
WORKDIR /home/jovyan/work

ENV HOME  /home/jovyan
ENV PYENV_ROOT $HOME/.pyenv
ENV PATH $PYENV_ROOT/shims:$PYENV_ROOT/bin:$PATH
RUN git clone https://github.com/pyenv/pyenv.git ~/.pyenv
RUN pyenv install 3.7.9
RUN pyenv global 3.7.9

RUN pip install --upgrade pip
RUN pip uninstall -y numpy

COPY ./requirements.txt .
RUN pip install -r requirements.txt
RUN rm ./requirements.txt

# Please, uncomment to disable token
CMD ["jupyter", "lab", "--no-browser","--NotebookApp.token=''","--NotebookApp.password=''"]


