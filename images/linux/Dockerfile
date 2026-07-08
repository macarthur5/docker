FROM ubuntu:24.04

RUN apt update && \
    apt install -y \
        python3 \
        git \
        curl \
        nodejs \
        npm \
        tmux

RUN apt update && apt install -y curl git gpg && \
    mkdir -p -m 755 /etc/apt/keyrings && \
    curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg \
        | gpg --dearmor -o /etc/apt/keyrings/githubcli-archive-keyring.gpg && \
    chmod go+r /etc/apt/keyrings/githubcli-archive-keyring.gpg && \
    echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" \
        > /etc/apt/sources.list.d/github-cli.list && \
    apt update && \
    apt install -y gh

ENV PATH="/root/.local/bin:${PATH}"        

RUN curl -fsSL https://claude.ai/install.sh | bash        

WORKDIR /workspace

CMD ["bash"]