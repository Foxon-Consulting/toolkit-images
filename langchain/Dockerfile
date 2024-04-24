# Create your image base-toolkit-image here
FROM python:3.11

# # Install necessary packages
RUN apt-get update -y

RUN apt-get install -y sudo git ssh python3 curl make npm pip

RUN npm i release-please -g

RUN pip install pre-commit

# # Handle multiplatform line endings
RUN git config --global core.autocrlf true

# Install Bourne Again Shell
RUN apt-get install -y bash

# Get a nice prompt
ENV PS1="\[\033[35m\]\t\[\033[m\]-\[\033[36m\]\u\[\033[m\]@\[\033[32m\]\h:\[\033[33;1m\]\w\[\033[36m\] -\[\033[36m\]\$(git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/')\[\033[00m\] $ "

# # Install Docker
RUN apt-get install docker -y

# # Install dependencies for unstructured
RUN apt-get install -y libmagic-dev poppler-utils tesseract-ocr libreoffice pandoc

# # Install unstructured
RUN pip install unstructured[all-docs]

CMD ["/bin/bash"]
