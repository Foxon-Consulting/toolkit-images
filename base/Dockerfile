# Create your image base-toolkit-image here
FROM alpine:3.18.4

# Install necessary packages
RUN apk update && \
    apk add --no-cache sudo shadow openssh git python3 py3-pip curl make npm

RUN npm i release-please -g

RUN pip install pre-commit

# Handle multiplatform line endings
RUN git config --global core.autocrlf true

# Install Bourne Again Shell
RUN apk add --no-cache bash

# Install make
RUN apk add make

# Install Docker
RUN apk add --update --no-cache docker-cli

# Get a nice prompt
ENV PS1="\[\033[35m\]\t\[\033[m\]-\[\033[36m\]\u\[\033[m\]@\[\033[32m\]\h:\[\033[33;1m\]\w\[\033[36m\] -\[\033[36m\]\$(git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/')\[\033[00m\] $ "

CMD ["/bin/bash"]
