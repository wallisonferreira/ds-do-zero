# Aula 24

# Criando o container e fazendo as configurações necessárias

docker container run -it --name jupyter-server -v "$PWD/data:/tmp" -p 8888:8888 ubuntu:16.04 bash

# Instalação de bibliotecas e softwares dentro do container

## Atualizando o repositório de pacotes do sistema

apt-get update --fix-missing

## Instalando o scrippt wget para fazer download e softwares básicos

apt-get install -y wget bzip2 ca-certificates build-essential byobu curl git-core pkg-config python3-dev python-pip python-setuptools python-virtualenv unzip

## Limpando os arquivos temporários e listas

apt-get clean
rm -rf /var/lib/apt/lists/

## Definindo a variável de ambiente com a localização para instalação do anaconda

echo 'export PATH=/opt/conda/bin:$PATH' > /etc/profile.d/conda.sh

## Fazendo o Download do Anaconda (Verifique se o link está correto)

wget --quiet https://repo.anaconda.com/archive/Anaconda3-2022.10-Linux-x86_64.sh -O ~/anaconda.sh

# Instalação de bibliotecas e softwares dentro do containter

## Instalando o Anaconda e suas bibliotecas

/bin/bash ~/anaconda.sh -b -p /opt/conda

## Excluindo o script de instalação

rm ~/anaconda.sh

## Atualizando a variável de ambiente PATH

export PATH="/opt/conda/bin:$PATH"

## Inicializando o Jupyter Notebook

jupyter notebook --ip=0.0.0.0 --allow-root --no-browser