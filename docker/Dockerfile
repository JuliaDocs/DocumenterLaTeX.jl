FROM ubuntu:18.04
ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update \
    && apt-get install --no-install-recommends -qy \
    latexmk \
    texlive-latex-base \
    texlive-luatex \
    texlive-latex-recommended \
    texlive-latex-extra \
    fonts-lato \
    python-pygments \
    fontconfig \
    && rm -rf /var/lib/apt/lists/*
RUN useradd -m zeptodoctor \
    && groupadd travis -g 2000 \
    && usermod -a -G travis zeptodoctor
WORKDIR /home/zeptodoctor
ADD https://api.github.com/repos/google/fonts/tarball/master google-fonts.tar.gz
RUN mkdir google-fonts .fonts \
    && tar xzf google-fonts.tar.gz --strip-components=1 -C google-fonts \
    && mv google-fonts/apache/robotomono/RobotoMono*.ttf .fonts \
    && rm -rf google-fonts google-fonts.tar.gz
RUN fc-cache -fv
USER zeptodoctor
