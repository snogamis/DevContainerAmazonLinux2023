# Note: You can use any Debian/Ubuntu based image you want. 
##FROM mcr.microsoft.com/devcontainers/base:bullseye
##ARG VARIANT=2023.2.20231030.1
##ARG VARIANT=2023
ARG VARIANT=2023.2.20231026.0
##FROM public.ecr.aws/amazonlinux/amazonlinux:${VARIANT}
FROM amazonlinux:${VARIANT}

# [Optional] Uncomment this section to install additional OS packages.
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends <your-package-list-here>

RUN    yum update \
    && yum install -y which sudo zsh glibc-all-langpacks \
    && yum groupinstall -y "Development Tools" \
    && yum install -y java-21-amazon-corretto maven-amazon-corretto21 rust cargo golang clang nodejs \
    && rm -rf /var/cache/yum/* && yum clean all
#    && amazon-linux-extras install -y python3.8 \
#    && yum install -y python3 \

ENV TZ=Asia/Tokyo \
    LANG=ja_JP.UTF-8 \
    LANGUAGE=ja_JP:ja \
    LC_ALL=ja_JP.UTF-8

##ARG USERNAME=vscode
##ARG USERNAME=ec2-user
ARG UID=1000
##ARG GID=1000
#RUN useradd -u ${UID} ec2-user \
RUN adduser -u ${UID} ec2-user \
    && echo "ec2-user ALL=NOPASSWD: ALL" >> /etc/sudoers
USER ${UID}

RUN bash -c "$(curl -fsSL https://raw.githubusercontent.com/ohmybash/oh-my-bash/master/tools/install.sh)" && sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
