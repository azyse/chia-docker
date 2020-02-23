FROM python:3.7-slim-buster

RUN apt-get update
RUN apt-get install build-essential git cmake libgmp3-dev --no-install-recommends -y
RUN apt-get install python3-dev python3-venv --no-install-recommends -y

RUN git clone https://github.com/Chia-Network/chia-blockchain.git chia
WORKDIR chia

RUN sh install.sh
RUN . .venv/bin/activate

RUN pip install -r requirements.txt
RUN python -m scripts.regenerate_keys
ENTRYPOINT python -m src.server.start_full_node --host "127.0.0.1" --port 8444 --rpc_port 8555