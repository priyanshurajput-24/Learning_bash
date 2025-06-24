# Docker Command

## Images 

* Set up for Ubuntu.

    ```bash
    export DEBIAN_FRONTEND=noninteractive && \
    apt update && \
    apt install -y tzdata && \
    ln -fs /usr/share/zoneinfo/Asia/Kolkata /etc/localtime && \
    dpkg-reconfigure -f noninteractive tzdata && \

    # Shell aliases and custom prompt
    echo "alias c='clear'" >> ~/.bashrc && \
    echo "alias u='cd ..'" >> ~/.bashrc && \
    echo "alias r='cd ~'" >> ~/.bashrc && \
    echo "PS1='${debian_chroot:+($debian_chroot)}\[\033[0;31m\]\\$\[\033[0m\] \[\033[0;32m\]🙈\[\033[0m\] '" >> ~/.bashrc && \

    # Install core tools and Python dependencies
    apt install -y vim python3 python3-pip python3.12-venv git htop curl tmux net-tools lsof && \
    pip3 install awscli --no-cache-dir --break-system-packages && \
    curl -LsSf https://astral.sh/uv/install.sh | sh && \

    # Git config
    git config --global user.name "Priyanshu" && \
    git config --global user.email "rajputmanu024@gmail.com" && \

    # Create .vimrc with custom settings
    cat <<EOF > ~/.vimrc
    syntax on
    set nu

    " Highlight the status line when splitting windows
    highlight StatusLineNC ctermbg=red guibg=red
    EOF

    # Reload shell settings
    source ~/.bashrc
    ```







---
* Direct get the terminal inside docker 
    ```bash
    docker run -it <image_id> /bin/bash
    ```

    ```bash
    docker run -it --gpus all -p 5000:5000 <image_id> /bin/bash
    ```

## Containers

* For starting a stoped container

    ```bash
    docker start <container-id>
    ```
* Connect to that running container

    ```bash
    docker exec -it <container-id> /bin/bash
    ```

## Volumes





## Hub 
* Push image to docker hub
    1. create a repo in docker hub, Choose `public` or `private` type.
    2. For making a existing container state as an `image`.
    3. run this command `docker commit 6c08e156e117a0 ubuntu_custom:latest`.

        ```bash
        docker commit <container-id> <custom-image-name>:<custom-tag-name>
        ```
    4. Tag the image `docker tag ubuntu_custom:latest priyanshu00024/custom_base_ubuntu:v1`

        ```bash
        docker tag <image-name>:<tag> <dockerhub-username>/<repo-name>:<custom-tag-name>
        ```
    5. Then just push the image `docker push priyanshu00024/custom_base_ubuntu:v1`

        ```bash
        docker push <dockerhub-username>/<repo-name>:<tag-name>
        ```
