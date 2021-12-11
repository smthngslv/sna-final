FROM python:3.9

WORKDIR /app

# Download latest wait-for script.
RUN wget https://raw.githubusercontent.com/eficode/wait-for/master/wait-for && \
    chmod +x wait-for && \
    apt-get update -y && \
    apt-get install netcat -y

# Environment.
COPY ./requirements.txt /tmp/requirements.txt
RUN python -m venv env && \
    ./env/bin/python -m pip install --no-cache-dir --upgrade pip setuptools wheel && \
    ./env/bin/python -m pip install --no-cache-dir -r /tmp/requirements.txt && \
    rm /tmp/requirements.txt

# App.
COPY ./config ./config
COPY ./innonymous ./innonymous
COPY ./entrypoint.sh ./entrypoint.sh

# Run.
EXPOSE 8000
ENTRYPOINT ["sh", "./entrypoint.sh"]
