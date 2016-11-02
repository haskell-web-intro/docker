from mmaz/ghc-secdev
# docker build -t mmaz/stack-secdev stack-secdev/
# docker run --rm -it mmaz/stack-secdev /bin/bash

ENV DEBIAN_FRONTEND noninteractive
RUN apt-get -y install nano

ENV PATH /root/.local/bin:$PATH
RUN stack install ghcid

# SecDev talk dependencies
RUN stack build direct-sqlite monad-control mtl sqlite-simple text aeson bytestring either servant servant-client servant-server servant-swagger swagger2 transformers wai wai-extra warp lens vector mmorph stm

# LiquidHaskell
RUN cd ~/ && \
    wget https://github.com/Z3Prover/z3/releases/download/z3-4.4.1/z3-4.4.1-x64-ubuntu-14.04.zip && \
    unzip z3-4.4.1-x64-ubuntu-14.04.zip && \
    rm z3-4.4.1-x64-ubuntu-14.04.zip
ENV PATH /root/z3-4.4.1-x64-ubuntu-14.04/bin:$PATH
RUN stack --resolver lts-6.22 setup
RUN stack --resolver lts-6.22 install daemons-0.2.1 liquid-fixpoint-0.5.0.1 located-base-0.1.1.0 dotgen-0.4.2 fgl-visualize-0.1.0.1 intern-0.9.1.4 liquidhaskell

#spacemacs
RUN git clone --recursive https://github.com/syl20bnr/spacemacs.git -b develop /root/.emacs.d
COPY .spacemacs /root/.spacemacs
RUN emacs -nw -batch -u root -q -kill && \
    emacs -nw -batch -u root -q -kill

# nano ~/.spacemacs
#    dotspacemacs-editing-style 'vim
#    dotspacemacs-editing-style 'emacs
