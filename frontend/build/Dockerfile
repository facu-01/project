FROM ubuntu:bionic

ARG DEBIAN_FRONTEND=noninteractive

# actualizamos
RUN apt-get update && apt-get upgrade -y \
    # añadimos los basicos
    && apt-get install -y git wget nano curl mlocate

# instalamos zsh
RUN apt-get install -y zsh

# instalamos oh-my-zsh y reemplazamos la shell
RUN sh -c "$(wget https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)" \
    && chsh -s $(which zsh) \
    && git clone --depth=1 https://gitee.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k \
    && git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

# seteamos la configuracion de zsh
COPY .p10k.zsh /root/.p10k.zsh
COPY .zshrc /root/.zshrc

# instalamos los paquetes necesarios para react
RUN curl -sL https://deb.nodesource.com/setup_16.x | bash - 
RUN apt-get install -y nodejs
RUN npm install -g yarn
