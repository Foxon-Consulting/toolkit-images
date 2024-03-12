FROM foxonconsulting/base-toolkit:1.0.0

# Install Ansible
RUN apk add --update --no-cache openssh-client sshpass py3-pip
RUN pip3 install ansible

# Install Terraform
ARG TERRAFORM_VERSION=1.5.0
RUN apk add --update --no-cache unzip git

RUN wget https://releases.hashicorp.com/terraform/${TERRAFORM_VERSION}/terraform_${TERRAFORM_VERSION}_linux_amd64.zip && \
    unzip terraform_${TERRAFORM_VERSION}_linux_amd64.zip -d /usr/local/bin && \
    rm terraform_${TERRAFORM_VERSION}_linux_amd64.zip

# Install AWS CLI
RUN apk add --update --no-cache python3 && \
    pip3 install --upgrade pip && \
    pip3 install awscli

# Install mysql client
RUN apk add --update --no-cache mysql-client

# Install curl
RUN apk add curl

# Install terraform-docs
RUN mkdir -p /tmp/terraform-docs
WORKDIR /tmp/terraform-docs
RUN curl -Lo ./terraform-docs.tar.gz https://github.com/terraform-docs/terraform-docs/releases/download/v0.16.0/terraform-docs-v0.16.0-$(uname)-amd64.tar.gz
RUN tar -xzf terraform-docs.tar.gz
RUN mv terraform-docs /usr/local/bin
RUN chmod +x /usr/local/bin/terraform-docs
RUN rm -rf /tmp/terraform-docs

# Install tflint
RUN mkdir -p /tmp/tflint
WORKDIR /tmp/tflint
RUN curl -Lo ./tflint.zip https://github.com/terraform-linters/tflint/releases/download/v0.47.0/tflint_linux_arm64.zip
RUN unzip tflint.zip
RUN mv tflint /usr/local/bin
RUN chmod +x /usr/local/bin/tflint
RUN rm -rf /tmp/tflint
