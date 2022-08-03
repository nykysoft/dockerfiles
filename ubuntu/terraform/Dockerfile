FROM ubuntu:latest

ARG DEFAULT_TERRAFORM_VERSION=1.0.7

RUN  apt-get update -y && apt-get install unzip curl wget git nano -y

# Terraform
RUN git clone --depth=1 https://github.com/tfutils/tfenv.git ~/.tfenv
ENV PATH="/root/.tfenv/bin:$PATH"
RUN tfenv install ${DEFAULT_TERRAFORM_VERSION}
RUN tfenv use ${DEFAUTL_TERRAFORM_VERSION}

# aws-cli
RUN curl -o ~/awscliv2.zip https://awscli.amazonaws.com/awscli-exe-linux-aarch64.zip
RUN unzip ~/awscliv2.zip -d ~
RUN ~/aws/install
RUN mkdir ~/.aws
RUN touch ~/.aws/config

# aws-vault
RUN curl -L -o /usr/local/bin/aws-vault https://github.com/99designs/aws-vault/releases/latest/download/aws-vault-linux-arm64
RUN chmod 755 /usr/local/bin/aws-vault
ENV AWS_VAULT_BACKEND=file

CMD ["bash"]
