FROM mmaz/stack-secdev
#docker build -t mmaz/ghcjs-secdev ghcjs-secdev/
#docker run --rm -it mmaz/ghcjs-secdev /bin/bash

RUN wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.32.0/install.sh | bash
ENV NVM_DIR /root/.nvm
ENV NODE_VERSION 4.6.0
RUN . $HOME/.nvm/nvm.sh && nvm install $NODE_VERSION && nvm alias default $NODE_VERSION && nvm use default # (.) is an alias for source, compatible with the ubuntu container shell (we are not using bash)
ENV PATH      $NVM_DIR/versions/node/v$NODE_VERSION/bin:$PATH

ENV PATH  /root/.stack/programs/x86_64-linux/ghc-8.0.1/bin:$PATH

COPY stack.yaml /root/ghcjs.yaml
RUN stack setup --stack-yaml=/root/ghcjs.yaml
