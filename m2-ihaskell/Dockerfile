FROM acrstudy.azurecr.io/math/sagemath-jupyter-m2:v1

USER sage

# Install Haskell
RUN curl -sSL https://get.haskellstack.org | sh

# Install IHaskell and its dependencies
RUN sudo apt-get -y install libtinfo-dev libzmq3-dev libcairo2-dev libpango1.0-dev libmagic-dev libblas-dev liblapack-dev && \
    git clone https://github.com/gibiansky/IHaskell ~/IHaskell && \
    cd IHaskell && \
    stack install gtk2hs-buildtools && \
    stack install --fast && \
    sage -sh -c "~/.local/bin/ihaskell install --stack" && \
    cd && \
    rm -rf IHaskell && \
    sage -sh -c "jupyter labextension install ihaskell_jupyterlab"
