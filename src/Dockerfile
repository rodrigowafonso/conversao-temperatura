FROM ubuntu

# Passo a Passo de Instalaçao do Nodejs no ambiente.
ARG NODE_MAJOR=22

RUN apt update -y && \
    apt install curl -y && \
    curl -fsSL https://deb.nodesource.com/setup_22.x -o nodesource_setup.sh && \
    bash nodesource_setup.sh && \
    apt install -y nodejs

WORKDIR /app
COPY . .

RUN npm install
ENTRYPOINT [ "node", "server.js" ]
